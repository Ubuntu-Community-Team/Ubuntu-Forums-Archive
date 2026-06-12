---
title: "Wubi on a Ubuntu 7.10 blew away the gui"
date: 2008-03-10
forum: General Help
---

### Post by jakey123 on 2008-03-10
I installed wubi off a Ubuntu 7.10 disk and when I restarted it said the Windows and Ubuntu Os are bootable and I did ubuntu and then there was a command prompt it blew a way the gui so hows can I get it back:guitar::popcorn:

---

### Post by tzulberti on 2008-03-10
If the Gnome isn't appearing you should do the following: "sudo dpkg-reconfigure xserver-xorg", and it would ask you some things about the GUI configuration. When that finish do: "sudo /etc/init.d/gdm restart", and GUI should appear.

---

