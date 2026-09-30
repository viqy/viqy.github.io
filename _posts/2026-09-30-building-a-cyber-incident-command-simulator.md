---
title: "Building a Cyber Incident Command Simulator"
date: 2026-09-30 17:30:00 +0800
categories: [Cybersecurity, Security Engineering]
tags: [incident-response, python, fastapi, sqlite, detection-engineering]
---

# Building a Cyber Incident Command Simulator

I am building a defensive web-based **Cyber Incident Command Simulator** to model the workflow of a security team responding to a synthetic incident.

The project follows a simple operational flow:

`Attack → Logs → Detection → Investigation → Decision → Response → Incident Report`

## Why I built it

Instead of creating a project that only demonstrates individual security tools, I wanted to model the workflow that connects security events to investigation and response decisions.

The initial scenario is a synthetic credential-compromise chain involving:

- Authentication activity
- PowerShell execution
- Encoded PowerShell
- Suspicious DNS activity
- Internal SMB activity
- Large outbound data transfer

## Architecture

The application is intentionally simple:

`Scenario Generator → Detection Engine → Correlation Engine → FastAPI → Command Center UI → Investigation → Report`

The backend is written in Python using FastAPI. SQLite stores investigation state so findings and response actions survive application restarts.

## Investigation workflow

The simulator supports an investigation lifecycle that moves from detection through triage, investigation, containment, eradication, recovery, and closure.

Analysts can record:

- Findings
- Investigation status
- Response actions
- Analyst identity
- Target and reason for each response action

## Reporting

The simulator generates an incident report containing the incident summary, attack assessment, event and detection counts, attack stages, investigation findings, and response actions.

Reports can also be exported as standalone HTML.

## Testing

The project currently has an automated test suite covering the simulator, detection, correlation, investigation, persistence, and reporting functionality.

## Source code

The project is open on GitHub:

[Cyber Incident Command Simulator](https://github.com/viqy/cyber-incident-command-simulator)

I will continue documenting the architecture and new capabilities as the simulator develops.
