# Icebreaker Name Game

A single-page, no-install web app for running a "guess everyone's name" icebreaker at a conference or meetup.

## How it works

1. **Setup tab** — Preload the roster of everyone in the session: Name, Designation, Region. Add rows one at a time, or paste a CSV block (`Name, Designation, Region` per line) and click **Import rows**. Also add the teams/players who will be doing the guessing.
2. Click **Start / Restart Queue** — this shuffles all participants into a random order for the guessing round.
3. **Play tab** — For the current participant, the app shows their Designation and Region as the clue (their name stays hidden). A player calls out their guess out loud; the host clicks **🎤 Start Listening**, which uses the browser's built-in speech recognition to transcribe the guess.
4. The app fuzzy-matches the transcript against the person's Name, Designation, and Region **separately**, and shows a ✓/✗ per field — one point per field guessed correctly. The host picks which team gets the points and clicks **Award points**.
   - If voice recognition is unavailable or mishears something, there's a manual text box to type the guess instead — it runs through the same scoring logic.
5. Click **Reveal name** to show the audience who it was, then **Next person →** to continue.
6. **Results tab** shows the final leaderboard and full history, and can **Export CSV** for a record of the session.

## Running it

No build step, no server, no dependencies. Just open `index.html` in Chrome or Edge (voice recognition needs one of those — Safari/Firefox can still be used with the manual typed-guess fallback). For convenience at a venue:

- Open the file directly on the laptop that's running the session, **or**
- Enable GitHub Pages for this repo (Settings → Pages → deploy from this branch) and open the hosted URL on any device.

All data (roster, teams, scores, history) is kept in the browser's local storage, so a refresh won't lose progress — but it's specific to that one browser/device, so run the whole game from a single laptop/tablet.

## Notes

- Speech recognition (Web Speech API) requires an internet connection and microphone permission; it does not send any of your roster data anywhere — only the mic audio goes to the browser's speech-to-text service.
- Names/designations with unusual spellings may need the manual-typed-guess fallback for more reliable scoring.
