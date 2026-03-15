# Follow Builders, Not Influencers

An AI-powered digest that tracks the top builders in AI — researchers, founders, PMs,
and engineers who are actually building things — and delivers curated summaries of
what they're saying.

**Philosophy:** Follow people who build products and have original opinions, not
influencers who regurgitate information.

## What You Get

A daily or weekly digest delivered to your preferred messaging app (Telegram, Discord,
WhatsApp, etc.) with:

- Summaries of new podcast episodes from top AI podcasts
- Key posts and insights from 33 curated AI builders on X/Twitter
- Links to all original content
- Available in English, Chinese, or bilingual

## Quick Start

1. Install the skill in your agent (OpenClaw or Claude Code)
2. Say "set up follow builders" or invoke `/follow-builders`
3. The agent walks you through setup conversationally — no config files to edit

The agent will ask you:
- How often you want your digest (daily or weekly) and what time
- What language you prefer
- Then guide you through getting one free API key (takes ~1 minute)

That's it. Your first digest arrives immediately after setup.

## Changing Settings

Everything is configurable through conversation. Just tell your agent:

- "Add @username to my follow list"
- "Remove Lenny's Podcast"
- "Switch to weekly digests on Monday mornings"
- "Change language to Chinese"
- "Make the summaries shorter"
- "Show me my current settings"

No files to edit, no commands to remember.

## Customizing the Summaries

The skill uses plain-English prompt files to control how content is summarized.
You can customize them two ways:

**Through conversation (recommended):**
Tell your agent what you want — "Make summaries more concise," "Focus on actionable
insights," "Use a more casual tone." The agent updates the prompts for you.

**Direct editing (power users):**
Edit the files in the `prompts/` folder:
- `summarize-podcast.md` — how podcast episodes are summarized
- `summarize-tweets.md` — how X/Twitter posts are summarized
- `digest-intro.md` — the overall digest format and tone
- `translate.md` — how English content is translated to Chinese

These are plain English instructions, not code. Changes take effect on the next digest.

## Default Sources

### Podcasts (5)
- [Latent Space](https://www.youtube.com/@LatentSpacePod)
- [Training Data](https://www.youtube.com/playlist?list=PLOhHNjZItNnMm5tdW61JpnyxeYH5NDDx8)
- [Lenny's Podcast](https://www.youtube.com/@LennysPodcast)
- [No Priors](https://www.youtube.com/@NoPriorsPodcast)
- [Unsupervised Learning](https://www.youtube.com/@RedpointAI)

### AI Builders on X (33)
[Andrej Karpathy](https://x.com/karpathy), [Swyx](https://x.com/swyx), [Greg Isenberg](https://x.com/gregisenberg), [Lenny Rachitsky](https://x.com/lennysan), [Josh Woodward](https://x.com/joshwoodward), [Kevin Weil](https://x.com/kevinweil), [Peter Yang](https://x.com/petergyang), [Nan Yu](https://x.com/thenanyu), [Madhu Guru](https://x.com/realmadhuguru), [Mckay Wrigley](https://x.com/mckaywrigley), [Steven Johnson](https://x.com/stevenbjohnson), [Amanda Askell](https://x.com/AmandaAskell), [Cat Wu](https://x.com/_catwu), [Thariq](https://x.com/trq212), [Google Labs](https://x.com/GoogleLabs), [Raiza Martin](https://x.com/raizamrtn), [Amjad Masad](https://x.com/amasad), [Guillermo Rauch](https://x.com/rauchg), [Riley Brown](https://x.com/rileybrown), [Alex Albert](https://x.com/alexalbert__), [Hamel Husain](https://x.com/HamelHusain), [Aaron Levie](https://x.com/levie), [Ryo Lu](https://x.com/ryolu_), [Garry Tan](https://x.com/garrytan), [Lulu Cheng Meservey](https://x.com/lulumeservey), [Justine Moore](https://x.com/venturetwins), [Matt Turck](https://x.com/mattturck), [PJ Ace](https://x.com/PJaccetturo), [Zara Zhang](https://x.com/zarazhangrui), [Nikunj Kothari](https://x.com/nikunj), [Peter Steinberger](https://x.com/steipete), [Dan Shipper](https://x.com/danshipper), [Aditya Agarwal](https://x.com/adityaag)

## Installation

### OpenClaw
```bash
# From ClawhHub (coming soon)
clawhub install follow-builders

# Or manually
git clone https://github.com/zarazhangrui/follow-builders.git ~/skills/follow-builders
cd ~/skills/follow-builders/scripts && npm install
```

### Claude Code
```bash
git clone https://github.com/zarazhangrui/follow-builders.git ~/.claude/skills/follow-builders
cd ~/.claude/skills/follow-builders/scripts && npm install
```

## Requirements

- Node.js (v18+)
- Supadata API key (free tier — [sign up](https://supadata.ai))

That's it. X/Twitter posts are fetched for free using Rettiwt-API in guest mode —
no API key, no login, no risk to your account.

## How It Works

1. A scheduled cron job triggers the skill at your chosen time
2. A Node.js script fetches new content:
   - YouTube podcast transcripts via Supadata API
   - X/Twitter posts via Rettiwt-API (guest mode — no login needed)
3. The AI agent remixes the raw content into a digestible summary
4. The digest is delivered to your messaging app

See [examples/sample-digest.md](examples/sample-digest.md) for what the output looks like.

## Privacy

- Your API key is stored locally in `~/.follow-builders/.env` — only sent to Supadata
  for YouTube transcripts. X/Twitter data is fetched without any API key.
- The skill only reads public content (public YouTube videos, public X posts)
- Your configuration and reading history stay on your machine

## License

MIT
