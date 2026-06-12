---
title: "Quick question about the sudo command"
date: 2013-02-17
forum: General Help
---

### Post by xSCCMx on 2013-02-17
In Ubuntu, many of you know that the sudo command asks for your password to install a program, much like the software center.

My question is that if I was to change my user password, would I have to change anything within sudo for the password to be valid?


Thank you.

---

### Post by papibe on 2013-02-17
Hi xSCCMx.

No. If you change your password, the next time you use sudo, you'll need to enter the new one.

'sudo' is not associated to your password, but to your user (because you are on the admin group).

When 'sudo' asks a password, it is not asking a special password for root or an admin group. It is asking for you to reconfirm that you are "you".

Take a look at this help [page]("https://help.ubuntu.com/community/RootSudo") for more details.

Does that help?
Regards.

---

