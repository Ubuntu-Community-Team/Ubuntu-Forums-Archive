---
title: "Thunderbird not storing sent messages in Sent folder."
date: 2015-09-08
forum: General Help
---

### Post by donsy on 2015-09-08
[FONT=Sans]Whenever I send a message from Thunderbird it doesn't appear in the Sent folder. I've tried every combination of settings in Account Settings > Copies & Folders, and still a sent message doesn't appear in the Sent folder. Any suggestions on what to try next would be greatly appreciated. (Version 38.2.0)[/FONT]

---

### Post by SeijiSensei on 2015-09-08
Are you using IMAP?  Are the sent messages supposed to be placed in a folder in the IMAP tree or stored in "Local Folders"?

---

### Post by donsy on 2015-09-08
Yes I'm using IMAP and the Sent folder in the IMAP tree. The only local folders are Outbox and Trash. Sometimes messages do show up in the Sent folder but only after a very long delay of more than an hour. And that's only some of the messages, not all.

---

### Post by donsy on 2015-09-08
The problem is that messages don't show up in the Sent folder until after logging off and logging back on. I didn't realize this until just now. Doh! I was expecting the Sent folder behavior to be the same as with Drafts and Trash, but no. I don't know why this delayed behavior but I can live with it for now. Obviously I'm new with Thunderbird.

---

### Post by SeijiSensei on 2015-09-08
Edit > Account Settings > Server Settings.  Set the "Check for New Messages Every" to a reasonable time like five or ten minutes.

Usually if I click on an IMAP folder in the tree, Thunderbird will update it as it opens.

---

### Post by donsy on 2015-09-08
> **SeijiSensei said:**
> Edit > Account Settings > Server Settings.  Set the "Check for New Messages Every" to a reasonable time like five or ten minutes.

Usually if I click on an IMAP folder in the tree, Thunderbird will update it as it opens.

Thank you, that plus tweaking the settings a bit more and it now works.

---

