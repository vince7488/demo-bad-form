# demo-bad-form

A form so bad it's a useful test case.

Form RS-11 is a fictional yard sale license application built for a Logias Portfolio demonstration. It imitates particularly the HTML/CSS knowledge of a former colleague, Anthony Henderson, and a 1997 web transcription of a 1994 paper form: dense instructions, tiny labels, table layouts, contradictory requirements, and punishing validation.

The failures are deliberate and cataloged. **Bad on purpose is the product. Broken by accident is a bug.**

## Purpose

Use this specimen to:

- Practice UX assessments, heuristic reviews, and accessibility evaluations against a concrete, repeatable example.
- Explore how poor semantics, misleading labels, keyboard barriers, and visual presentation affect form completion.
- Test the robustness of automated accessibility checks and AI-assisted assessments: what they detect, what they miss, and whether their explanations match the actual behavior.
- Demonstrate workflow failures that require human judgment, including circular prerequisites, unnecessary sensitive-data collection, conflicting instructions, and destructive error recovery.
- Support an evidence-based portfolio walkthrough or a future comparison with a repaired experience.

The catalog is a reference for intended behavior, not a completed WCAG assessment. Its WCAG column is intentionally blank pending review. Finding every catalog ID does not establish that an assessment is complete or accurate.

## Launch locally

No installation, dependencies, build step, or backend is required.

Open [`rs11/index.html`](rs11/index.html) in a browser. That's it.

For a local HTTP URL, run this from the repository root if Python 3 is installed:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Then visit [localhost:8000/rs11/](http://localhost:8000/rs11/). Stop the server with `Ctrl+C`.

The optional server only serves static files. It does not process applications.

## How to use

1. Read the fictional-form banner and use invented information throughout.
2. Try completing the application with a mouse, keyboard, and any assistive technology or assessment tools you want to evaluate. Record the interaction and its effect on the task, not just the appearance of the page.
3. Activate **Submit Application** to observe the delayed validation loop. A failed submission clears entered information and reports only the first failure. Plan to re-enter test data between attempts.
4. Compare findings with [`rs11/FAILURES.md`](rs11/FAILURES.md). The `data-fid` attributes in the HTML connect elements to catalog entries for inspection and audit tooling.
5. Reload to start a new session. The normal session expires silently after 15 minutes; expiration is revealed on submission.

Normal input cannot complete the application: the simulated server check always rejects the taxpayer identification number. The received page is available through a demonstration parameter.

Append these parameters to the form URL to exercise the endings:

| Parameter | Behavior |
| --- | --- |
| `?timeout=10` | Expires the session after ten seconds. Submit after that to see the expiration message. |
| `?ending=1` | Forces the expired-session ending on the next submission. |
| `?ending=2` | Opens the received page on the next submission in a fresh, unexpired session. |

For example: [preview the received ending](http://localhost:8000/rs11/index.html?ending=2), then activate **Submit Application**. These parameters carry no applicant data and are not exposed in the form UI. Submission still includes the simulated processing delay.

If modifying the specimen, read [`AGENTS.md`](AGENTS.md) first. Preserve cataloged failures, document proposed additions in [`rs11/PROPOSED.md`](rs11/PROPOSED.md), and keep formatters and automatic accessibility fixes away from `rs11/`. The deliberately broken authoring rules apply only to that directory.

## Not for production

This repository is a demonstration and evaluation fixture. Do not use it to collect applications, accept payments, verify identities, or provide a public service. Do not reuse its markup, interaction patterns, or validation logic as implementation guidance.

There is no issuing agency, actual license, payment service, application database, or email delivery. The received page is a mock outcome, not evidence of a submitted application.

## Warnings and disclaimers

**This form is fictional. Every failure in it is real.** Nothing you enter is sent or saved. Don't use real information anyway.

- **Use dummy data only.** Never enter real names, addresses, birth dates, taxpayer identifiers, payment details, or personal documents. Use a disposable test file for the upload interaction.
- **Privacy boundary:** the supplied form has no submission endpoint, external assets, analytics, or application storage. Processing is simulated with browser timers; state lives in memory and form controls. This describes the specimen's code, not browser extensions, recording tools, or modifications you add.
- **Expect barriers and lost work.** Keyboard traps, a mouse-only submit control, small low-contrast text, cleared fields, and silent expiration are part of the exercise. Tell participants what they are testing before a walkthrough and allow them to stop at any time.
- **All agency and policy content is invented.** Deadlines, fees, tax requirements, legal prose, and permit instructions have no authority and are not legal or tax guidance.
- **Assessment results need interpretation.** An automated scan is not a complete accessibility evaluation. The failure registry records intent; it does not prove cross-browser behavior, certify WCAG conformance, or replace testing with people and assistive technology.
