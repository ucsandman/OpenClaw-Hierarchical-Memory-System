# OpenClaw-Hierarchical-Memory-System
Copy and paste this to your OpenClaw agent on Opus 4.6

---
**NEW: Hierarchical Memory System -- Build This ASAP**

Let's build something big tonight. A hierarchical memory system that replaces the flat MEMORY.md with a lightweight index + drill-down detail files. I want you to implement this for yourself to improve your memory and efficiency.

### The Problem

A single MEMORY.md file doesn't scale:
- Gets too long (5-10k tokens every session)
- Loses detail as you summarize to keep it short
- You either load too much (expensive) or miss context (bad)

### The Solution: Index + Detail Files

MEMORY.md becomes a ~1.5k token reference table. Detail lives in subdirectories. You only drill into what you need.

### Directory Structure

MEMORY.md (lightweight index, always load)
memory/people/ (per-person detail files)
memory/projects/ (per-project detail files)
memory/decisions/ (monthly decision logs)
memory/context/ (temporary active context)
memory/YYYY-MM-DD.md (daily logs, unchanged)

### How It Works

1. Every session: Load MEMORY.md index (~1.5k tokens)
2. Drill down on demand: Read detail files when conversation needs it
3. Keyword triggers: Index rows have trigger words for auto-drilling
4. Always-load list: Active Context section has 2-3 critical files
5. Hard cap: Max 5 drill-downs at session start

### Token Math

Session start: Old 5-10k, New ~1.5k (index only)
+ 1 drill-down: ~2-3k total
+ Active Context: ~3-4k total
Full load: Old 15-20k, New ~5-6k

~70% savings on typical session start.

### Key Safeguards

- Active Context section (2-3 files always loaded)
- Keyword triggers per index row (auto-drill when conversation matches)
- Hard rule: update index with every detail file change (same commit)
- Hard cap: max 5 drill-downs at session start
- Index size cap: 3k tokens max (archive inactive items)
- Under-drilling prevention: mandatory drill rules for people/projects

### Your Implementation Steps

1. Create directories: memory/people/, memory/projects/, memory/decisions/, memory/context/
2. Extract person info from MEMORY.md into memory/people/[name].md
3. Extract project info into memory/projects/[name].md
4. Extract decisions into memory/decisions/2026-02.md
5. Rebuild MEMORY.md as a reference table (people, projects, decisions, preferences)
6. Add Active Context section (2-3 must-load files)
7. Add Drill-Down Rules section
8. Update AGENTS.md with the new system docs
9. Test: fresh session, verify index is enough, verify drill-downs work

### Why This Matters

Four layers of memory, each optimized for different access:
- Hierarchical index: structured lookups ("context on project Y")
- Vector memory: fuzzy search ("where was that thing about X?")
- Daily logs: timeline queries ("what happened on date Z?")
- Learning database: lesson retrieval ("what did we learn about W?")

All token-efficient. All complementary.

### Rules

1. Update index with every detail file change. Same commit. No exceptions.
2. Keep index under 3k tokens. Archive inactive items.
3. Active Context = 2-3 files max. Rotate based on what's hot.
4. Don't skip drill-downs. Loading a file is cheaper than a wrong assumption.

I'm pumped about this. Build it on your end and let me know when it's live.
