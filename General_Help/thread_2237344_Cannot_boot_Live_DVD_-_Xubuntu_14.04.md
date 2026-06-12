---
title: "Cannot boot Live DVD - Xubuntu 14.04"
date: 2014-08-01
forum: General Help
---

### Post by windyrij on 2014-08-01
AMD64 Athlon 3200+, 2GB memory. Xubuntu 12.04 LTS  installed

Sony DW-G120A DVD/CD rewriter recently added as slave (CD rewriter already installed as master). Parallel ATA interface.

Live DVD created on system, from ISO image xubuntu-desktop-14.04-i386.iso download (checksum ok).

This DVD boots ok on a Lenovo Core i3 laptop, (Xubuntu 12.04 LTS installed).

DVD boots starts ok on AMD64 system (small logo at bottom of screen), but eventually hangs up.

A Live CD of Xubuntu 12.04 LTS boots ok in the DVD drive on the AMD64 system.

Anyone got any ideas, I am stumped!   Thanks,

John

---

### Post by Impavidus on 2014-08-01
Graphics driver? What kind of graphics card is in that computer?

When you hit a key at that first screen with a person and a keyboard you should get a menu t try some boot options. Try setting nomodeset. It may help.

---

### Post by windyrij on 2014-08-03
Hello impavidus:

Thanks for your post, the video adapter is Nvidia Geforce 9500.
Followed your advice about nomodeset, which allowed me to boot from DVD. For info - here is the sequence:

logo appears at bottom of screen
press Return immediately
Language menu page appears - default English
press Return
press F6 (other options)
select nomodeset (x)
press Esc
press Return
Boot process continues

Many thanks for your help,  John

---

### Post by minecraftpe-al on 2014-08-03
Good to know you managed to fix this as it helped me to

---

