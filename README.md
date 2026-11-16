# divorcereckoning

Landing page: "The Divorce Reckoning" — https://divorcereckoning.netlify.app

## Deploy

Auto-deploys to Netlify from `main` branch. Push to update.

## Local preview

Open `index.html` in a browser. No build step.

## The Mirror (value first entry)

`mirror/index.html` is The Mirror, the divorce reckoning tool that lives at https://divorce.joinunstuck.com (a GoHighLevel funnel page). `mirror/ghl-paste.html` is the same tool as a block for GoHighLevel's Custom JS/HTML element.

What changed from the live version:
- The first screen is the phase choice. One tap on a phase opens that phase's mirror. No email wall before he has seen anything.
- Name and email are asked after he has seen his mirror and right before the part where he writes ("Put your name on it"). Same webhook, same `mirror_intake` event and `source`; the lead now also carries `phase` and `capture_point: "after_mirror"`.
- The overview screen is gone; its two stats and the "this tool will not agree with your victim story" line sit under the phase cards.
- The logo no longer shows a black box (it blends into the page).
- The closing attribution reads @MRUNSTUCK.
- Plain events go to `window.dataLayer` if the page has one: `mirror_phase_pick`, `mirror_gate_view`, `mirror_gate_submit`, `mirror_results_sent`.
- `mirror/index.html` is `noindex`. Everything after the gate (ownership, framework, declaration, results email) is unchanged.

Put it live on divorce.joinunstuck.com (GoHighLevel pages cannot be edited from outside GoHighLevel):
1. Open the funnel page in the GoHighLevel builder, find the Custom JS/HTML element that holds the tool.
2. Select all of its code and replace it with the whole of `mirror/ghl-paste.html`. Save and publish.
3. Open the page on a phone: the first thing you should see is the three phases, not a form. Tap one, tap Next, and the name and email screen should appear before ownership. Use a test email; the webhook starts the same workflow as before.
- Saves as he goes (added 2026-11-16): answers, checks, percentage and the screen he was on are kept on his device (`mirror_progress_v1`, 30 days). A returning man sees "Pick up where I left off" or "Start over", and is not asked for his email twice. Event: `mirror_resume`.
- Also served at https://joinunstuck.com/mirror/ (copied into the joinunstuck-site repo).
