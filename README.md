# Sugar Log

A small offline app for logging blood sugar readings on an Android phone:
before each meal, 2 hours after each meal, and random checks during the day.

## What it does

- **English / हिंदी:** tap the language button in the header (or Settings →
  Language) to switch all of the app's text, dates, alerts and CSV exports
  between English and Hindi. Phones set to Hindi start in Hindi.
- **Automatic date & time:** a new reading is stamped with the phone's current
  date and time when you tap Save, so there's nothing to type. Editing a reading
  keeps its original time. Past days in the Timesheet can't be filled in later;
  only today's empty cells open the form.

- **Today:** a progress bar for today's scheduled readings (e.g. 3 / 6), a
  daily streak, and a reminder card showing when the 2-hour after-meal reading
  is due. Readings are coloured green (in target), amber (high), red (very high)
  or purple (low).
- **Timesheet:** one row per day and one column per slot (Breakfast / Lunch /
  Dinner, each split into Pre and 2h Post), plus Random, Done and Avg columns.
  You can view 7, 14, 30 or 90 days, or everything. Tap an empty cell to fill it
  in, or tap a value to edit it.
- **Progress:** logging completion over 7 and 30 days, time spent in your target
  range, averages before and after meals, and a 14-day trend chart.
- **Meds:** add your medicines (name, dose) and choose when you take each one:
  morning before breakfast, after lunch and/or after dinner. Tick doses off each
  day; each shows Upcoming, Due now (for 3 hours after its time) or Missed.
  There's a 7-day history, and a 💊 column in the Timesheet and a "Medicines
  taken" card in Progress. The Meds tab shows a red dot when a dose is due.
- **Reminders:** set the three reminder times on the Meds tab (default 7:30,
  14:00, 21:00). Two kinds of alert:
  - **⏰ Phone alarm (most reliable):** on Android, tap ⏰ next to a time to open
    the Clock app with that alarm filled in, then set it to repeat daily. It
    rings even when Sugar Log is closed.
  - **🔔 App notifications:** alerts for due medicines and 2-hour sugar checks,
    but only while the app is open or was used recently. A web app can't
    schedule alerts while it's fully closed.
- **Settings** (gear icon, top right): choose mg/dL or mmol/L, pick which meals to track, set the
  after-meal reminder gap (default 120 min), set your target ranges, export to
  CSV (opens in Excel or Google Sheets), and back up or restore your data.

Your data is stored only on the phone, in the browser's storage for the site
the app is served from. Nothing is sent anywhere. Use **Settings → Backup file**
now and then, because clearing Chrome's site data deletes your readings.

## Putting it on your Android phone

To install as an app (home-screen icon, works offline) it has to be served over
HTTPS. The simplest free options:

1. **Netlify Drop:** go to https://app.netlify.com/drop and drag this whole
   folder onto the page. You'll get an `https://….netlify.app` link.
2. **GitHub Pages:** push this folder to a repository and turn on Pages.

Then on the phone, open the link in **Chrome**, tap **⋮ → Add to Home screen /
Install app**, and open Sugar Log from the home screen.

Quick test on your home Wi-Fi (no install or offline support):

```bash
python3 -m http.server 8000
```

Run that in this folder, then open `http://<your-mac's-IP>:8000` on the phone.

## Files

- `index.html`: the whole app (HTML, CSS and JS)
- `manifest.webmanifest`, `icon*.png`, `icon.svg`: app name and icons for install
- `sw.js`: service worker that lets the app work offline
