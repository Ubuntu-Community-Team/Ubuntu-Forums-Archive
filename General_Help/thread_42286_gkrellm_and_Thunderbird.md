---
title: "gkrellm and Thunderbird"
date: 2005-06-16
forum: General Help
---

### Post by Digitallysick on 2005-06-16
Gkrellm says i have 5 emails, but i only have 3, it says my mail box is /var/mail , i want it to check for my thunderbird mail, how do i set this up?? (because right now its incorrect??)

---

### Post by intangible on 2005-06-17
By default gkrellm monitors your local account mbox (for system messages, stuff like that).

All you need to do is set it up to check for remote mail.
**Right-Click on the Mail Icon in gkrellm->Mailboxes tab->Check "Remote Mailbox"->Fill in your email information (like you put in Thunderbird)->Click "Add".**  You can also remove the local mailbox monitoring if you want.

---

