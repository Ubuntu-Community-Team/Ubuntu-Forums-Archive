---
title: "[SOLVED] 2 Questions (GRUB and Desktop)"
date: 2007-08-08
forum: General Help
---

### Post by dmf86 on 2007-08-08
Hi there. After some experimenting with the ATI driver and some updates, i got it to work, but i lost items in the "Places" menu! :| All that remains in "Desktop", and when i click it, it appears "could not open location "file:///home/myusername/Desktop | There is no default action associated with this location".
So my first question is: how do i get the lost items? (home, etc) I can't access my files...
The second question is: I got a dual-boot system, and now in the GRUB e got new entries regarding, without knowing why... the only difference between then is the kernel version. When i choose one or the other, it seems to me that im always in the "same" OS... What it means? Thanks for any assistance.

---

### Post by dmf86 on 2007-08-08
Solved it :) Missing Nautilus... Close thread please.

---

### Post by dfreer on 2007-08-08
As for GRUB, every so often a new kernel update will come along, and the default behavior for GRUB is to list the new versions alongside the old ones. This is in case a new kernel update causes the system to not boot, you can fallback to an older kernel. 
You can change it's default behavior, so that it never shows a new kernel, or it *only* shows the newest kernel, or even a combination (so that it shows the 2 newest kernels only).

As for the desktop issue, does it literally say "file:///home/myusername/Desktop ....", or is your actual username in there, say *dmf86* for example?

EDIT: You can put [SOLVED] at the beginning of the title thread if you wish, by editing your first post.

---

### Post by dmf86 on 2007-08-09
It said my actual username, but since i was testing i had removed Nautilus by mistake and that caused it... :) Thanks for the reply.

---

