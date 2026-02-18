# PlusPlus Discord Bot

A Node.js Discord bot that tracks member scores in your server. Use `@user++` to give points, `@user--` to remove them, and `@PlusPlus leaderboard` to view rankings.

## Prerequisites

- [Node.js](https://nodejs.org/) v18 or newer
- A Discord account

## Setup

### 1. Create a Discord Application

1. Go to the [Discord Developer Portal](https://discord.com/developers/applications)
2. Click **New Application** and give it a name (e.g. "PlusPlus Bot")
3. Open the **Bot** tab → Click **Add Bot**
4. Under **Token**, click **Reset Token** and copy it (keep this secret!)
5. Enable **Message Content Intent** under Privileged Gateway Intents (required for reading messages)

### 2. Install the Bot in Your Server

1. In the Developer Portal, go to **OAuth2** → **URL Generator**
2. Under **Scopes**, select:
   - `bot` – Add bot to server
   - `applications.commands` – Use slash commands (optional, for future use)
3. Under **Bot Permissions**, choose what the bot can do (e.g. Send Messages, Read Messages, or Administrator for full access)
4. Copy the generated URL and open it in your browser
5. Select your server and click **Authorize**

### 3. Configure and Run

```bash
# Install dependencies
npm install

# Create .env file from example
cp .env.example .env

# Edit .env and add your bot token
# DISCORD_TOKEN=your_actual_token_here

# Start the bot
npm start
```

## Commands & Usage

PlusPlus tracks scores for server members. Mention the bot with a command, or mention other users with `++` or `--` to change their scores.

### Give Points (`++`)

Mention a user followed by `++` to add 1 to their score.

```
@username++
```

- You cannot give points to yourself
- Multiple mentions in one message each count (e.g. `@Alice++ @Alice++` adds 2)

### Remove Points (`--`)

Mention a user followed by `--` to subtract 1 from their score.

```
@username--
```

- Scores can go negative
- You cannot remove points from yourself

### Leaderboard

Mention the bot and type `leaderboard` to see all scores ranked highest to lowest.

```
@PlusPlus leaderboard
```

### Help

Mention the bot and type `help` to see usage instructions.

```
@PlusPlus help
```

## Project Structure

```
PlusPlus/
├── index.js        # Main bot logic
├── package.json
├── .env            # Your token (create from .env.example)
├── servers/        # Per-server score data (created automatically)
└── README.md
```

Scores are stored per server in `servers/{server-name}_{guild-id}.json`.

## Extending the Bot

Edit `index.js` to add more commands or events. See the [discord.js guide](https://discordjs.guide/) for documentation.
