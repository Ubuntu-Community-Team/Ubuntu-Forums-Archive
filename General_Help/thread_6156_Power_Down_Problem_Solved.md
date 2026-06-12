---
title: "Power Down Problem Solved"
date: 2004-11-25
forum: General Help
---

### Post by CAPTAIN RON FL on 2004-11-25
**THIS IS FOR ALL THOSE PEOPLE OUT THERE WHO ARE HAVING PROBLEMS SHUTTING DOWN THEIR BOXES** 

[QUOTE=CAPTAIN RON FL]**POWER DOWN PROBLEM SOLVED** 

Finally got my sisters machine to completely shut down.

This is how I did it.

I did this: sudo gedit /boot/grub/menu.1st in a terminal.
 added acpi=off apm=power-off as shown below: 

title Ubuntu, kernel 2.6.8.1-2-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.8.1-2-386 root=/dev/hda1 ro single acpi=off arm=off
initrd /boot/initrd.img-2.6.8.1-2-386
savedefault
boot

Saved and then I  typed "sudo gedit /etc/modules" into a terminal; typed my password in and this is what I got:


# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line. Comments begin with
# a "#", and everything on the line after them are ignored.

psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp
apm

I then added "apm to the last line. Saved and closed out the terminal.


That's how I got mine to power off on shut down. :grin:  \\:D/[/QUOTE]

**I WANT TO THANK ALL THOSE WHO HELP ME SOLED THIS PROBLEM. HERE'S A BIG THANK YOU FROM CAPTAIN RON!!!**  \\:D/  :grin:

---

### Post by wallijonn on 2004-11-25
Thank you for posting the fix.

---

