# Daymark

Daymark is a small habit tracker that runs on your own computer. You add the routines you care about, decide when they happen, and tick them off as you go. Over time it shows you how consistent you've been.

There's no account and no cloud. Everything is saved in a SQLite file inside the project folder, so your data stays with you.

![Daymark Today page](docs/screenshots/today.png)

## Why I built it

Most habit apps want you to sign up, sync, and pay. I wanted something simple that lives on my machine, keeps a real history, and gets out of the way.

## Features

- **Habits your way.** Give each habit a name, icon, color, category, and a goal per check-in (for example, 8 glasses of water).
- **Flexible schedules.** Daily, weekly, or monthly. Pick specific weekdays or dates, and set a start date and an optional end.
- **Today page.** See what's due, check things off, or log progress step by step. You can also look back at past days.
- **Library.** Search and filter your habits, edit them, or archive the ones you're pausing without losing their history.
- **Stats.** Completion rate, streaks, a trend chart, a habit leaderboard, and a year-long activity grid.
- **Settings.** Dark mode, week start day, browser reminders, categories, and your display name.
- **Backups.** Export to JSON, import it back, or create and restore full SQLite backups.

![Daymark Stats page](docs/screenshots/stats.png)

## Built with

- React 19 and TypeScript
- Vite
- Tailwind CSS v4
- Node.js with its built-in SQLite support

## Getting started

You'll need **Node.js 22.13 or newer**. No separate database is required.

```sh
npm install
npm run dev
```

Then open [http://127.0.0.1:3100](http://127.0.0.1:3100). Press `Ctrl+C` in the terminal to stop it.

To run a production build instead:

```sh
npm run build
npm start
```

This one runs at [http://127.0.0.1:3000](http://127.0.0.1:3000).

## Useful commands

| Command | What it does |
| --- | --- |
| `npm run dev` | Starts the app and the local data API |
| `npm run build` | Type-checks and builds for production |
| `npm start` | Runs the production build |
| `npm test` | Runs the tests |
| `npm run verify` | Type checks, tests, and build in one go |

If a port is busy, pick another one:

```sh
PORT=3200 API_PORT=3201 npm run dev
```

## Your data

Daymark creates its database the first time it runs:

```text
data/database.sqlite    your habits, history, and settings
data/backups/           backups made from Settings
```

To move Daymark to another computer, stop the app, copy the whole project folder (including `data/`), run `npm install`, and start it again.

The files aren't encrypted, so treat them like any other personal files. Keep a copy of important backups somewhere outside the project folder too.

## Project structure

```text
server/   Node.js API and SQLite database
shared/   Schedule logic used by both the app and server
src/      React app and styles
tests/    Schedule, database, and API tests
public/   Static files
```

## Troubleshooting

- **Port already in use?** Set a different `PORT` as shown above.
- **Production app says the build is missing?** Run `npm run build` first.
- **No reminder showing up?** Check that notifications are allowed in your browser and that reminders are on in Settings. Reminders only fire while Daymark is open.
