---
title: "My outbox in Evolution is gone"
date: 2008-06-19
forum: General Help
---

### Post by Aeph on 2008-06-19
So my outbox disappeared. If I try to add a folder called "outbox", I get a message saying: "Error while creating folder 'Outbox'." I can't send email anymore. Does anybody know how to fix this?

---

### Post by Aeph on 2008-06-20
I also tried reinstalling Evolution and resetting my account, neither of which worked.

---

### Post by Werner Iseli on 2008-11-23
I had the very same problem: the outbox suddenly just wasn't there. And without outbox, evolution cannot send any e-mails. This happened with ubuntu 8.04 hardy heron and after I upgraded to 8.10 intrepid ibex, the problem still remained.

I found out that my outbox file was extremely huge and after doing a tail on the file I noticed there was a mail in there with a huge attachment. So beware, don't send huge files with evolution. In general, huge mails don't reach the recipient anyway, since most e-mail systems allow e-mails only up to 500 megs or so. So I decided to move the file away and create an empty Outbox file. And voilà, it worked again!

For those interested, here's an ls of the Outbox files:

~/.evolution/mail/local$ ls -l Outbox*
-rw------- 1 werner werner 2786071365 2008-10-12 09:22 Outbox
-rw-r--r-- 1 werner werner        137 2008-11-23 08:10 Outbox.cmeta
-rw------- 1 werner werner         44 2008-10-06 23:07 Outbox.ev-summary
-rw------- 1 werner werner          3 2008-10-06 23:07 Outbox.ev-summary-meta
-rw------- 1 werner werner       7168 2008-11-22 23:43 Outbox.ibex.index
-rw------- 1 werner werner          8 2008-11-22 23:43 Outbox.ibex.index.data

~/.evolution/mail/local$ mv Outbox Outbox.broken
~/.evolution/mail/local$ > Outbox

Hope this helps.
Werner

---

