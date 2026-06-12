---
title: "changing permission"
date: 2008-06-27
forum: General Help
---

### Post by steve984 on 2008-06-27
is there a way for me to log on as administrator all the time. I am using hardy and I need to change files to get my hardware to run on my computer but it keeps saying I don't have permission. I am the only one who uses this computer so security is not a concern

---

### Post by mcduck on 2008-06-27
> **steve984 said:**
> is there a way for me to log on as administrator all the time. I am using hardy and I need to change files to get my hardware to run on my computer but it keeps saying I don't have permission. I am the only one who uses this computer so security is not a concern

If your computer is connected to Internet then security is _always_ a concern.

Anyway, you don not need to log in as root, the first user created during install belongs to admin group and is able to temporarily gain root privileges. Just use the "sudo" in fron tf those commands taht would otherwise need to be run as root.

If you want to open the file manager with full privileges just hit alt-f2 and run "gksudo nautilus". Remember to close the window as soon as you don't need it any more, as it allows you to break your system..

You should also read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

