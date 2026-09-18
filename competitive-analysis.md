# Language Learning Apps: Competitive Analysis and Feature Roadmap Inputs

Prepared September 2026 for the learnDE product team. Covers 30+ products: the ten named incumbents (Duolingo, Babbel, Memrise, Busuu, ELSA Speak, Speak, Pimsleur, Lingvist, Tandem, HelloTalk, Rosetta Stone) plus AI-first challengers (Praktika, TalkPal, Loora, Langua, Jumpspeak, Univerbal, Gliglish), input-based and web tools (LingQ, Lingopie, Language Reactor, Readlang, Clozemaster, Anki, Glossika, Speakly, Mango, Language Transfer, Michel Thomas), tutor marketplaces (italki, Preply, Lingoda, Cambly), and general assistants acting as competitors (ChatGPT Voice, Gemini Live, Google Little Language Lessons).

Sources: company blogs and press releases, SEC filings (Duolingo shareholder letters through Q2 2026), Duolingo research papers, Trustpilot, App Store and Play Store reviews, Hacker News and Reddit threads, and independent review sites. Prices vary by region and promotion; treat them as indicative. Claims that rest on a single secondary source are flagged.

---

## Executive summary

1. **The category has converged on one shape**: a gamified beginner course (A1 to A2) plus a bolted-on AI conversation partner sold in a premium tier. Every incumbent shipped an AI chat or call feature between 2024 and 2026. Reviewers rate most of them shallow and say "you can get this free in ChatGPT".
2. **Duolingo owns the habit layer, not the outcome layer.** 58.7M daily users, 84% current-user retention, 600+ streak experiments. Its own effectiveness studies show reading and listening gains; speaking and real listening lag. The 2025 Energy system and AI-first pivot cost it brand trust with free and long-streak users.
3. **The unmet need is B1 to B2 output practice with durable feedback.** "I finished the tree and can't hold a conversation" is the single most repeated sentiment across HN, Reddit and review sites. Apps built for this (Langua, Speak) are web-first, English-heavy, or lack a curriculum.
4. **Billing friction is the loudest one-star driver in the whole category**, ahead of pedagogy. Card-gated trials converting to annual charges, hidden cancel flows, credits that never refund. A transparent pricing model is the cheapest reputational differentiator available.
5. **Accessibility is owned by nobody.** Screen-reader-broken exercises, drag-only word tiles, timers, tiny targets and guilt notifications exclude blind, motor-impaired, ADHD, dyslexic and older learners.
6. **Human exchange has a trust problem AI has not solved.** Tandem and HelloTalk both sit at 2.7/5 on Trustpilot for harassment, dating misuse, ghosting and arbitrary bans.
7. **Professional and exam personas are served only by niche apps and free public portals.** For a German-focused product this means nurses and engineers relocating for work, Anerkennung B2 requirements, telc, Goethe, TestDaF and DTZ exam formats, and Integrationskurs alignment.

---

## 1. Feature Architecture and Core Mechanics

### 1.1 Pedagogical delivery

Five distinct pedagogical families exist in the market. Most successful products blend two.

| Family | Representative apps | How it teaches | Where it breaks |
|---|---|---|---|
| Gamified translation drills with implicit grammar | Duolingo, Mondly, Drops | Short tap and type exercises in a linear path; grammar via optional "Guidebook" tips; stories folded into the path | Narrow input, ceiling near A2; speaking is binary pass/fail; "grammatically valid Japanese no native would say" (AI content) |
| Explicit CEFR curriculum with dialogues | Babbel, Busuu, Lingoda, Mango | 10-15 minute lessons: vocabulary in context, dialogue, explicit grammar note, then spaced review; Busuu adds native-speaker video and community corrections | Progress "slow beyond beginner levels"; little open-ended output; Babbel Live (human classes) discontinued for consumers mid-2025 |
| Immersion without translation | Rosetta Stone | Image-word-audio inference, TruAccent pronunciation scoring on every prompt; 2026 "Sapphire" adds text Chat Missions (web only) | "Adults aren't children"; abstract vocabulary impossible via stock photos; no grammar explanations |
| Frequency-ordered vocabulary with SRS | Memrise, Lingvist, Clozemaster, Glossika, Speakly, Anki | Sentence-context cloze cards, adaptive intervals (Lingvist), fixed expanding intervals (Memrise), FSRS (Anki), mass sentence repetition (Glossika) | Vocabulary "in a vacuum", no speaking; Lingvist users run out of new words after ~15 months; Memrise removed community courses |
| Comprehensible input | LingQ, Lingopie, Language Reactor, Dreaming Spanish, Readlang | Import any text or video; click-to-look-up; words progress unknown to known; dual subtitles; hours-tracked roadmaps | Not for beginners; cluttered UI (LingQ); literal AI translations (Lingopie); no structured path |
| Audio-only graduated recall | Pimsleur, Language Transfer, Michel Thomas | 30-minute hands-free lessons with anticipation prompts at expanding intervals; "thinking method" reasoning out answers | Scripted, formal register, "mind-numbingly" repetitive; no reading, writing or native listening; Michel Thomas audio is ~85% English instructor |

Cross-cutting observations:

- **Spaced repetition is universal but uneven in quality.** Duolingo's Half-Life Regression (2016) and Birdbrain difficulty model absorb forgetting curves into one network updated after every exercise. Anki's open-source FSRS-6 predicts recall better than SM-2 for ~99.5% of collections and needs 20-30% fewer reviews for equal retention. Memrise still uses a fixed schedule (4h, 12h, 24h, 6d, 12d, 48d, 96d, 6 months).
- **Grammar is the fault line between "fun" and "serious" apps.** Duolingo and Rosetta Stone teach it implicitly and get criticised by adults who "want someone to confirm or correct" their theory. Babbel and Busuu teach it explicitly and are recommended for intermediates. Nobody does both well: explanation on demand inside an implicit flow.
- **Speaking is now marketed as core by every leader** (Duolingo Q1 2026: "speaking is now a core part of the product"; Speak: 1B+ spoken sentences per year) but most speaking exercises remain read-this-sentence-aloud with a green tick or red cross.
- **Story and scenario framing has won over topic lists.** Duolingo Stories and Adventures, Memrise scenarios ("ordering food"), Speak's situational roleplays with three objectives, Univerbal's "Language Quests". Users engage more with a task to complete than a vocabulary set to finish.

### 1.2 AI and conversational interfaces

State of the art as of September 2026, ranked by technical depth:

| Capability | Leaders | Notes |
|---|---|---|
| Speech-to-speech conversation (no transcribe-then-LLM-then-TTS chain) | Speak (OpenAI GPT-4o Realtime) | Removes the lag users describe as "waiting for the robot"; weaker at strict instruction-following and phoneme scoring, so Speak keeps a separate Pronunciation Coach |
| Phoneme-level pronunciation scoring | ELSA (proprietary ASR on ~200M hours of learner audio), Rosetta TruAccent, Pimsleur Voice Coach | ELSA colour-codes each sound and shows mouth-position tips; general LLM apps (TalkPal, Duolingo Video Call) have no phoneme scoring at all |
| Configurable correction style | Langua (subtle / explicit / post-call), Speak (in-roleplay hints), Duolingo (post-call recap) | The field is converging on learner-controlled interruption rather than always-on nagging |
| Persistent memory across sessions | Langua (viewable, editable memories since Aug 2025), Duolingo Lily (remembers past calls), Speak Premium Plus (frequent-mistake targeting) | Absence of memory is now a named complaint against Loora, Praktika, Jumpspeak ("repeats herself", "lost context") |
| Avatar video-call tutors | Praktika (photoreal avatars), Duolingo Video Call with Lily (Rive animation), ELSA avatars | Evidence of outcome benefit is thin; reviewers call avatars "distracting" and ask for audio-only; Praktika has no audio-only mode |
| Chat-about-your-own-content | Langua (text and audio import, July 2026), LingQ (AI transcription and simplification), Lingopie Netflix extension (April 2026) | Strong for intermediates; absent from every mass-market incumbent |
| Explain-my-answer | Duolingo (made free to all in Jan 2026, per third-party pricing guides), Lingopie Grammar Coach, Memrise Grammar Buddy | Quality complaints: "shallow", "literal", occasional language mixing |
| AI-generated curriculum at scale | Duolingo (148 courses in April 2025; 20,500 course units in Q1 2026 vs 7,100 per quarter in 2025) | Triggered the "AI slop" backlash; smaller courses (Irish, Japanese) show awkward phrasing and errors |

Where each incumbent gates its AI:

- Duolingo: Video Call and Roleplay in Max (~$168/yr), now migrating down into Super per the Q2 2026 letter. Max was 5% of subscribers at end-2024.
- Babbel Speak (Sept 2025): 28 guided scenarios per language pair, five languages, included in subscription. Guided, not free-form.
- Busuu Conversations (Oct 2024): Premium Plus, initially iOS only.
- Memrise MemBot and AI Buddies: Pro. "Works for basics but lacks conversational depth."
- Rosetta Stone Chat Missions (2026): text-only, browser-only, 25 languages.
- Lingvist: no conversational AI at all.
- Tutor marketplaces (Preply, italki, Lingoda, Cambly): AI framed as homework between human lessons, not a tutor replacement. Users are confused when it is bundled without a clear purpose ("Where is AI?").

**The free competitor.** ChatGPT Voice and Gemini Live (40+ languages, mid-conversation switching, LearnLM Guided Learning) are repeatedly described as "the most underrated language learning tool" and as equal to Duolingo Max's conversation quality. Dedicated apps survive by offering what assistants lack: phoneme scoring, a curriculum, SRS integration, dialect-specific cloned voices, and durable artifacts (error logs, flashcards, level trajectory).

### 1.3 Multimodal interactions that drive engagement

Interaction inventory across the category, with what users say about each:

**High engagement, low complaint**
- Tap-to-order word tiles (Duolingo, Busuu, Babbel): fast, satisfying, works for grammar order. Accessibility problem: drag-only variants exclude motor-impaired users; WCAG 2.2 expects a tap alternative.
- Match pairs (word to translation, audio to text): the most-praised Duolingo exercise for "flow".
- Push-to-talk speaking card with live transcript and per-word highlighting (Speak, ELSA): the moment users feel they are "actually talking".
- In-chat correction with red strikethrough and green rewrite (HelloTalk, Tandem): the single best-liked UI pattern in exchange apps.
- Interactive dual subtitles with click-to-pause and sentence loop (Lingopie, Language Reactor, LingQ sentence mode): intermediates' favourite.
- Hands-free driving mode with CarPlay and Android Auto (Pimsleur): "the one interaction pattern learners consistently praise" in the audio segment.
- Roleplay objective checklist (Speak's three in-scene goals, Rosetta Chat Missions): converts open chat into a task with a finish line.
- Home and lock-screen widgets with a mascot whose mood changes toward midnight (Duolingo): half of widget users hold a 6-month+ streak.

**Engaging but polarising**
- Timed exercises and lightning rounds: engagement for some, "frantic tapping with little retention" for ADHD and older users.
- Photoreal avatar calls (Praktika): novelty appeal, then "distracting"; audio-only requested.
- Mnemonic image "Mems" (Memrise, now AI-generated): loved by long-time users, thinner since the redesign.

**Low engagement or actively disliked**
- Binary pass/fail speech recognition with no explanation of what was wrong (Duolingo, Babbel, Busuu).
- Waveform-matching instead of real speech recognition (Mango).
- Stock-photo image grids for abstract vocabulary (Rosetta Stone).
- Interstitial upsells "every 30 to 90 seconds" (Duolingo free tier).

---

## 2. Retention, Motivation and Habit Loops

### 2.1 Gamification mechanics: what works and what burns users out

**What the data says works (Duolingo's published numbers)**

| Mechanic | Published effect | Source |
|---|---|---|
| Current User Retention (CURR) as north-star | ~6x the DAU impact of MAU-oriented levers; CURR 84% in Q2 2026, rising ~1 point/year | Mazal, Lenny's Newsletter; Q2 2026 shareholder letter |
| Streaks | Users with 7+ day streaks tripled to >50% of DAU; 10M+ users hold 1-year+ streaks | Mazal; Q4 2024 letter |
| Streak Wager (bet gems on 7 days) | D7 retention +14% | Duolingo blog |
| Weekend Amulet | +4% week-later return, 5% lower streak loss | Duolingo blog |
| Leaderboards / leagues | +17% total learning time; highly engaged learners tripled | Mazal |
| Friend Streaks | Learners with a shared streak 22% more likely to complete a daily lesson; one-third of DAU have one | Duolingo blog; Q4 2024 letter |
| Widget | Half of widget users have a 6-month+ streak; better retention controlling for self-selection | Duolingo engineering blog |
| Signup after first lesson | +20% DAU (as retold by Appcues and others) | Mazal |
| Streak Revival event (June 2026) | 15.4M streaks restored, 8M from previously inactive users; DAU growth re-accelerated to +23% | Q2 2026 letter |
| Energy replacing Hearts (2025) | Raised DAU, median learning time and conversion at once | Q2 2025 letter |

**What causes burnout and churn**

- **Streak maintenance replaces learning.** "Logging in at midnight to protect the streak without having studied anything in weeks." Silverman and Barasch (Journal of Consumer Research, 2023) show users treat the streak as the goal and drop off after a break, especially when they blame themselves. A repair option attenuates the drop, which justifies Streak Repair.
- **Leagues create XP farming and sandbagging**: grinding Practice for points, joining late in the week to dodge grinders, "late-night XP anxiety".
- **Energy punishes correct answers.** Draining a unit per exercise regardless of correctness reads as "a cash grab" to free users; Android Authority ran "I'm finally quitting Duolingo after this change"; long-streak loyalists quit publicly. It also capped free practice at roughly 15-20 minutes a day.
- **Interruptions**: pop-ups, badges, gem offers roughly every 30 to 90 seconds in the free tier.
- **AI-first backlash (April to August 2025)**: streak-deletion videos, 400K+ lost TikTok followers, ~41% negative sentiment. DAU still grew 40% in Q2 2025 but at the low end of guidance. Von Ahn dropped AI usage from performance reviews by April 2026.
- **Community loss**: forum removal in 2023 and volunteer contributor removal are still cited churn reasons.

**The counter-movement.** Memrise removed points and de-emphasised leaderboards, and built a "My Activities" view that "doesn't send reminders or notifications, a quiet, guilt-free space". Babbel and Rosetta Stone keep streaks minimal with no leagues or currency and market themselves "for adults". Speak, Langua and Praktika use streaks only. Review sites frame Duolingo as fun-first for beginners and Babbel or Busuu as the intermediate choice. There is a clear gap for retention mechanics that motivate adults without shame or punishment.

### 2.2 Onboarding and personalisation

**Common pattern (Duolingo, roughly 7 screens)**: language, "how did you hear about us", motivation ("why are you learning"), daily goal (Casual 5 min to Intense 20 min), experience level, optional placement test, notification permission, first lesson, then account creation. Each step is both a commitment device and a personalisation signal.

**Variations**
- Busuu: five-minute CEFR placement test that drops the learner into the right unit, plus a Study Plan asking for realistic weekly minutes and a target date. A softer commitment device than a daily streak.
- Babbel: self-declared level (Newcomer to Advanced), weekly goal, short placement quiz for some languages.
- Lingvist: placement is implicit; the SRS calibrates by skipping known words in the first cards.
- ELSA: five-minute speech assessment produces a baseline score and a path highlighting weak sounds.
- Praktika: asks for CEFR level (A1 to C1) but "does not map your learning against a CEFR path or gradually raise complexity".
- Rosetta Stone: no adaptive placement at all, flagged as a weakness for returning learners.

**Adaptive difficulty**: Duolingo's Birdbrain updates learner ability and exercise difficulty after every exercise (teardown claims ~1.25B exercises/day). Lingvist adapts word selection in real time. Langua added CEFR-aligned grammar and "My Path" recommendations (July 2026). Everyone else is a static course with an open chat bolted on. Genuinely CEFR-tracked adaptive speaking remains a promise, not a shipped product.

**Evidence on commitment devices**: explicit commitments with a scheduled payoff (7-day wager) beat vague daily goals. Localised framing matters: telling German users "notifications are proven to foster learning success" lifted opt-in 8%, with no effect in Spanish.

### 2.3 Push notification and re-engagement strategy

**Duolingo's playbook (from Jackson Shuttleworth, Sub Club podcast, and the KDD 2020 bandit paper)**
- Practice reminder fires **23.5 hours after the last session**; behavioural timing beats user-chosen times.
- Daily reminders for **up to 7 days**, then practice pushes stop ("These reminders don't seem to be working. We'll stop sending them for now.")
- Separate **Streak Saver** push before midnight.
- Hard cap of roughly 2 pushes per day; tone shifts by state (active, wobbling, at-risk, dormant).
- The best re-engagement window is **days 1 to 4** after a lapse.
- Copy selected by a sleeping-recovering bandit over 200M notification examples: +0.5% total DAU, +2% new-user retention. A recency penalty models template fatigue.
- Friend-initiated nudges out-click app-initiated ones; even leaderboard strangers beat standard campaigns.
- The Handbook explicitly caps notifications "even when short-term metrics say otherwise".

**Competitor behaviour**: Babbel, Busuu, Rosetta Stone and Lingvist send a scheduled daily reminder at a chosen time. Their complaints are about promotional spam (Lingvist keeps pushing offers to paid users who disabled them), not tone. Memrise removed reminders from its activity view entirely.

**Benchmarks**: median push direct open rate ~3% (Airship 2025), top decile 8-11%. Education opt-in is near the top of categories (~94% Android). 64% of users say they will delete an app that sends 5+ pushes a week. iOS 18.2's revised prompt lifted iOS opt-in to ~54%.

**Win-back at scale**: the June 2026 Streak Revival event is the largest published resurrection campaign in the category. Management called it non-recurring, implying scarcity is part of its power. The 2025 "Duo dies" campaign (1B+ organic views) shows brand-level resurrection stunts also move numbers.

**The cost**: the passive-aggressive owl persona is effective and meme-generating, but anxiety complaints, especially around children, are real and documented (Screenwise, Lumi Academy).

---

## 3. Competitor Feature Matrix

| App | Primary value prop | Standout signature feature | Monetization / paywall trigger | Common user frustration (App Store, Play Store, Reddit, Trustpilot) |
|---|---|---|---|---|
| **Duolingo** | Free, fun, five-minutes-a-day habit in 40+ languages | Streak system with Friend Streaks, widgets and Video Call with Lily | Free with ads and daily Energy cap; Super ~$84/yr removes limits; Max ~$168/yr adds Video Call and Roleplay; Family $120/yr | Energy caps free practice and drains on correct answers; A2 ceiling ("26% fluent in idiot"); AI-first content quality; upsell interstitials; guilt notifications |
| **Babbel** | Linguist-built CEFR courses "for adults" | Explicit grammar notes inside real-life dialogues; Babbel Speak guided AI scenarios | First lesson free; ~$8-15/mo, lifetime $599 list (often ~$299); 20-day refund | Auto-renewal and refund disputes dominate Trustpilot; slow progress past beginner; Babbel Live discontinued; only 14 languages |
| **Busuu** | Structured CEFR path with human feedback | Community of native speakers corrects your written and spoken exercises; AI Conversations | Free limited lessons with ads; Premium ~$6-15/mo; Premium Plus for AI and offline | Silent auto-renewal; inconsistent volunteer corrections; app "not updated in years"; Chegg parent in distress |
| **Rosetta Stone** | Immersion without translation | TruAccent graded pronunciation on every prompt; 2026 Sapphire Chat Missions | 3-day trial, no free tier; ~$12/mo annual; lifetime $199-299, often $149 | No grammar explanation ("adults aren't children"); dated stock photos; no placement test; lifetime buyers asked to pay again; cancellation page "fails to load" |
| **Memrise** | Vocabulary plus native-speaker video | Thousands of "Learn with Locals" native clips; scenario-based SRS; MemBot AI chat | Free with daily caps; Pro ~$23/mo or ~$62-90/yr; lifetime ~$250-330 | Community courses removed (2024), "most controversial change in its history"; content thins after beginner; monthly price "steep for a vocab app" |
| **Lingvist** | Fastest route to the 4-5K highest-frequency words | Adaptive cloze SRS that skips known words; Course Wizard generates decks from any text | ~50 words/day free; ~$80/yr; lifetime ~$100; 14-day card-gated trial | "Pretends to work free"; runs out of new vocabulary after ~15 months; no speaking; promo pushes to paid users |
| **ELSA Speak** | Fix your English pronunciation | Phoneme-level colour-coded scoring on 200M hours of learner audio; IELTS band estimator; Speech Analyzer for uploaded recordings | Free daily caps; ~$160/yr; lifetime $250; Pro tier for unlimited AI roleplay | Trial converts to $130 annual "without clear notification"; no in-app subscription management; dated UI; inflated scores; English only |
| **Speak** | Learn by talking, not tapping | Speech-to-speech Live Roleplay on GPT-4o Realtime with three in-scene objectives | Trial only, no free tier; Premium ~$84/yr; Premium Plus ~$165/yr for unlimited custom lessons | ASR mishears accents yet passes mispronunciations; American English only, no dialect choice; repetitive at higher levels; six languages |
| **Pimsleur** | Hands-free audio fluency in 30 minutes a day | Graduated Interval Recall with CarPlay and Android Auto driving mode | $20/mo per language; 7-day trial; lifetime ~$299 on deal | "Mind-numbingly" repetitive phrases; formal register; one lesson a day gating; phone-only cancellation |
| **Tandem** | 1-to-1 language exchange with natives | Correction preferences (flag every mistake vs general feedback); Parties audio rooms; Tandem GPT | Free: 3-5 translations and 10 new chats/day; Pro $80/yr | Dating-app misuse ("Hey beautiful"), scammers, ghosting after 3 exchanges, bans without explanation; "paying to fix problems that shouldn't exist" |
| **HelloTalk** | Free exchange at scale (70M+ users, 260 languages) | In-chat red-strikethrough / green-rewrite correction; Moments feed; Voicerooms with Azure live captions | ~90% free; VIP $5-10/mo unlocks unlimited translation and gender/location filters | Harassment of women; arbitrary bans of paying VIPs; political censorship; gender filters "enable targeted misuse" |
| **Praktika** | A human-feeling AI tutor at app prices | Photoreal lip-synced avatar tutors with personalities | 7-day card trial; $50 per 3 months minimum; $120/yr | Trial charges full annual early; avatar "repeats herself"; no audio-only mode; no CEFR progression |
| **TalkPal** | Breadth: 130+ languages, nine practice modes | Photo mode (describe an AI image), Characters, Debate | 10 min/day free; ~$90-120/yr | Robotic voices; no grammar syllabus; feedback depth "extremely limited"; charges after cancellation |
| **Loora** | Workplace English coach for professionals | Hands-free continuous conversation, no push-to-talk | ~$119/yr, or ~$30/mo weekly-renewing; "most expensive in category" | Hard-to-cancel "partially fraudulent practices"; forgets earlier sessions; surface-level topics |
| **Langua** | Intermediate-plus conversation with real voices | Cloned native-speaker dialect voices; editable AI memory; subtle/explicit/post-call correction modes; import your own audio | Communicate plan capped at 75 messages and 30 call-minutes a day; Unlimited ~$200/yr; 30-day refund | Slow AI chat at times; web-first UX on mobile; not for absolute beginners; price |
| **LingQ** | Comprehensible input from any content | Word-status colouring (blue to yellow to known) across imported text, audio and video | 20 saved words free (demo only); ~$10/mo annual; Premium Plus ~$22/mo | Cluttered interface; "non-transparent billing"; unapproachable support; no structure for beginners |
| **Lingopie** | Learn from real TV and film | Dual-language interactive subtitles with click-to-save flashcards; Netflix Chrome extension (2026) | ~$144/yr; lifetime $760 list; 7-day trial | Difficult cancellation; literal AI translations; shallow Grammar Coach; better for intermediates |
| **italki** | Pay-per-lesson human tutors | Marketplace from $5/hr community tutors; italki Plus AI homework | No subscription; credits per lesson; Plus ~$6/mo | Credits never refund to cash, expire after 12 months; teacher no-shows; 40% tutor commission; "detest the AI tools" |
| **Preply** | Human-led, AI-enhanced tutoring | Lesson Insights, Daily Exercises and Scenario Practice generated from your tutor lesson (OpenAI) | Weekly-hours auto-renewing subscription | Impossible to pause; refunds void once any hour used; cancel means losing paid lessons; chatbot support |
| **Lingoda** | Live CEFR group classes on Zoom | Sprint cashback challenge; AI class reports | ~$8-23 per class; Marathon ~EUR 369/mo | 72-hour cancellation forfeits credit; popular slots full; "too much English in class" |
| **Mango Languages** | Library-funded, 70+ languages incl. endangered | Colour-coded literal vs loose translation chunks | Free via public libraries; $8-18/mo | "Far too shallow", ends around B1; waveform matching, not speech recognition |
| **Glossika** | Mass sentence repetition, 60+ languages | 3,000 sentences per language with six practice modes | $199-399/yr | Overpriced for one language; errors in materials; no grammar; monotone voices |
| **ChatGPT Voice / Gemini Live** | Free, unlimited conversation in 40+ languages | Mid-conversation language switching; Guided Learning scaffolding | Free or bundled with general subscription | No curriculum, no pronunciation scoring, no SRS, no progress tracking |

---

## 4. White-Space Analysis and Market Gaps

### 4.1 Speaking fluency and real-world conversation readiness

**The gap in one sentence**: apps grade recitation, not communication. Reading a sentence aloud into a binary pass/fail recogniser is what Duolingo, Babbel, Busuu and Mango call "speaking". Even Speak and Duolingo Video Call get "AI conversations that loop the same three phrases" and calls that "last about 30 seconds".

Specific gaps no leader closes:

1. **No bridge between scripted and free speech.** Products are either fully scripted (Pimsleur, Babbel Speak's 28 guided scenarios) or fully open (TalkPal, ChatGPT). Nobody scaffolds from "repeat this" to "answer with a hint" to "say it another way" to "improvise" inside one scene.
2. **Correction without conversation flow.** Always-on correction interrupts; end-of-call recaps arrive too late to fix a habit. Only Langua lets learners choose subtle, explicit or post-call correction, and it is web-first.
3. **Pronunciation and conversation are separate products.** ELSA scores phonemes but conversation is thin; Speak converses fluently but its recogniser "mishears clear accented speech" and passes mispronunciations. No end-to-end speech model does both well yet, so the winning architecture is speech-to-speech for flow plus a dedicated scoring path for drills.
4. **Dialect and accent choice is almost absent.** Speak defaults to American English with no British or Australian option; Spanish variant selection is rare; Arabic apps force a choice of MSA or one dialect; Swiss German apps are "mainly for tourists". Langua's cloned regional voices are the only serious attempt. For German this means Austrian and Swiss variants, regional register, and Hochdeutsch vs colloquial speech.
5. **Listening to real natives is untrained.** Michel Thomas is 85% English instructor audio; Pimsleur is studio-clean and formal; Duolingo TTS is uniform. Learners report being "almost entirely useless" in real conversation despite daily practice. Busuu and Memrise native video clips are the exception, and both are short.
6. **No durable artifacts from speaking.** Conversations evaporate. TalkPal, Jumpspeak, Praktika and Loora have no error log, no SRS card from a mistake, no level trajectory. Langua logs vocabulary to flashcards; Speak Premium Plus targets frequent mistakes. Both are paywalled top tiers.
7. **Human exchange is unsafe and unproductive.** Tandem and HelloTalk score 2.7/5. "Most conversations lasted less than three exchanges." A supervised, structured, AI-moderated way to reach real humans does not exist.

### 4.2 Accessibility, cognitive load and UI clutter

- **Screen readers**: AppleVis threads document Duolingo ads that cannot be exited in VoiceOver, Continue buttons that do nothing on double-tap, no audio cue for right or wrong answers. A design critique calls it "visual-first design excluding the blind learners the platform claims to serve".
- **Motor impairment**: drag-and-drop word tiles are "a massive barrier for users with motor tremors". WCAG 2.2 requires a single-pointer alternative.
- **ADHD and dyslexia**: "bright animations, endless notifications, crowded lesson screens, pressure to maintain streaks"; hearts and timers produce "frantic tapping with little retention". Requests: dyslexia-friendly fonts, adjustable spacing, synchronised text-to-speech highlighting, no timers by default.
- **Older adults**: "tiny fonts, low-contrast backgrounds, tap targets smaller than a fingertip"; the "figure it out from patterns" pedagogy frustrates adults who want rules confirmed. Cambridge ReCALL research confirms older learners want explicit correction.
- **Hearing-impaired**: listening exercises with no transcript fallback; speaking tasks with no alternative modality.
- **Cognitive load and clutter**: Duolingo's free tier interrupts roughly every 30 to 90 seconds with pop-ups, badges, gems and upsells. LingQ and italki are called "cluttered" after redesigns. Lingopie's dashboard is "confusing". Memrise's redesign "cluttered" a previously simple app.
- **Children**: speech grading produces false negatives on genuinely close attempts; uncurated ads in the free tier; documented streak anxiety.

Not a single competitor markets accessibility as a feature. Meeting WCAG 2.2 AA with tap alternatives, no default timers, large targets, transcripts everywhere and a quiet mode would be a category first.

### 4.3 Underserved personas

| Persona | What they need | Who serves them today | Gap |
|---|---|---|---|
| **Intermediate plateau learners (B1 to B2)** | Varied real input, output practice, feedback on nuance, grammar on demand | Langua, LingQ, Lingopie, tutors; new niche apps (BlablaPal, Polygloss) | Every mass-market app ends at A2 or B1; HN: "There's no one resource that will get you to even an intermediate level"; JLPT learners call N3 to N2 the "Valley of Death" |
| **Professional relocators** (nurses, engineers, IT workers moving to Germany, Netherlands, Japan) | Domain vocabulary (Pflege, Handwerk, Büro), register for workplace, B2 for Anerkennung, telc B2 Pflege exam format | Tiny niche apps ("German for Nurses"), Elsevier textbooks, Deutsch am Arbeitsplatz, Loora (English only) | Generalist apps have no domain tracks; B2 Anerkennung requirement is a hard, dated, high-stakes goal nobody maps to |
| **Exam candidates** (Goethe, telc, TestDaF, DTZ, DELF, JLPT, IELTS) | Exam-format speaking and writing practice with rubric scoring, timed mocks | ELSA (IELTS band estimator), GPP Goethe Prep, Gibi Exam Prep, Bunpro, WaniKani | Mainstream apps offer no exam-format practice; speaking-part rehearsal with examiner-style AI is wide open |
| **Immigrants and integration-course learners** | Alignment with Integrationskurs curriculum and DTZ; menus in their own language; life-admin scenarios (Ausländerbehörde, Jobcenter, Kita) | vhs-Lernportal (free, BAMF-recognised, A1 to C1, menus in 20 languages) | Commercial apps ignore this population entirely |
| **Heritage speakers** | Start from listening comprehension, fix production and literacy, no zero-level insult | eTandem exchange (academic literature) | Every app starts from zero; Duolingo blogs about "no sabo kids" but has no track |
| **Conversationalists vs test-preppers** | Two different goals: sound natural and confident vs pass a rubric | Speak and Praktika (conversation); ELSA (test) | No product lets the learner switch goal mode with different scoring and content |
| **Older adults** | Explicit rules, large type, no timers, patient correction | None explicitly | Untapped and growing |
| **Learners of dialects and regional variants** | Austrian and Swiss German, Latin American vs Peninsular Spanish, Arabic dialects | Langua cloned voices; uTalk and Mango for rare languages | Almost no dialect choice anywhere |
| **Kids** | Curated, safe, no ads, no streak anxiety | Duolingo ABC, Lingopie kids mode | Duolingo for Schools sunsets July 2027 |

### 4.4 Pricing and trust gaps

- Trial-to-annual surprise charges are the top one-star driver for ELSA, Praktika, Loora, TalkPal, Jumpspeak, Lingopie, Babbel and Busuu.
- Cancellation friction: Rosetta Stone's cancellation page "fails to load", Pimsleur cancels by US phone line only, ELSA has no in-app subscription management, Preply cannot be paused.
- Credit traps: italki credits never refund to cash and expire after 12 months idle; Lingoda's Sprint forfeits credit at 72 hours.
- Lifetime-deal saturation (Babbel, Rosetta Stone, Memrise, Mondly) angers earlier full-price buyers; Rosetta "lifetime" buyers from 2018 were asked to pay again in 2022.
- Duolingo Max at ~$168/yr is "flat out too expensive" and its headline feature (Explain My Answer) went free in January 2026, undercutting the tier.

A product with an in-app cancel button, a no-card trial, transparent minute or lesson caps, and renewal reminders would differentiate on Trustpilot alone.

### 4.5 Market context

- Category revenue ~$1.54B in 2025 (+18.8%), 327M downloads; top five providers hold ~58% of revenue, up from 39% five years earlier.
- Duolingo FY2025 revenue $1.04B (+39%), 12.7M paid subscribers and 58.7M DAU by Q2 2026; 2028 target 100M DAU. Over 40% of Babbel, Busuu, Pimsleur and Rosetta users also use Duolingo; under 2.5% of Duolingo users use those rivals.
- Speak passed $100M annualised revenue at a ~$1.17B valuation; Preply raised $150M at $1.2B (Jan 2026); Praktika raised $35.5M on 1.2M MAU.
- Consolidation and exits: Mondly (Pearson) stops marketing June 2026; Duolingo for Schools sunsets July 2027; Chegg is restructuring around Busuu with a ~$48M 2026 revenue target.
- Retention benchmarks: cross-industry D1 ~25%, D7 ~12%, D30 5-7%; education D30 often 2-3%, with 10%+ considered strong. Duolingo's 84% CURR and 41.7% DAU/MAU are extreme outliers.

---

## 5. Recommended Feature Backlog

Organised for a new product whose wedge is **conversation readiness for adult learners from A2 upward**, with German as the launch language given the learnDE context. Each item names the competitor shortcoming it answers.

### Tier 1: Table Stakes (must-have for MVP)

| Feature | Why it is baseline | Competitor reference |
|---|---|---|
| CEFR-aligned structured path (A1 to B2) with explicit, on-demand grammar notes | Adults and intermediates leave implicit-only apps; Babbel and Busuu are recommended for this reason | Babbel, Busuu |
| Spaced repetition using an FSRS-class scheduler that feeds from every exercise and conversation | 20-30% fewer reviews than SM-2 at equal retention; nobody in the mass market exposes this quality | Anki FSRS, Lingvist |
| Core exercise set: tap-to-order tiles (with tap-to-select alternative), match pairs, listen-and-type, fill-the-gap, speak-the-line | The interaction vocabulary users already know | Duolingo, Busuu |
| AI conversation partner with speech-to-speech latency and a task checklist per scene | Every incumbent has one; latency and "three objectives" framing are the current bar | Speak, Duolingo Video Call |
| Pronunciation feedback at the word level minimum, phoneme level on drill cards, with a separate scoring path from the conversation model | Binary pass/fail is the top speaking complaint; no single model does both flow and scoring | ELSA, Rosetta TruAccent |
| Placement test (5 minutes) plus weekly time commitment and target-date study plan | Softer commitment device than daily streaks; adults respond to a realistic plan | Busuu Study Plan |
| Streak with forgiveness built in: free freeze, 3-day repair window, weekend flexibility | Streaks work (D7 +14% with wager) but repairable breaks prevent the post-break cliff | Duolingo, Silverman and Barasch 2023 |
| Behaviour-timed reminders (23.5 hours after last session), capped at 1-2 per day, auto-stop after 7 days, tone never shaming | The published Duolingo cadence minus the guilt persona | Duolingo, Memrise quiet mode |
| Home and lock-screen widget showing today's status | Half of widget users hold 6-month+ streaks | Duolingo |
| Offline lessons and audio | Paywalled by most; expected by commuters | Pimsleur, Babbel |
| WCAG 2.2 AA from day one: no drag-only tasks, no timers by default, 44pt targets, AA contrast, transcripts for all audio, VoiceOver and TalkBack tested exercises, dyslexia font option | Zero competitors meet this; documented exclusion of blind, motor-impaired, ADHD and older learners | AppleVis complaints |
| Transparent pricing: no-card trial, in-app cancel, renewal reminder 7 days before charge, clear free-tier caps | The single loudest one-star theme category-wide | ELSA, Babbel, Praktika complaints |
| Progress dashboard tied to CEFR (a shareable level score) | Duolingo Score sharing to LinkedIn shows demand for a credible number | Duolingo Score, ELSA IELTS estimator |

### Tier 2: Key Differentiators

| Feature | Competitor shortcoming solved | Design notes |
|---|---|---|
| **Scaffolded speaking ladder inside every scene**: repeat, answer with hint, say it another way, improvise. Learner or system moves up a rung when accuracy holds | Apps are either fully scripted or fully open; no bridge to free speech | Track rung per scenario; surface "you improvised for the first time" as a milestone |
| **Correction style as a user setting** (subtle in-flow, explicit interrupt, post-conversation debrief) plus "ask me to repeat the correction" | Always-on nagging vs too-late recaps; only Langua offers this and only on web | Default to post-conversation for A2, subtle for B1+ |
| **Every conversation leaves artifacts**: error log grouped by grammar pattern, auto-generated SRS cards from mistakes, vocabulary you produced vs understood, and a level trajectory chart | TalkPal, Praktika, Loora, Jumpspeak conversations evaporate | The FSRS scheduler consumes conversation errors, not just lesson misses |
| **Visible, editable tutor memory** ("you work as a nurse in Hamburg, you struggle with dative after prepositions") | Absence of memory is a named complaint; Langua is the only app that exposes it | Show what the tutor remembers; let users delete or correct entries |
| **Domain tracks for professional relocators** (healthcare, engineering, IT, hospitality, trades) mapped to the telc B2 Pflege and Anerkennung requirements | Served only by tiny niche apps and textbooks | Content authored with domain experts; scenarios like Übergabe, Patientenaufklärung, Baustellenbesprechung |
| **Exam mode**: examiner-style AI for Goethe, telc, TestDaF and DTZ speaking parts with the real rubric, timed mocks, and rubric-based scores | Mainstream apps have no exam-format practice | Rubric transparency is the trust builder; show the criteria before the score |
| **Life-admin scenarios for newcomers** (Ausländerbehörde, Jobcenter, Kita registration, Hausarzt, Mietvertrag) with the actual forms and phrases | Commercial apps ignore integration learners; vhs-Lernportal is the only reference | Also the most shareable content for immigrant communities |
| **Dialect and register selector** for both tutor voice and recogniser expectation (Hochdeutsch, Austrian, Swiss; formal Sie vs informal du) | Speak's American-only default is a repeated complaint; Langua's cloned voices are the only attempt | Cloned voices from consenting regional speakers |
| **Real native listening layer**: short unscripted clips of real speakers with interactive dual transcripts, feeding the SRS | Studio-clean audio leaves learners "useless" in real conversation | Busuu and Memrise clips are the proof of demand; add scrubbing and sentence loop |
| **Chat about your own content**: import a work email, a Netflix subtitle file, a podcast episode, a news article; the tutor builds a lesson and conversation from it | Only Langua and LingQ do this, both web-first and unstructured | Strongest hook for the B1 to B2 plateau |
| **Hands-free mode** with CarPlay and Android Auto for conversation and review | Pimsleur owns the pattern but with scripted, repetitive content | Voice-only turn-taking with no screen dependency |
| **Supervised human exchange**: matched 15-minute structured sessions with a scenario card, AI moderation, no gender or location filters, no profile browsing, post-session AI debrief | Tandem and HelloTalk at 2.7/5 for harassment, dating misuse and ghosting | Removes the dating-app affordances that enable misuse |
| **Heritage-speaker entry point**: placement that starts from listening comprehension and targets production and literacy gaps | Every app starts from zero | Small persona, large loyalty |
| **Human-authored core curriculum, AI for personalisation only, stated publicly** | Duolingo's AI-first backlash created a trust opening; Babbel and Mango already position on this | Publish who wrote and reviewed each unit |

### Tier 3: Delighters

| Feature | Why it spreads |
|---|---|
| **"First improvised sentence" moment**: the app captures and plays back the first time you answered without a hint, with a shareable card | Emotionally bigger than any XP number; Speak users describe "the moment I felt I was actually talking" |
| **Weekly voice diary** (60 seconds, prompted) with a side-by-side playback of week 1 vs now | Progress in speaking is invisible; hearing yourself improve is the proof learners crave |
| **Monthly "Year in Review"-style speaking report** showing minutes spoken, patterns fixed, words produced, with an XP-free shareable card | Duolingo's most-shared asset is the percentile card; a speaking version is unowned |
| **Friend Streak lite**: pair with one friend or partner, not five, on a shared weekly goal | Friend-driven win-back out-clicks app messages; a shared streak lifts daily completion 22% |
| **Quiet mode toggle**: turns off all animation, sound, badges and reminders in one tap | Memrise's guilt-free view is loved; ADHD and older users ask for exactly this |
| **Pronunciation "mouth cam" tips**: when a phoneme fails three times, show a short native-speaker clip of the mouth position | ELSA's most-praised feedback element |
| **Say it three ways**: after any correct answer, an optional prompt to rephrase (more formal, more casual, shorter) | Trains flexibility, the real B2 skill, in 10 seconds |
| **Scene remix**: after finishing a scenario, one tap regenerates it with a twist (the waiter is rude, the train is cancelled) | Kills the "same three phrases" repetition complaint |
| **Streak Revival as an annual event**, not a paid repair | Duolingo's June 2026 one-off restored 15.4M streaks and re-accelerated DAU; scarcity is the point |
| **Localised motivation copy** tested per language market (German opt-in +8% with a research-backed framing) | Cheap, measurable, and nobody but Duolingo does it |
| **Community-corrected writing with reputation**, opt-in, moderated, with the red-strikethrough green-rewrite UI | Busuu's most unique feature and HelloTalk's best-liked UI, minus the volunteer-quality lottery |
| **Regional culture snippets** inside scenarios (why Germans say "Mahlzeit", what a Pfand machine does) | The one content type learners screenshot and send to friends |

---

## Appendix A: Evidence highlights by source type

- **SEC filings**: Duolingo Q4 2025, Q1 2026 and Q2 2026 shareholder letters (CURR 84%, DAU 58.7M, paid subs 12.7M, Streak Revival 15.4M restores, Video Call moving into Super).
- **Duolingo research and blog**: Half-Life Regression (2016), Birdbrain (2020), sleeping-recovering bandit for notifications (KDD 2020, +0.5% DAU, +2% new-user retention), streak research (Wager D7 +14%, Weekend Amulet +4%), widget post, copy-testing post (German opt-in +8%), Handbook.
- **Growth teardowns**: Jorge Mazal in Lenny's Newsletter (CURR 6x lever, DAU 4.5x, leaderboards +17% learning time); Jackson Shuttleworth on Sub Club (23.5-hour reminder, 7-day stop, days 1-4 window).
- **Academic**: Silverman and Barasch, Journal of Consumer Research 2023 (streak goal substitution and repair effect); CALICO Journal and Language Learning and Technology 2024 (Duolingo A2 completers reach Intermediate Low to High on reading and listening, speaking lags); Sutton and Webb 2026 meta-analysis on audiovisual input; Anki FSRS open benchmark (500-700M reviews).
- **Review sentiment**: Trustpilot (Tandem 2.7, HelloTalk 2.7, Cambly 2.1, Jumpspeak 3.2, Busuu 4.3 with auto-renewal as top theme); AppleVis accessibility threads; Hacker News "An opinionated critique of Duolingo" (Oct 2025) and "Ask HN: Does Duolingo Work?"; Class Central and Android Authority on Energy; TechCrunch on the AI-first backlash.
- **Market data**: Business of Apps and Sensor Tower (category $1.54B 2025, 327M downloads, top five at 58% share, 40%+ rival-user overlap with Duolingo); Forbes on Speak ($100M+ ARR); Airship 2025 push benchmarks.

## Appendix B: Caveats

- Prices are indicative and regionally variable; several are from third-party pricing guides rather than first-party pages.
- Reddit is poorly indexed; Reddit sentiment is drawn from secondary roundups and directly fetched Hacker News threads.
- Duolingo's "Explain My Answer went free in January 2026" and Video Call moving into Super are reported by third-party guides and the Q2 2026 letter respectively; verify before citing externally.
- Retention multipliers from teardown sites (for example "2x daily retention for streak holders") are unverified; Duolingo-published figures are marked as such.
