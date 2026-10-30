# Peace Rising

**An alarm clock that wakes you with a word from God, chosen for how you feel.**

Peace Rising turns the first moment of the day into a moment with scripture. When the alarm rings, you silence it by answering one question: *How are you feeling this morning?* A couple of quick follow-up questions later, the app gives you Bible verses matched to your morning, a short prayer and a moment to reflect. **Peace Rings** then links you with people who wake up at the same time, so you can pray together.

No account is needed for the alarm, check-in or journal. An account is only needed to join Peace Rings.

**Live demo:** [peace-rising.vercel.app](https://peace-rising.vercel.app)

> This is a working web prototype built for demonstration. The native iOS and Android apps are planned (see [Roadmap](#roadmap)).

---

## The problem

Many people reach for their phone the moment they wake up, and the first things they see are news, notifications and social feeds. That sets the tone for the whole day. People of faith often *want* to start the day with God but struggle to build the habit.

Peace Rising puts that moment where the habit already is: the alarm clock.

## How it works

1. **Set your alarm** before bed. The app offers a verse to sleep on.
2. **Wake to a gentle chime** that grows slowly, with a sunrise on screen.
3. **Silence it by checking in.** Choose how you feel (for example Anxious, Tired, Grateful or Sad), then answer two quick questions about what's behind it and what you need most.
4. **Receive scripture** matched to your answers, with a short prayer and a reflection prompt.
5. **Pray together** in Peace Rings, a small group (a "ring") of people whose alarms go off around the same time as yours.

## What's in the demo

| Area | What you can try |
|---|---|
| **First launch** | A launch animation, then welcome, optional first name, wake-up time, morning themes and notifications. No account needed. |
| **Alarms** | Create, edit, toggle and delete alarms with repeat days. A countdown to the next alarm and a bedtime verse. |
| **Wake-up** | A full-screen sunrise with a chime that grows louder. Snooze, or tap "I'm awake" to start the check-in. A sound check reminds users to turn off Silent mode. |
| **Morning check-in** | 8 moods, a mood-specific follow-up question and a "what do you need" question. Choosing a mood silences the alarm. |
| **Your word for this morning** | 3 verses picked from a tagged library, each labelled with what it matched. Includes a short prayer, a reflection box, and buttons to save a verse or share it to your circle. |
| **Safeguarding** | If someone says they feel hopeless, a support card appears before the verses, encouraging them to reach out to someone they trust or to local crisis services. |
| **Journal** | Day streak, a 7-day mood strip, mood history, saved verses and past mornings. |
| **Peace Rings** | Guests see a preview of their matched ring and a "Join Now" button. After 4 seconds a "Create a free account to join" prompt slides up; "Join Now" opens the sign-in window with an app-style zoom from the button, and sign-up steps slide in like iOS screens. After sign-up: a ring matched to your alarm time, prayer requests with an "I prayed" button, anonymous posting, ring chat and other rings to join. |
| **Find rings** | Search rings by campus, city, church or language, set your campus, and filter by My campus, Near me, International students, New believers, Churches, From home, Language groups or Online. Verified badges and safety guidance help students new to a country find trustworthy communities. Guests can browse; joining needs an account. |
| **Accounts** | Sign up with Apple, Google, phone number (SMS code) or email, only from Peace Rings or the account button. Includes an 18+ confirmation, an offer to back up the journal, and sign out. Accounts are simulated in the demo. |
| **Profile** | Members tap their avatar (top right of Peace Rings or Alarms) to edit their name, city, a line about themselves, avatar colour, morning themes and ring privacy; turn journal backup on or off; sign out; or delete their account. |
| **Settings** | A gear button next to the avatar on every page. Light, dark, dark by time of day, or follow the phone; four accent colours; four ring chimes and five nature sounds with previews; gentle wake, snooze length and vibrate; whether a check-in is needed to silence the alarm; verses per morning; and a bedtime reminder. |
| **Desktop view** | "Explore on Desktop" (or adding `#desktop` to the link) opens a full-screen desktop layout: a sidebar menu over a slowly drifting navy-and-teal gradient, with glass panels. "Phone view" switches back. |

**Demo tips**

- Turn your sound on, and on a phone turn off Silent mode. The alarm is part of the experience.
- On a laptop, the page shows the app in a phone frame with demo controls. Scan the QR code to open it on your phone.
- On iPhone, open the link in Safari, then tap **Share > Add to Home Screen** to use it full screen like an installed app.
- **Reset demo** (in the side panel, or at the bottom of the Alarms screen) restores the starting state. **Replay onboarding** and **Replay intro** show the first-launch flow and launch animation again.

> Journal history and Peace Rings members are sample data for demonstration. No real accounts are created, and everything you enter is saved only in your own browser.

## How verses are chosen

Each verse in the library is tagged with the moods, situations and needs it speaks to (for example `anxious`, `money`, `peace`). Your three answers are matched against those tags, and the three best-matching verses are shown. Each verse card shows which of your answers it matched.

This approach is deliberate: verses come from a **curated, reviewed library** and are never generated. In the full app, the library will be reviewed by pastors and theologians, and AI may help personalise *which* verses are chosen, but never write or paraphrase scripture.

Scripture is quoted from the **King James Version (KJV)**, which is in the public domain.

## Technical overview (prototype)

The prototype is deliberately simple, so it runs anywhere with no build step.

- **One HTML file** with plain HTML, CSS and JavaScript, and no frameworks.
- **Web Audio API** generates the alarm chime in code, so there are no audio files.
- **localStorage** saves alarms, check-ins and saved verses on the user's own device.
- **Progressive web app** setup (web app manifest, home-screen icons and iOS meta tags), so it can be added to a phone's home screen.
- **Hosting:** Vercel, deploying automatically from this GitHub repository.

```
peace-rising-site/
├── index.html            # The whole app: markup, styles, logic and verse library
├── manifest.json         # Web app manifest (name, colours, icons)
├── apple-touch-icon.png  # iPhone home-screen icon
├── icon-192.png          # App icons
└── icon-512.png
```

### Run it locally

No install is needed. Download the repository and open `peace-rising-site/index.html` in a browser.

To serve it locally (recommended, so the manifest and icons load):

```bash
cd peace-rising-site
python3 -m http.server 8000
# then open http://localhost:8000
```

### Deploy

Vercel is connected to this repository with **Root Directory** set to `peace-rising-site`. Any change committed to `main` goes live automatically within about a minute.

## Roadmap

**Phase 1: Native app (MVP)**
- iOS and Android apps built with **React Native (Expo)**.
- Reliable alarms using Apple's **AlarmKit** (iOS 26+) and Android's **AlarmManager**, so alarms ring even when the phone is locked or on Silent.
- User accounts and cloud sync with **Supabase**.
- An expanded, theologically reviewed verse library, with more translations licensed through **API.Bible**.

**Phase 2: Peace Rings**
- Real rings grouped by alarm time window, with live chat and morning voice prayer.
- Accounts with Sign in with Apple, Google, phone (SMS) and email, required only for Peace Rings and journal backup.
- Safety by design: 18+ age gate, phone verification, anonymous requests, mute, report and human moderation.

**Phase 3: Growth**
- Personalised devotionals, guided prayer audio and rings for churches and small groups.
- Optional AI personalisation, grounded only in the curated verse library.

### Platform note

On Android, the app can require the check-in before the alarm stops. On iOS, Apple shows its own alarm controls, so users can always stop an alarm without opening the app. The iOS design makes "open Peace Rising" the natural next step rather than forcing it.

## Accounts: only where they're needed

Peace Rising works fully without an account: alarms, check-ins, verses and the journal are saved on the phone. People are asked to sign up only when they choose to join **Peace Rings**, because a prayer community needs verified members, an 18+ age check and the ability to report people. This keeps the first experience quick and follows Apple's App Store guidance not to require sign-in for features that don't need it.

## Wellbeing and privacy

- Mood and journal entries are **personal and sensitive**. In the prototype they never leave the device. The full app will encrypt them, collect only what it needs and comply with applicable data protection law (including Nigeria's NDPA and GDPR where relevant).
- Peace Rising offers encouragement and is **not a substitute for professional help**. When a user signals they are in distress, the app points them to people and services who can help.

## Team

<!-- Add team names, roles and contact details here -->

## License

<!-- Choose a license, e.g. MIT for the code. Scripture text is KJV (public domain). -->
