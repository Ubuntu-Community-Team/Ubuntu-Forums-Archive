---
title: "Mutt and mail format problem"
date: 2007-02-23
forum: General Help
---

### Post by David1965 on 2007-02-23
Hi.

I am using Mutt 1.5.12 on Ubuntu 6.10, and until recently had no problems. I've set up a new email account and when I go to my inbox it says "/home/username/Mail/inbox is not a mailbox". I've searched the net and found out what the problem is but can't find a way to resolve it. The problem is that mbox format expects the first line of a message to be the sender and date, but my first line is the return path. If I manually add a first line of a message in the mbox format everything works ok.

Any ideas/suggestions would be appreciated. 

Thanks.

---

### Post by llamakc on 2007-02-23
How are you delivering mail to your mbox? Are you running the mail server yourself?

---

### Post by David1965 on 2007-02-23
I'm using fetchmail to get the mail and procmail to filter it.

---

### Post by llamakc on 2007-02-23
The machine you're using to get the mail from is using Maildir instead.

---

### Post by David1965 on 2007-02-24
You were right llamakc. I've changed the mailbox directory structure and procmailrc and it now works fine. Thank you very much.

---

