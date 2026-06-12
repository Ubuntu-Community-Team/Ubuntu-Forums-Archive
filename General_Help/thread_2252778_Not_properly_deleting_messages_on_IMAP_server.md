---
title: "Not properly deleting messages on IMAP server"
date: 2014-11-14
forum: General Help
---

### Post by defaria on 2014-11-14
I'm running Ubuntu 14.04 server with Dovecot IMAP. I also use k9 on my cell phone and Thunderbird at home on my Ubuntu Desktop as well as on Windows at work with Thunderbird also connecting to my IMAP server at home. And I've configured k9 to delete messages on the IMAP server when I delete them in k9. But they don't get removed from the IMAP server when I delete them in k9. Similarly when I delete them in TB on the desktop they are still on k9 and TB on Windows at work. IOW I have 3 email clients I use to read my IMAP store and I want it such that if I delete a message on one client they disappear from the other clients. Note I can refresh or re-get email on TB, for instance and  the messages are still there. I can expunge or compact folders and the messages remain on the other clients. I can stop and restart TB and still they remain. If I get one email I have to delete it three times, one for each place.

Is there a config setting I'm missing on the server (I have full control there)?

---

### Post by defaria on 2014-11-18
Nobody?!?

---

### Post by defaria on 2014-11-19
Apparently I found that my Thunderbird cache (.msf files) were corrupted. Thought it might be an IMAP server settings. Sorry.

---

