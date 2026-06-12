---
title: "Move mail from evolution to thunderbird"
date: 2007-09-05
forum: General Help
---

### Post by wolf202 on 2007-09-05
Hi, I have all my mail in evolution on my ubuntu system, and i need to move it to thunderbird on a windows system.  How can I export my evolution email to a format like .mbox?

-wolf

---

### Post by Irihapeti on 2007-09-05
Evolution mail already seems to be in mbox format. If you install the Thunderbird extension ImportExportTools, you can use it to import the mbox files into Thunderbird.

HTH

Irihapeti

---

### Post by wolf202 on 2007-09-05
but where do i find the .mbox file?

---

### Post by ninehrcoma on 2007-09-05
One way to do the migration would be to set up or turn on imap on your mail server (or even a local instance of postfix/dovecot). You could then copy your mail folders up to the server (into your imap folders) and connect to the same account with thunderbird to copy them back locally. We have done this successfully several times.

---

### Post by Irihapeti on 2007-09-05
Sorry, should have included this information in the earlier message. The mailbox files are in ~/.evolution/mail/local - or at least they are on my system. It's a hidden folder, so you'll need to have "show hidden files" turned on.

Irihapeti

---

### Post by wolf202 on 2007-09-06
Thanks for all the help got everything transfered over!

---

