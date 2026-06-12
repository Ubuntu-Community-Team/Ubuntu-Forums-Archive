---
title: "Thunderbird + dovecot -&gt; data corruption?..."
date: 2008-05-17
forum: General Help
---

### Post by nazg00l on 2008-05-17
My setup is: a GUI workstation running Xubuntu Hardy + home file server running Dapper.

I have long used a Thunderbird mbox on the network drive, but after upgrading to Hoary and encountering some CIFS glitches I decided to migrate the whole setup to the "by the book" configuration, i.e. IMAP server (dovecot) on the file server (Ubuntu Dapper) + Tbird connecting to it. For various reasons I do not want to use fetchmail directly into the IMAP account, but rather to retrieve new mail from "real world" servers via POP3 using Tbird and then moving it within Tbird to the IMAP folders.

What resulted is apparent data corruption. Thunderbird retrieves a batch of mail from external servers (100+) all right, but then chokes up trying to move it to chosen IMAP folders (using filters). I get ```
The current command did not succeed. The mail server responded: Append aborted.
``` dialog on the workstation. Tbird IMAP logs do not show any unusual messages. Dovecot logs, on the other hand, show errors, but nothing related to aborting folder append actions:
```
Corrupted index cache file <IMAP_mailbox>/dovecot.index.cache:
Duplicated field in header: hdr.LIST-ID
```
Google didn't say anything at all about the Tbird error message, nor anything relevant about the Dovecot one. Rebuilding the index in Tbird caused some messages to be invisible (they still existed in actual IMAP folders on disk), while the errors in Dovecot log reappear next time for different folders...

So, it looked like a Thunderbird IMAP glitch. However, I just tried Claws Mail and it can see all messages in folders, including ones that Tbird could not. Ultimately I want to remain with Thunderbird, though. Any suggestion? I did not find any reported Tbird weaknesses for moving mail among IMAP folders, but perhaps there are some?...

---

### Post by Monicker on 2008-05-17
I'm not sure what is causing your issue, but I have never experienced any problems using Thunderbird to connect to a dovecot imap server.  That is what we use at work, and its always been fine.

---

### Post by nazg00l on 2008-05-17
Thanks for your reply **Monicker**, now I know that these two programs can work together, so my problems are most likely configuration-related.

I modified my Tbird filters so that now all POP3 mail is first downloaded into an mbox and then junk-filtered only. The problems seem to have disappeared, although Dovecot still logs *Corrupted index cache file* errors. Will wait and see. Perhaps the reason was too many concurrent IMAP requests associated with incoming mail from a dozen POP3 accounts?...

---

