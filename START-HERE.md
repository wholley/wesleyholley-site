# Wesley Holley — Portfolio Website

This is your complete website. It's a single, fast page styled to match your
2026 portfolio PDF, plus a built-in **visual editor** so you can change text and
swap images later without touching any code.

You'll do a one-time setup (about 30–45 minutes, mostly waiting). After that,
editing the site is as easy as logging into a web page and typing.

---

## How it works (the 30-second version)

- Your website files live in a free **GitHub** account (think of it as a folder in the cloud).
- **Netlify** (which you already have) watches that folder and publishes it to **wesleyholley.com**.
- The editor at **wesleyholley.com/admin** lets you change wording and images in your browser. When you click *Save*, it updates the folder, and Netlify republishes the site automatically — usually live within a minute.

You never need to open a code file again after setup.

---

## What's in this folder

| File / folder | What it is |
|---|---|
| `index.html` | The website itself. (Don't edit by hand — use the editor.) |
| `content.json` | All your words and image names. The editor writes to this for you. |
| `images/` | Your photo and all the project images. |
| `admin/` | The visual editor (`config.yml` + `index.html`). |
| `netlify.toml` | Tells Netlify how to publish. Leave it alone. |
| `START-HERE.md` | This guide. |

---

# Part 1 — One-time setup

### Step 1 — Put the files on GitHub

1. Create a free account at **github.com** (if you don't have one).
2. Click the **+** in the top-right → **New repository**.
3. Name it `wesleyholley-site`. Set it to **Public**. Click **Create repository**.
4. On the new repo page, click **“uploading an existing file.”**
5. Drag in **everything inside this folder** — `index.html`, `content.json`, `netlify.toml`, and the `images` and `admin` folders. Wait for them all to finish, then click **Commit changes**.

> Tip: make sure you upload the *contents* of this folder, not the folder itself. The `index.html` file should sit at the top level of the repo.

### Step 2 — Tell the editor which repo to use

1. In your new GitHub repo, open the `admin` folder, click `config.yml`, then click the **pencil ✏️** to edit.
2. Find this line near the top:
   ```
   repo: YOUR-GITHUB-USERNAME/wesleyholley-site
   ```
3. Replace `YOUR-GITHUB-USERNAME` with your actual GitHub username. For example, if your username is `wesholley`, it becomes:
   ```
   repo: wesholley/wesleyholley-site
   ```
4. Click **Commit changes**.

### Step 3 — Publish it with Netlify

1. Log into **netlify.com**.
2. **Add new site → Import an existing project → Deploy with GitHub.**
3. Authorize Netlify to see your GitHub, then pick the `wesleyholley-site` repo.
4. Leave all build settings blank/default and click **Deploy**.
5. After a few seconds you'll get a temporary address like `random-name-123.netlify.app`. Open it — your site is live! (Images and text should all show.)

### Step 4 — Connect your domain (wesleyholley.com)

**In Netlify:**
1. Open your site → **Domain management** (or *Domains*) → **Add a domain**.
2. Type `wesleyholley.com` and confirm it's yours.

**In Namecheap:**
1. Log in → **Domain List** → **Manage** next to wesleyholley.com → **Advanced DNS**.
2. Delete any existing default “parking” records, then add these two:

   | Type | Host | Value | TTL |
   |---|---|---|---|
   | A Record | `@` | `75.2.60.5` | Automatic |
   | CNAME Record | `www` | `your-site-name.netlify.app` | Automatic |

   *(Use the exact `something.netlify.app` name Netlify gave you for the CNAME value.)*
3. Save. DNS can take anywhere from a few minutes to a day to take effect. Netlify will automatically add a free HTTPS/SSL certificate once it sees the domain — no action needed.

### Step 5 — Turn on the editor login

This lets you sign in to the editor with your GitHub account (one click, forever).

**A. Create a GitHub OAuth app:**
1. GitHub → click your avatar → **Settings** → **Developer settings** (bottom of left menu) → **OAuth Apps** → **New OAuth App**.
2. Fill in:
   - **Application name:** `Wesley Holley Site Editor`
   - **Homepage URL:** `https://wesleyholley.com`
   - **Authorization callback URL:** `https://api.netlify.com/auth/done`  ← must be exactly this
3. Click **Register application**.
4. Copy the **Client ID**. Click **Generate a new client secret** and copy that too.

**B. Add them to Netlify:**
1. Netlify → your site → **Project configuration** → **Access & security** → **OAuth**.
2. Under **Authentication providers**, click **Install provider** → choose **GitHub**.
3. Paste the **Client ID** and **Client Secret**. Save.

Done. ✅

---

# Part 2 — Editing your site (the easy part)

1. Go to **wesleyholley.com/admin**
2. Click **Login with GitHub** and approve it.
3. You'll see your content grouped into sections: *Hero, About, Projects, Contact,* etc.
4. Click any section, change the text or swap an image, then click **Save** (and *Publish* if asked).
5. Wait about a minute and refresh **wesleyholley.com** — your change is live.

**To change an image:** click the image field, then **Upload** a new one from your computer. Use the same shape/orientation as the old one for best results.

**To add or remove a project:** open **Projects**, use the **＋** button to add one (title, description, image), or the trash icon to remove one. Drag them to reorder.

**Add your LinkedIn:** open the **Contact** section, paste your full LinkedIn profile URL into the *LinkedIn URL* box, and save. The button appears automatically. (Leave it blank to hide it.)

> You can also edit from your phone — the editor works on mobile.

---

## If something goes wrong

**The editor won't log in / “Login with GitHub” fails.**
Double-check Step 5: the callback URL must be exactly `https://api.netlify.com/auth/done`, and the Client ID/Secret must be pasted into Netlify under Access & security → OAuth.

*Quick fallback:* On the `/admin` login screen, click **“Sign in with Token”** instead. It links you to a GitHub page with the right settings pre-filled — generate the token, paste it back, and you're in. This works even if Step 5 isn't finished.

**My change didn't show up.**
Give it 1–2 minutes (Netlify is republishing), then hard-refresh the page (Cmd/Ctrl + Shift + R).

**The domain shows an error or “not secure” for a while.**
That's normal right after Step 4 — DNS and the SSL certificate can take up to a day. It resolves on its own.

**I want to change the green accent color or fonts.**
Those live near the top of `index.html` (the `--accent` color and the font links). Any developer can tweak them in two minutes — or just ask me.

---

## A note on the project images

Right now each project shows the matching page from your PDF as a single image, so
the site looks complete immediately. When you have higher-resolution or individual
shots of any project, just use the editor to upload a replacement — no other changes needed.
