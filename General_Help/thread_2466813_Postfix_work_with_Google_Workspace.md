---
title: "Postfix work with Google Workspace"
date: 2021-09-06
forum: General Help
---

### Post by kladizkov on 2021-09-06
We use postfix mail server to receive all mails of example.com. We have around 60 mail users. We are planning to give 2 email users with Google Workspace, so they can receive and send from Google Workspace.

For example,

[EMAIL="rob@example.com"]rob@example.com[/EMAIL] and [EMAIL="bob@example.com"]bob@example.com[/EMAIL] are Google Workspace users. They need to send/receive mails using Google Workspace.
[EMAIL="sandra@example.com"]sandra@example.com[/EMAIL] and our other 50+ users use our legacy postfix system.

We do not want to make any changes to MX records. So mails of rob and bob have to be received first by Postfix, then routed to Google. What sort of changes have to be made in Postfix in order to make this work?

---

### Post by kladizkov on 2021-09-08
Bump

---

