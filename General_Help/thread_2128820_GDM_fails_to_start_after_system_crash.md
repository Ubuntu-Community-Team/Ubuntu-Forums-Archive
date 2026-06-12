---
title: "GDM fails to start after system crash"
date: 2013-03-24
forum: General Help
---

### Post by Prodoc on 2013-03-24
My system hangs every once in a while when exiting [the game HoN](http://www.heroesofnewerth.com/). Usually it was fine just to reset the system, now GDM fails to start and I can't seem to fix it.

My system boots until the splash screen (plymouthd) only displaying the blue/green vertical bars and does not continue to show me the login screen. I disabled the splash in grub to see what is happening. All processes start fine, except GDM which displays a "[failed]" behind it. I can switch to a tty when in this state.

[LIST]
[*]I reinstalled the video card driver just in case
[*]I performed a fsck on all drivers as well just to be sure
[*]I reinstalled gdm (apt-get --reinstall install gdm)
[*]I tried resetting the gdm settings with *sudo -u gdm gconftool-2 --recursive-unset /*
[/LIST]
All to no avail.

Log files in /var/log/gdm don't give me much to go on, but I might be looking in the wrong files.
I installed lightdm as a test and that does work. This also lists GDM during boot and does start without "[failed]". As soon as I switch back to GDM it stops working again though.

How can I find out what is going wrong?

Specs:
OS: Ubuntu 12.10 GNOME remix (x64), with all gnome3 ppa packages updated.
Video card: AMD Radeon HD 6950 with proprietary CCC 13.3beta3 (13.2 at the moment of the crash)

---

