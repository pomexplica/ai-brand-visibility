# AI Brand Visibility Tracker - ChatGPT, Claude & Perplexity

People now ask AI assistants "what is the best X?" instead of Googling. This Actor asks the AIs **the same questions your buyers ask**, with live web search turned on, and tells you **if your brand shows up, in what position, which competitors are recommended instead, and which web pages the AI used as sources.**

**[Run it on Apify](https://apify.com/pomlabs/ai-brand-visibility?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)**: no install, no login, free credit on a new Apify account.

## What you get

**For each question and each AI**
- The full answer, as a user would read it
- `brandMentioned`, `brandMentions` and `brandFirstMentionChar` (where in the answer your brand first appears)
- `brandRankAmongTracked`: your position among you and your competitors, by order of first mention (1 = mentioned first)
- `competitorsMentioned`: which tracked competitors appeared and how many times
- `citedSources`: the URLs the AI cited in its answer
- `searchResults`: all pages the AI found while searching (useful to see which sites feed the AI)
- `brandDomainCited`: whether a page from your own site was among them
- Date and time of the check, engine and model used

## Pricing

**No API key needed for Claude. You pay only for answers delivered: $0.03 per question per AI.** Failed questions are listed with the reason and never charged.

That is the free-plan price; Apify paid plans (Bronze, Silver, Gold) pay less per item.

## Call it by API

```bash
curl -X POST "https://api.apify.com/v2/acts/pomlabs~ai-brand-visibility/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"prompts": ["What is the best CRM for a small business?", "HubSpot vs Pipedrive, which one should I choose?"], "brand": "HubSpot", "brandDomain": "hubspot.com", "competitors": ["Salesforce", "Pipedrive", "Zoho"]}'
```

Python:

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("pomlabs/ai-brand-visibility").call(run_input={"prompts": ["What is the best CRM for a small business?", "HubSpot vs Pipedrive, which one should I choose?"], "brand": "HubSpot", "brandDomain": "hubspot.com", "competitors": ["Salesforce", "Pipedrive", "Zoho"]})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Use it from Claude, Cursor or any MCP client

```bash
claude mcp add ai-brand-visibility "https://mcp.apify.com?tools=pomlabs/ai-brand-visibility" -t http
```

## More Actors by Pom Labs

- [YouTube Transcript Scraper: Translate, No Login · $3/1K](https://apify.com/pomlabs/youtube-transcript-scraper?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [Instagram Transcript Scraper: Reels, TikTok, Facebook, Hook](https://apify.com/pomlabs/social-video-transcript?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [Reddit Scraper: Deleted & Removed, Mods, Hidden Profiles](https://apify.com/pomlabs/reddit-posts-comments-scraper?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [LinkedIn Company Scraper (No Cookies): Posts, Similar Companies](https://apify.com/pomlabs/linkedin-company-scraper?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [YouTube Comments Scraper + Replies, Shorts · No API Key · $1/1K](https://apify.com/pomlabs/youtube-comments-scraper?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [Instagram Profile Scraper: Exact Followers, Reels Views](https://apify.com/pomlabs/instagram-profile-data?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [LinkedIn Profile Scraper (No Cookies) + Similar Profiles](https://apify.com/pomlabs/linkedin-profile-scraper?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [Threads Scraper: Keyword Search, Posts & Profiles · No Login](https://apify.com/pomlabs/threads-scraper?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [AliExpress Scraper: Exact Units Sold, Prices, Search · $1/1K](https://apify.com/pomlabs/aliexpress-scraper?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [Mercado Livre & Amazon BR Coupon Code Checker](https://apify.com/pomlabs/mercadolivre-coupon-checker?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [Page Time Machine · Wayback Diff + AI · No Login · $2.5/1K](https://apify.com/pomlabs/page-time-machine?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [Video Downloader: TikTok No Watermark, Instagram, YouTube, X](https://apify.com/pomlabs/video-downloader?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [NSFW Image Detector & Image Tagger - Moderation + Categories](https://apify.com/pomlabs/image-moderation-tagger?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)
- [Google Trends Scraper: Related Queries, No 429 · $2/1K](https://apify.com/pomlabs/google-trends-scraper?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility)

Full documentation, input fields and output format: [AI Brand Visibility Tracker - ChatGPT, Claude & Perplexity on Apify](https://apify.com/pomlabs/ai-brand-visibility?utm_source=github&utm_medium=readme&utm_campaign=ai-brand-visibility).
