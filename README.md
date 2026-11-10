# Fantasy Live (starter)

A live fantasy football web app you can add to your iPhone home screen. No App Store needed.

## What it does
- **Games tab:** every game this week with live scores. Tap a game to see each player's fantasy points.
- **My Team tab:** tap **+** next to any player to add them, and your live team total shows here.
- **Settings:** switch between PPR, Half PPR, and Standard scoring, look at past weeks, and add your proxy URL.
- Refreshes every 60 seconds while it's open.

## Files
| File | What it is |
|---|---|
| `index.html` | The whole app |
| `manifest.json` | Name, icon, and full screen mode for the home screen |
| `sw.js` | Caches the app so it opens fast |
| `icon-*.png`, `apple-touch-icon.png` | App icons |
| `worker.js` | Optional Cloudflare proxy (see step 3) |

## 1. Put it online (free, about 5 minutes)
1. Make a free GitHub account, then create a new **public** repo named `fantasy-live`.
2. Click **Add file > Upload files** and upload everything except `worker.js` and this README.
3. Go to **Settings > Pages**, set Source to **Deploy from a branch**, pick `main` and `/ (root)`, and save.
4. After a minute, your site is live at `https://YOUR-USERNAME.github.io/fantasy-live/`.

## 2. Add it to your home screen
Open the link in **Safari**, tap **Share**, then **Add to Home Screen**.

## 3. If the Games tab says it can't reach the data source
Some browsers block ESPN requests that come straight from a web page. The fix is the free proxy:
1. Make a free Cloudflare account and go to **Workers & Pages > Create > Create Worker**.
2. Replace the starter code with everything in `worker.js` and click **Deploy**.
3. Copy the worker URL (something like `https://fantasy-live.yourname.workers.dev`).
4. In the app, go to **Settings**, paste it into **Proxy URL**, and save.

The proxy also caches data, so ESPN only gets hit about twice a minute total, even if your whole league uses the app.

## Testing before game day
Go to Settings and pick last week to see real, finished games. Add a few players and check that the totals match ESPN.

## Updating the app
After changing `index.html`, change `VERSION` in `sw.js` (for example `v1` to `v2`) and upload both files. Phones will pick up the new version the next time the app is opened.

## Next steps
- Pull your real ESPN league rosters through the proxy's `/league` route. Add your `LEAGUE_ID`, `ESPN_S2`, and `SWID` cookies as Worker secrets.
- Add D/ST scoring and bonus rules.
- Head to head matchup view.

Note: ESPN's endpoints are unofficial, so they can change without warning. That's fine for a personal app, but don't charge money for it.
