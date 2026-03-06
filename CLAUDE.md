# CLAUDE.md — Call_Collection Repository Guide

This file provides context and conventions for AI assistants working with this repository.

---

## Repository Overview

**Call_Collection** is a data repository of customer service call transcripts. It contains **182 plain-text transcript files** covering customer calls from **November 2025 through February 2026**. There is no application code, build system, or test infrastructure — this is purely a structured data collection.

The calls appear to be from a company called **PreVeil**, a cybersecurity/compliance software provider (encrypted email and file storage), and document customer success, onboarding, and technical support conversations.

---

## Repository Structure

```
Call_Collection/
├── CLAUDE.md                                    ← This file
├── [Company Name] - [YYYY-MM-DD] - Customer Call Transcript.txt
├── [Company Name] - [YYYY-MM-DD] - Customer Call Transcript.txt
└── ... (182 .txt files total)
```

There are **no subdirectories**, no configuration files, no scripts, and no dependencies.

---

## File Naming Convention

All transcript files follow this exact pattern:

```
[Company Name] - [YYYY-MM-DD] - Customer Call Transcript.txt
```

**Examples:**
- `Asset Link Global - 2025-12-05 - Customer Call Transcript.txt`
- `Bluefin Innovations - 2025-12-12 - Customer Call Transcript.txt`
- `Critical Networking - 2026-01-08 - Customer Call Transcript.txt`

**Edge cases:**
- Some companies have multiple calls on different dates (e.g., `Calian - 2026-01-08` and `Calian - 2026-01-23`)
- One file uses a `_2` suffix for a duplicate date: `Custom Panel & Controls - 2026-01-16 - Customer Call Transcript_2.txt`

---

## Transcript File Format

Each transcript file has a consistent two-part structure:

### Header (first 4 lines)
```
Account: [Company Name]
Call Date: [YYYY-MM-DD]
Duration: [HH:MM:SS]
Participants: [Name1], [Name2], ...
```

### Body (after separator)
```
======================================================================

[Speaker Name]: [dialogue line]
[Speaker Name]: [dialogue line]
...
```

Speaker names in the body often include a company abbreviation suffix (e.g., `Jeremiah ALG:` for Asset Link Global).

---

## Content Domain

These transcripts document **PreVeil customer calls**, which typically cover:

- **Onboarding** — account setup, org creation, scheduling implementation meetings
- **Email gateway configuration** — subdomain setup, DNS/certificate requirements, routing
- **Compliance & CMS** — CMMC/CUI scoping questions, endpoint classification, VDI use
- **Cloud lock / data controls** — policies for preventing local file sync
- **Technical support** — troubleshooting access, permissions, device issues
- **Account management** — introductory calls, renewal discussions, feature walkthroughs

---

## Date Range

| Earliest call | Latest call |
|---------------|-------------|
| 2025-11-24    | 2026-02-16  |

The bulk of calls fall between December 2025 and February 2026.

---

## No Code, No Build System

This repository has **none** of the following:
- Programming language source files
- Package managers (`package.json`, `requirements.txt`, `Gemfile`, etc.)
- Build tools (`Makefile`, `webpack.config.js`, etc.)
- Test frameworks or test files
- Linting or formatting configuration
- Docker or CI/CD configuration
- Environment variable files

**Do not attempt to run, build, or test this repository** — there is nothing to execute.

---

## Git Configuration

- **Remote:** `http://local_proxy@127.0.0.1:46306/git/orleeberlove/Call_Collection`
- **Default branch:** `master`
- **Active feature branch:** `claude/claude-md-mmfej5sfiucw4wze-UQJaX`
- **Commit history:** 2 commits, both bulk uploads of transcript files

---

## Working with This Repository

### Adding new transcripts
New transcript files should follow the established naming convention exactly:
```
[Company Name] - [YYYY-MM-DD] - Customer Call Transcript.txt
```

If a company has a second call on the same date, append `_2` before `.txt`.

### Searching transcripts
Use `grep` or a text search tool to find transcripts by company, participant, topic, or date:
```bash
# Find all calls mentioning CMMC
grep -rl "CMMC" .

# Find all calls with a specific participant
grep -rl "Andrew Meggs" .

# Find calls within a date range (by filename)
ls *2026-01*.txt
```

### Analyzing content
When analyzing transcript content:
- The **header block** is reliable structured metadata
- The **body** is conversational and may contain transcription artifacts (repeated phrases, mid-sentence breaks)
- Speaker attribution uses the format `FirstName [CompanyAbbrev]:` in the body

---

## Conventions for AI Assistants

1. **Treat files as read-only data** unless explicitly asked to modify them.
2. **Do not create new transcript files** unless provided with actual call content.
3. **Respect participant privacy** — these are real customer conversations; avoid extracting or republishing personally identifiable information unnecessarily.
4. **Use filename metadata** (company, date) for quick lookups before reading full file content.
5. **Do not infer missing data** — if a transcript is ambiguous, note the ambiguity rather than guessing.
6. When asked to summarize or analyze calls, focus on the **business/technical content** of the conversation.
