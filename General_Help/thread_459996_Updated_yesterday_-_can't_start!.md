---
title: "Updated yesterday - can't start!"
date: 2007-05-31
forum: General Help
---

### Post by Skootle on 2007-05-31
Hi. I updated my ubuntu system yesterday (linux-kernel-headers or something like that) but now I can't start my machine! It loads GDM perfecly, but once I type in my username and password, everything goes wrong. It says it can't find the home directory and shoots me back to GDM, and if I try Gnome Failsafe, I'm also thrown back. 

I currently have 3 HDD's:
 - SATA 120GB -> Root /
 - ATA 40GB -> Home
 - ATA 200GB -> random files

I tried taking a look at my fstab from the Terminal Failsafe (which seems to run without problems) and there were some errors (like **error=UUID...bla...bla...bla**, I can't really remember since I'm on another computer right now), so I just backed it up and started modifying it to remove said errors. I'm still without luck, so I decided to post a thread here.

Thanks!

---

### Post by dr.silly on 2007-05-31
I have the exact same problem
try booting into the grub entry before it (not recovery mode) that worked for me

---

### Post by dr.silly on 2007-05-31
I have two hard drives by the way

---

