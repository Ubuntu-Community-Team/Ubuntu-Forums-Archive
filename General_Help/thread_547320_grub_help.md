---
title: "grub help"
date: 2007-09-09
forum: General Help
---

### Post by numus on 2007-09-09
I have ubuntu on a partition on a 2nd harddrive and windows xp on the primary drive.. anyway to get grub to select windows xp as primary and i can select ubuntu.. right now it selects ubuntu as primary...

---

### Post by merlinus on 2007-09-09
In /boot/grub/menu.lst, look for a line that says:

default 0

Count down near the bottom of the file to find the number of lines that begin with

title

and subtract one from that of windows (counting for these purposes begins at zero rather than one).

Then change default 0 to that number.

If you want windows to appear first on the grub menu, post back.

---

### Post by numus on 2007-09-09
ya i want windows to appear first on grub

---

### Post by merlinus on 2007-09-09
Move all of the lines referencing windows (at the end of the file) above the line that says:

### BEGIN AUTOMAGIC KERNELS LIST

and leave default 0.

---

### Post by numus on 2007-09-09
the ext3 reader i am using for windows keeps crashing windows explorer when i try to enter teh boot directory

---

### Post by merlinus on 2007-09-09
Windows explorer?

Boot into ubuntu.  Then in a terminal:

```

gksudo gedit /boot/grub/menu.lst

```

---

### Post by p_quarles on 2007-09-09
1) Boot into Ubuntu
2) Once you've logged in, press alt-F2
3) Type "gksudo gedit /boot/grub/menu.lst"
4) Make the changes that Merlinus suggested.

Edit: Beat me to it :)

---

### Post by Maestro23 on 2007-09-09
> **p_quarles said:**
> 1) Boot into Ubuntu
2) Once you've logged in, press alt-F2
3) Type "gksudo gedit /boot/grub/menu.lst"
4) Make the changes that Merlinus suggested.

Edit: Beat me to it :)

You beat me to it. :)

---

