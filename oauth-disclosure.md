---
layout: legal
title: OAuth Disclosure
---

# OAuth Permissions Disclosure

**Last Updated:** 2026-04-27

This page provides a plain-language explanation of every Google OAuth permission that **Verascribe Guardian** asks for during installation, exactly what each one allows, and why each one is necessary. It is designed to satisfy Google's OAuth verification requirements and to give you a single, scannable place to verify what the add-on can — and cannot — do with your Google account.

For full detail, see our [Privacy Policy](./privacy-policy.md) and [Terms of Service](./terms-of-service.md).

> **Note for Google OAuth reviewers:** This page is linked directly from the OAuth consent screen and is intended for your review. Each scope listed below corresponds to a declared scope in the add-on's `appsscript.json` manifest. Scopes are listed in the same order they appear in that manifest.

---

## Limited Use compliance

Verascribe Guardian's use of information received from Google APIs adheres to the **[Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy)**, including the **Limited Use** requirements.

In particular:
- We use your Google Workspace data **only to provide and improve user-facing features** of the Service that are visible and prominent in the user interface.
- We do **not** transfer Google Workspace data to others except as necessary to provide the Service, comply with applicable law, or as part of a merger or acquisition.
- We do **not** use Google Workspace data for **serving advertisements**.
- We do **not** allow humans to read your Google Workspace data unless (a) we have obtained your affirmative consent for specific messages, (b) it is necessary for security purposes (e.g., investigating abuse), (c) it is necessary to comply with applicable law, or (d) it is for internal operations and the data has been aggregated and anonymized.
- We do **not** use Google Workspace data to develop, improve, or train **generalized AI/ML models** of any kind.

---

## The permissions we request

| OAuth Scope | Plain-language summary | Why we need it |
|---|---|---|
| `userinfo.email` | See the email address on your Google Account | License registration, trial validation, support correspondence |
| `spreadsheets.currentonly` | View and edit **only the Sheet you have open** when you launch the add-on | Persist your custody log, schedule, and settings into hidden tabs in your own workbook |
| `drive.file` | Create and access **only files Verascribe Guardian creates** in your Drive (not your other files) | Store evidence attachments, generated PDF/CSV reports, and JSON backups in a Verascribe folder you own |
| `script.send_mail` | Send mail from your Gmail account | Email license-registration receipts to you and route "Contact Us" support messages |
| `script.external_request` | Make outbound HTTPS calls from the add-on's server code | Validate your license against `_registry.myverascribe.com` |
| `script.container.ui` | Show sidebars and dialogs in your Sheet | Render the Verascribe Guardian user interface |
| `script.scriptapp` | Internal Apps Script operations | Run the add-on's own server-side logic and triggers |

> **Note on the Verascribe Guardian Library (for Google reviewers):** The add-on depends on a shared Apps Script library (Library ID: `1jn6m2AA4sSvniiT-FC6j_QgDunt3o60REnVM5PE1ekvoulIISTxOFUM0`). The library runs *inside* the add-on project — it is not installed separately by users and does not present its own OAuth consent screen. The library's `appsscript.json` declares a subset of the scopes above; it omits `script.container.ui` because it never renders a sidebar or dialog. The scopes listed in this document correspond to the **add-on project's** manifest, which is the project users authorize at installation.

---

## What we **cannot** see

Because we use the **most restrictive** scopes Google offers for our needs, the add-on **cannot**:

- Read or modify any Google Sheet other than the one you have open with Verascribe Guardian running.
- Read, list, or modify any file in your Google Drive other than files Verascribe Guardian itself created.
- Read your Gmail inbox, drafts, or any message we did not send through the add-on.
- See your Google Calendar, Contacts, Photos, YouTube, Search history, or any other Google product data.
- Track you across the web, build advertising profiles, or share your data with advertisers or data brokers.

---

## Where your data actually lives

The Service is **offline-first**. The custody, financial, and evidence data you create stays in three places, all of which **you** own and control:

1. **Your browser's IndexedDB** — a working copy on your device for fast offline access.
2. **Your Google Sheet** — durable storage in hidden tabs of the workbook you installed the add-on into.
3. **Your Google Drive** — evidence attachments and exports in folders named "Verascribe Evidence" and "Verascribe - Archived Evidence (Standalone)".

The **only** outbound transmission to Verascribe-controlled infrastructure is a license-validation call. The add-on first contacts `_registry.myverascribe.com` — a DNS record owned by Nemerai, LLC — which redirects to a Google Apps Script web app at `https://script.google.com/macros/s/AKfycbzR…/exec`, also owned and operated by Nemerai, LLC. Both the routing domain and the Apps Script endpoint are Verascribe infrastructure. The payload contains only your email address, a workbook identifier, your license token, and a cryptographic signature — nothing else. See Section 5 of the Privacy Policy.

---

## How to revoke access

You can withdraw any of these permissions at any time:

1. Visit **[myaccount.google.com/permissions](https://myaccount.google.com/permissions)**.
2. Find **Verascribe Guardian** in the list.
3. Click **Remove Access**.

Revoking access will stop the add-on from functioning. It will **not** delete the data already stored in your own Google Sheet or Google Drive — those remain in your account until you delete them.

---

## Questions?

Email **myverascribe@gmail.com** and we will respond within a reasonable time, generally no more than 5 business days.
