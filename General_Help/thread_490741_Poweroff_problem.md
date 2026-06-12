---
title: "Poweroff problem"
date: 2007-07-02
forum: General Help
---

### Post by satimis on 2007-07-02
Hi folks,


Ubuntu desktop 7.04


System is halted but NOT poweroff.  Ubuntu logo is displayed on screen finally.  Pls advise which file I have to edit.  TIA


B.R.
satimis

---

### Post by ashwin_cse on 2007-07-03
When you want to switch off the system open console by pressing pressing alt+f2 & type gnome-terminal .This will open a terminal . Type sudo poweroff. This should poweroff the pc completely.

---

### Post by satimis on 2007-07-03
> **ashwin_cse said:**
> When you want to switch off the system open console by pressing pressing alt+f2 & type gnome-terminal .This will open a terminal . Type sudo poweroff. This should poweroff the pc completely.
Hi ashwin_cse,

Tks for your advice.  Tried it with the same result as running;

$ sudo poweroff
OR
$ shutdown -h now

On console/gnome terminal.

System halted with Ubuntu logo hanging on the screen.  Power is not off.


I think the OS is not yet properly configured for poweroff.  During booting started it displays "...ACPI Ubable to locate RSDP".


B.R.
satimis

---

### Post by satimis on 2007-07-04
Hi folks,

The problem was solved by editing /boot/grub/menu.lst.  Added "ACPI=force" (w/o quote) on kernel line

Now my Ubuntu box can be halted and poweroff.


B.R.
satimis

---

