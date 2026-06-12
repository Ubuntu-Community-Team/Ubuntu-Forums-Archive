---
title: "[SOLVED] No Virtual Terminals, just black screen :("
date: 2007-11-09
forum: General Help
---

### Post by kvonb on 2007-11-09
-

---

### Post by omrsafetyo on 2007-11-09
have you tried modifying the runlevel in /etc/inittab ??

For instance, tty1 is runlevel 1 (I believe), whereas the GUI login that we usually see is tty0/runlevel0.  If you modify this to load a different runlevel, you should get console login.

If you want to force it through GRUB... try this... [http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-rescuemode-booting-single.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-rescuemode-booting-single.html)  its for red-hat but should work.

Just see the note at the bottom if you are using SCSI drives.

---

### Post by kvonb on 2007-11-09
-

---

### Post by kvonb on 2007-11-09
-

---

