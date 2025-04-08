# n8n Auto-Updater via GitHub Actions

> Seamlessly update your **n8n Docker Compose instance** on a remote server using GitHub Actions — automatically or with a click. Perfect for devs, teams, and solo automators.

![Deploy Workflow](https://github.com/wmbalex/n8n-docker-updater/actions/workflows/deploy.yml/badge.svg)

![n8n logo](https://raw.githubusercontent.com/n8n-io/n8n/master/assets/n8n-logo.png)

---

## 🚀 What is this?

This is a **ready-to-use GitHub Actions workflow** that connects to your remote server via SSH and runs `docker compose pull && down && up -d` to update your self-hosted [n8n](https://github.com/n8n-io/n8n) instance.

- 🧠 **Smart**: no scripts to write
- 🖱️ **One-click**: run from GitHub UI
- 🔁 **Auto-update**: runs on push to `main` (or your preferred branch)
- 🔐 **Secure**: SSH key-based authentication

---

## ⚡ Quick Start for Everyone

> Just want it to work? Clone this repo and go:

```bash
git clone https://github.com/wmbalex/n8n-docker-updater.git
cd n8n-docker-updater
```

1. Go to GitHub ➔ **Create a new repo** (Public or Private)
2. Push this code to your own GitHub repo:

```bash
git remote set-url origin git@github.com:YOUR_USERNAME/n8n-docker-updater.git
git push -u origin main
```

3. Add **GitHub Secrets** (see below)
4. Hit "Run Workflow" → Done 🎉

---

## 🧪 Test the Updater

Once you've added the required GitHub secrets, head to the **Actions** tab and:

- Select the `Deploy n8n` workflow
- Click `Run workflow`
- Watch it update your n8n container in seconds! 🚀

---

## 📁 Repo Structure

```
n8n-docker-updater/
├── README.md
└── .github/
    └── workflows/
        └── deploy.yml
```

---

## 🛠 How It Works

1. GitHub Actions uses a **private SSH key** to connect to your server
2. It runs `docker compose` commands to update your n8n container
3. You trigger it **manually** or when pushing code/config changes to your repo

---

## 📦 Requirements

### On your **server**

- Docker & Docker Compose installed
- n8n running via Docker Compose (e.g. from [n8n-io/n8n/docker-compose](https://github.com/n8n-io/n8n/tree/master/docker/compose))
- Public SSH key added to `~/.ssh/authorized_keys`

### On your **GitHub repo**

- Use this repo or copy `.github/workflows/deploy.yml`
- Add your secrets (see next section)

---

## 🔐 Setup (One-Time)

### 1. Generate SSH key

On your local machine:

```bash
ssh-keygen -t ed25519 -C "github-actions-deploy" -f github_n8n_deploy_key
```

- Save the private key (for GitHub)
- Add the public key to your server: `~/.ssh/authorized_keys`

---

### 2. Add GitHub Repository Secrets

Go to your repo ➔ **Settings > Secrets and variables > Actions** ➔ Add these:

| Name              | Value                                                  |
| ----------------- | ------------------------------------------------------ |
| `N8N_SERVER_IP`   | Your server IP address (e.g. `123.123.12.12`)          |
| `N8N_SERVER_USER` | SSH user (e.g. `root` or `ubuntu`)                     |
| `N8N_DEPLOY_KEY`  | Contents of the **private SSH key** you just generated |

---

## ✅ How to Use

### Manual Trigger

1. Go to **Actions** tab
2. Select **Deploy n8n** workflow
3. Click **Run workflow**

### Automatic Trigger

- Push any commit to `main` (or configured branch)
- Workflow will run and update your n8n instance

---

## 🌐 Example: Docker Compose Folder Structure

If you followed [n8n's Docker guide](https://github.com/n8n-io/n8n/tree/master/docker/compose), your layout might look like:

```
/root/n8n/
├── docker-compose.yml
├── .env
└── data/
```

Make sure the workflow `cd`s into the correct folder (`/root/n8n` or wherever you host it).

---

## 💡 Tips

- ✅ Use a **dedicated SSH key** just for GitHub Actions
- ✅ Restrict the key to a non-root user with limited privileges
- 🛑 Never commit your private key
- 🕓 Add a cron trigger for scheduled auto-updates (optional)
- 🔔 Add Telegram/Slack notifications with a second step (advanced)

---

## 🔮 Planned Features

Here are a few cool future ideas you (or contributors) might develop:

- 📆 **Scheduled nightly updates** (cron job)
- 🔔 **Telegram/Slack/Webhook notifications** after update
- 💥 **Docker Compose fallback auto-recovery** if update fails
- ✅ **Workflow status badge** for GitHub README
- 🌐 **Multi-environment support** (dev/staging/prod)
- 📈 **Metrics log** to track uptime/deploys (e.g. with Google Sheets or InfluxDB)
- 🌙 **Dark/light themed logs** with output formatting

Have a feature idea? Open an [issue](https://github.com/wmbalex/n8n-docker-updater/issues) or submit a PR 🚀

---

## 🤝 Contributing

PRs welcome! This updater is a helpful companion to [n8n-io/n8n](https://github.com/n8n-io/n8n), not an official project.

---

## 🙏 Donate

If this saved you time or headaches, consider supporting the project 💖

→ [**Donate $10 in Crypto**](https://mytokensgate.com/pay.php?checkout_id=1)

Your support keeps open-source flowing 🙏

---

## 📜 License

[MIT](LICENSE)

---

Made with ❤️ by [@wmbalex](https://github.com/wmbalex)

