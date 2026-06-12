---
title: "Fail during boot, mouse and tty at the same time"
date: 2013-02-06
forum: General Help
---

### Post by martvefun on 2013-02-06
Hello,

I recently partitioned my ubuntu 12.04 disk to install debian in dualboot. After the installation, ubuntu started once. I had a brief error message during boot about the partition 8f... (the uid of the ubuntu partition) not found but it worked fine.
The next time I started, I was stuck on a black screen with a '_' blinking **and** had the mouse pointer. I can switch between tty with alt-F1, F2... and I keep the mouse pointer. I tried too get an interface using startx in a tty but it failed. The initial screen (alt-F7) is the only one I don't have a command line, I am stuck with my black screen.

I had only 20GB used out of 250 on my ubuntu partition, after dived in 2 partitions of 120GB, it shouldn't be a problem of cutting into system data so.
I haven't seen any error on the screen.

Any idea what can cause the problem ?

Thank you

**Update** : if I restart lightdm in a tty, I can access my desktop ! However, I will have the same problem at the next boot.

---

