# Ruben Gagliardi — full-stack engineer

I build products end to end: **TypeScript / Angular / React** on the front, **C# / .NET and SQL** on the back,
and AI-assisted development as a daily tool rather than a demo. Eight years of shipping, most of them running
technology for a business I also ran.

> **About the code.** The projects below are real, working software. Their source stays **private**: I am
> advertising what I can do, not giving away the implementations. Read the description, look at the screens,
> ask me anything — I am glad to walk through the design and the decisions in a call.

---

## 1. Slot engine — booking without double bookings

**What it is.** An API and dashboard for booking time slots on shared resources (arenas, rooms, coaches):
opening hours, capacity, half-open intervals, cancellations that keep history.

**The interesting part is not the CRUD.** It is the invariant: *two people asking for the same slot at the
same moment must not both get it.* Exactly one request wins, the other gets a `409` with a reason.

**Stack.** ASP.NET Core minimal API · EF Core + SQLite · xUnit · Angular
**Evidence.** 19 automated tests — 12 on the domain rules, 7 through HTTP, including the concurrency one.

**What was hard.** Half-open intervals are easy to get wrong (`11:00-12:00` does not overlap `10:00-11:00`),
and the naive check-then-insert is a race. I serialise the booking per resource and I write down where that
stops being enough (a second instance needs the database constraint, not the lock).

<!-- screenshot: availability grid -->
<!-- screenshot: 409 conflict with a readable reason -->

---

## 2. Operations automation — the tools I actually use

**What it is.** A set of small tools that run my own operations: browser automation over the **Chrome DevTools
Protocol**, mailbox archiving with **SHA-256 manifests** for every moved file, a tab registry that only ever
closes the tabs it opened itself.

**Why it is worth showing.** Everyone says "I use AI". The engineering is the part around it: idempotent
scripts, hashes to prove a file was not altered, written safety rules before the first click, and a rule that
says *never* instead of *usually*.

**Stack.** Node.js · CDP · Gmail API · file integrity checks

<!-- screenshot: archive manifest with hashes -->
<!-- screenshot: the tab registry -->

---

## 3. KDP publishing pipeline

**What it is.** The publishing side of a small editorial business: EPUB preparation, cover pipeline, metadata,
and the checks that stop a book from being published with the wrong data.

**Stack.** Python · EPUB/PDF tooling · browser automation · checklists as code

<!-- screenshot: pipeline report -->

---

## How I work

- **Rules before code.** Intervals, uniqueness, capacity: written as tests before they are written as endpoints.
- **Small surface.** Minimal APIs, one error contract, no layer for the sake of a layer.
- **Boring operations.** Seeded fake data, reproducible runs, hashes instead of trust.
- **Limits written down.** Every design note says where the solution stops working.

## Currently

Looking for a **remote senior full-stack** role. TypeScript/Angular/React with a .NET and SQL backbone.

- LinkedIn: <!-- TODO -->
- The full CV is available on request.
