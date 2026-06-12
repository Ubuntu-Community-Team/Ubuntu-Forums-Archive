---
title: "Security question"
date: 2007-03-10
forum: General Help
---

### Post by wireless on 2007-03-10
Hey All
after passing a sudo command i.e sudo synaptic and typing the password. afterwards any sudo command i give it dosnt ask for a password but running the command streight away.. is it normal?
thnx in advance.

---

### Post by aa.ivanov on 2007-03-10
Yes it is.

When you get administrative privileges with sodo, gksudo or kdesu they do not expire at once but are rather kept for a small period of time. That's why sudo is not asking you for password the second time. BTW synaptic is a GUI tool and calling it through sudo might cause you headaches. Use gksudo for all GUI stuff instead of sudo.

One more thing - linux documentation is generaly much more usefull than windows documentation. Here's some ubuntu documentation relevant to sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by wireless on 2007-03-10
thnx mate :)

---

