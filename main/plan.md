# Lost in the Inbox — Capstone Plan

## The problem
Academic emails (from professors, university offices, coursework) get buried in an inbox that's mostly promotional mail, newsletters, and routine notifications. On top of that, a good chunk of the remaining email is repetitive and low-effort to answer — confirmations, RSVPs, acknowledgements — but still takes real time to open, read, and reply to one by one.

## The idea
"Lost in the Inbox" is an idea where an agent sits in front of an inbox and does three things:
1. **Filters for what matters.** It classifies incoming mail so academic/university communication surfaces immediately, instead of competing with everything else for attention.
2. **Summarizes the rest.** Non-academic mail gets condensed into a short digest instead of sitting in the inbox as dozens of unread messages.
3. **Drafts the boring replies.** For clearly routine messages (confirmations, RSVPs, simple acknowledgements), it writes a draft reply and asks for one-click approval instead of requiring a reply to be composed from scratch.

## MVP (what I'm building first)
- Connect to one inbox ([Gmail API / Outlook API — pick whichever you're using]).
- Classify each incoming email as *academic* or *not academic* using an LLM prompt over sender, subject, and body.
- Route academic mail to the main view; move everything else into a separate digest view/label.
- Generate one short daily-digest summary of the non-academic mail.
- Detect routine, templated emails (confirmations, RSVPs, acknowledgements) and generate a draft reply that I approve or edit before it sends — nothing sends automatically.

## Stretch goals (if there's time)
- Learn from which drafts I approve vs. edit, to improve future drafts.
- Priority scoring inside "academic" mail (e.g. flag anything deadline-sensitive).
- A small dashboard showing how much got triaged / how much time it saved.
- Calendar-aware replies (e.g. suggesting meeting times when a professor asks to schedule one).

## How AI will be used, and why
- **Classification** — an LLM reads each email's sender, subject, and body and decides whether it's academic or not. This isn't a keyword filter: the same sender can send both academic and non-academic mail, so the signal is in the content, not just metadata, which needs contextual understanding rather than fixed rules.
- **Summarization** — an LLM condenses a batch of non-academic emails into a short digest, so I get the gist without opening each one.
- **Reply drafting** — an LLM drafts a reply to routine messages in a normal, polite tone matching the original message. I stay in the loop: every draft is approved or edited before sending, nothing goes out automatically.
- **Why AI specifically** — inbox content is unstructured and highly variable; the same judgment call ("is this urgent," "is this routine") can't be solved with fixed rules across different senders and phrasing. Classification, summarization, and natural-language generation are exactly the tasks LLMs are suited for.
