---
title: "Help with Kernel Compile"
date: 2008-06-12
forum: General Help
---

### Post by ShinHadoken on 2008-06-12
Ok, so I followed the instructions [here]("http://kernelnewbies.org/FAQ/KernelCompilation") and I've done well so far, no problems. Except at the *very* end. You see, I'm running a Wubi installation, and I don't have a lilo.conf file. What file do I need to edit to get my new kernel to show up in the "ESC menu" at boot in Wubi?

Thank you SOOOO much,

SH

---

### Post by Nepherte on 2008-06-12
Ubuntu uses grub as default boot manager, not lilo. You can find the boot entries in /boot/grub/menu.lst

---

### Post by MaxNorris on 2008-06-12
For me anyway, I used the instructions in the [Master Kernel Thread](http://ubuntuforums.org/showthread.php?t=311158), and they worked spot on for me.  I didn't have to manually create a Grub entry; Dpkg automatically created one when I installed the resulting .deb's.

---

