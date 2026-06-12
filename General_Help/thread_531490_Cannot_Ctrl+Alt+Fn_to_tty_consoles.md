---
title: "Cannot Ctrl+Alt+Fn to tty consoles"
date: 2007-08-21
forum: General Help
---

### Post by imbjr on 2007-08-21
I've tried:

1. Modding Grub's menu.lst with vga=795 as a kernel option. I recently had to rejig menu.lst for other reasons (I shrank my XP partition and my devices changed their names!).

2. Re-installing numerous packages mentioned in similar threads here. Interestingly, I still get the double "Error activating XKB configuration" dialog if I tinker with, for example, adding euro symbol support.

3. Checked my init scripts. /etc/events.d looks ok. I thought I was missing /et/inittab but I tried that and then discovered its obsolete. However, I'm not sure if there's something in the rc.d directories I'm missing.

4. ps -elf | grep -i etty shows that getty is running for all 5 ttys.

5. My VirtualBox installation has no problem with getting to ttys and I can still alt+ctrl+backspace.

I recently installed VMWare (but this problem may have started some time back) and have an ATI card (with no 3D functionality). I get the right resolution I want from the card tho and whatever it was I installed the restricted drivers manager no longer says I need anything.

So, now I'm stumped.

---

### Post by zxccvb on 2007-08-21
Is your problem similar to either of these?

[http://ati.cchtml.com/show_bug.cgi?id=783](http://ati.cchtml.com/show_bug.cgi?id=783)
[http://ati.cchtml.com/show_bug.cgi?id=37](http://ati.cchtml.com/show_bug.cgi?id=37)

---

### Post by imbjr on 2007-08-22
zxccvb: neither of those apply.

I cannot reach the vts to begin with.

 I'm still wondering if its a grub vga problem. I may have to investigate numerous vga codes.

---

### Post by imbjr on 2007-08-22
Well, I've tried the grub menu mod in hex too now - no luck.

I've tried reconfig of xorg - no luck.

sudo dumpkeycodes gives
dumpkeycodes: No such device

sudo getkeycodes gives
Plain scancodes xx (hex) versus keycodes (dec)
0 is an error; for 1-88 (0x01-0x58) scancode equals keycode

KDGETKEYCODE: No such device
failed to get keycode for scancode 0x5a
(which I've seen during boot up too)

Looks like if I want tty1 I will have to alt+ctrl+backspace and then alt-ctrl+f1 - note that the backspace keycombo does not drop me to a terminal  - which I thought it would.

There's something borked about the keyboard, but whatever it is, it's not yeilding its secrets.

On the plus side, I may have just made a baby-step to getting 3d working on this ati card - after coming across an mtrr problem - though logs still suggest it's not perfect.

---

