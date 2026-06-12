---
title: "The bsd-mailx option [-b bcc-addr] doesn't work at all."
date: 2018-04-06
forum: General Help
---

### Post by Hans_van_Leeuwen on 2018-04-06
On my Ubuntu 16 system the package "bsd-mailx" is installed.

The [-c cc-addr] option of the executable bsd-mailx works correct.
But the [-b bcc addr] doesn't work at all.

After the command below both Steve and John bith get the E-mail.
$ date | bsd-mailx -s cc-test -c [email]steve@gmail.com[/email] [email]john@gmail.com[/email]
$ mailq
-Queue ID-  --Size-- ----Arrival Time---- -Sender/Recipient-------
028D34C0059      236 Fri Apr  6 13:49:54  root
                                         [email]john@gmail.com[/email]
                                         [email]steve@gmail.com[/email]


After the command below only John get the E-mail and Steve doesn't get the E-mail.
$ date | $ bsd-mail -s bcc-test -b [email]steve@gmail.com[/email] [email]john@gmail.com[/email]
$ mailq
-Queue ID-  --Size-- ----Arrival Time---- -Sender/Recipient-------
028D34C0059      236 Fri Apr  6 13:49:54  root
                                         [email]john@gmail.com[/email]

Is this a user error of mine or a bug in the bsd-mailx executable?

---

