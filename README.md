# Dad's Birthday Tickets — setup

The whole website is one file, `index.html`. Tickets are stored in a free
Firebase Realtime Database, so the count is the same on every device.

Until you finish step 2, the page runs in **demo mode**: it works, but tickets
are saved only in the browser you're using.

## 1. Create the database (about 5 minutes)

1. Go to <https://console.firebase.google.com> and sign in with a Google account.
2. Click **Create a project**, name it (e.g. `dad-tickets`). Google Analytics is not needed.
3. In the left menu open **Build → Realtime Database** → **Create Database**.
   Pick a location near you, then choose **Start in locked mode**.
4. Open the **Rules** tab, replace everything with the contents of
   `database.rules.json` from this folder, and click **Publish**.

## 2. Connect the page

1. In Firebase click the gear icon → **Project settings**.
2. Under **Your apps**, click the **</>** (Web) icon, give it any nickname, and
   click **Register app**. (Firebase Hosting is not needed.)
3. Firebase shows a `firebaseConfig = { ... }` block. Copy the values.
4. Open `index.html` in a text editor and find `const FIREBASE_CONFIG` near the
   bottom. Replace the placeholder values with yours. Make sure `databaseURL`
   is there; if Firebase didn't show it, copy it from the top of the Realtime
   Database page (it looks like `https://dad-tickets-default-rtdb.firebaseio.com`).
5. Just below, change `ADD_PASSCODE` from `"1234"` to your own code.

These Firebase values are meant to be public, so it's fine that they sit in the
web page.

## 3. Put it online (pick one)

**Netlify Drop (easiest, no Git):**
go to <https://app.netlify.com/drop>, sign up, and drag this whole folder onto
the page. You get a link like `https://something.netlify.app`; you can rename it
under **Site configuration → Change site name**.

**GitHub Pages:**
create a public repository, upload `index.html`, then go to
**Settings → Pages → Deploy from a branch → main / root**. The link is
`https://<your-username>.github.io/<repo-name>/`.

## Using it

- **Redeem:** tap a ticket once (it turns white), then tap again.
- **Add:** tap the **+** in the bottom-right corner. The first time on each
  device it asks for your passcode, then remembers it.

## Good to know

- Anyone with the link can redeem tickets. The passcode only stops casual
  visitors from *adding* them; someone technical could still get around it.
  For a family gift that's usually fine.
- To reset everything, open the Realtime Database page in Firebase and delete
  the `tickets` entry.
