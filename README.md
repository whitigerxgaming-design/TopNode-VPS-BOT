<div align="center">

# 🌟 TOP NODE VPS Bot

**A fully automated Discord bot for creating and managing LXC/LXD VPS containers.**

Made by **WHITIGER** for **TOP NODE**

</div>

---

## ✨ Features

- Create, delete, resize, suspend and reinstall VPS containers from Discord
- Port forwarding and SSH access for every VPS
- Multi-node support
- Admin and main-admin controls
- Runs 24/7 as a systemd service

## 📋 Requirements

- A fresh **Ubuntu** or **Debian** VPS/server with **root** access (KVM or dedicated recommended)
- A Discord Bot Token from the [Discord Developer Portal](https://discord.com/developers/applications)
- Your Discord User ID

> In the Developer Portal → **Bot** tab, enable all three **Privileged Gateway Intents** (Presence, Server Members, Message Content).

## 🚀 Installation

Run these commands as **root** on your VPS:

```bash
apt update && apt install git -y
git clone https://github.com/whitigerxgaming-design/TopNode-VPS-BOT.git
cd TopNode-VPS-BOT
chmod +x install.sh
sudo ./install.sh
```

Then follow the prompts:

1. Choose your OS (`1` Ubuntu / `2` Debian)
2. Enter your **Discord Bot Token**
3. Enter your **Main Admin Discord ID**

The installer sets up LXD, Python, the bot and a `bot` systemd service automatically.

## 🛠️ Managing the Bot

| Action | Command |
|---|---|
| Check status | `systemctl status bot` |
| Live logs | `journalctl -u bot -f` |
| Restart | `sudo systemctl restart bot` |
| Stop | `sudo systemctl stop bot` |
| Disable autostart | `sudo systemctl disable bot` |

## ⚙️ Configuration

Settings live in `/etc/systemd/system/bot.service`. After editing, apply with:

```bash
sudo systemctl daemon-reload
sudo systemctl restart bot
```

| Variable | Description | Default |
|---|---|---|
| `DISCORD_TOKEN` | Your bot token | required |
| `MAIN_ADMIN_ID` | Main admin Discord ID(s), comma-separated | required |
| `BOT_NAME` | Name shown in embeds | `TOP NODE` |
| `LOGO_URL` | Logo used in embed thumbnail/footer | TOP NODE logo (this repo) |
| `PREFIX` | Command prefix | `!` |
| `VPS_USER_ROLE_ID` | Role given to VPS owners | auto-created |
| `DEFAULT_STORAGE_POOL` | LXD storage pool | `default` |

## 👑 Admin Commands

- `!admin-add @user` / `!admin-remove @user` — manage admins (main admin only)
- `!add-admin <user_id>` / `!rm-admin <user_id>` — manage main admins by ID
- `!admin-list` — list all admins

Run `!help` in Discord to see every command.

## 📝 Notes

- The bot runs as **root** because it manages LXC containers. Keep your token and server secured.
- `vps.db` (SQLite) is created in `/root` on first run.

---

<div align="center">Made with ❤️ by <b>WHITIGER</b> for <b>TOP NODE</b></div>
