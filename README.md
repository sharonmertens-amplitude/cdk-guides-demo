# Drivewell Auto Group — Guides & Surveys test site

A self-contained dealership-console lookalike (DMS/CRM style) for testing Amplitude
**Guides & Surveys** against a realistic, clickable surface. All data is fictitious.

## The one thing to edit
Open `index.html` and find this line near the top of the `<script>` block:

```js
const AMPLITUDE_API_KEY = "REPLACE_WITH_YOUR_DEMO_ORG_API_KEY";
```

Paste your **demo org** API key between the quotes
(Amplitude → Settings → Projects → your demo project → API Key).
Set `SERVER_ZONE = "EU"` only if the demo org is in the EU data region.

> The Guides & Surveys (Engagement) install snippet can vary by org. Compare the two
> `<script src="...amplitude...">` lines in the `<head>` against the snippet under
> **Guides and Surveys → Settings → Installation** in the org, and paste theirs over
> these if they differ. This is the most common reason guides don't appear.

## What's built in for testing
- **Role switcher** (Sales Manager / Service Advisor / F&I Manager / BDC Agent) →
  sets the `user_role` user property and changes the visible queue + primary button,
  so per-role guides can be demonstrated by flipping a dropdown.
- **Store + OEM** selectors → set `store_id` and `oem` user properties (mirrors the
  attributes CDK passes via GTM).
- **EN / ES** toggle → sets `language` and swaps copy for localization tests.
- **Stable selectors**: every anchorable element has a `data-guide-target="..."`
  attribute — use these in the visual editor so guides don't break on layout tweaks.
- **Precision events** on every interaction (`Dashboard Viewed`, `Role Switched`,
  `Queue Item Opened`, `Primary Action Started`, `Workflow Completed`, …).
- **Reset first-visit state** button (bottom strip) → resets the Amplitude user so
  first-login guides re-fire on demand.

The app runs even before a key is added — the bottom strip just shows
"not connected" until you paste one in.
