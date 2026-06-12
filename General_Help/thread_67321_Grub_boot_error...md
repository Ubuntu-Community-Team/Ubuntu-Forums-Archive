---
title: "Grub boot error.."
date: 2005-09-19
forum: General Help
---

### Post by n0ah on 2005-09-19
Ok, I got home from work, and my computer was frozen.. only solution was a hard boot (which I absolutely hate doing).. when it came back up.. I get this..


  Booting `Ubuntu, kernel 2.6.10-5-amd64-generic Default `

root (hd0,0)
  Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz root=/dev/sda1 ro acpi=off console=tty0 quiet splash

Error 17: Cannot mount selected partition

Press any key to continue...


I'm goin nuts, I've removed drives and checked the cables, checked my bios, and a number of other things, among them I've googled the error, which I found other people had got when trying to Dual boot, but I've switched strictly to Ubuntu about two months ago.. 

If anyone can help I'd appreciate it very, very much.

Thanks,
-Derek


btw..
AMD 64 3200+, 1GB DDR, 2x WD 160GB SATA, 1x WD 160GB IDE, GeForce 6600GT.. anything else ya might need to know?

---

### Post by ektich on 2005-09-20
[QUOTE=n0ah]Ok, I got home from work, and my computer was frozen.. only solution was a hard boot (which I absolutely hate doing).. when it came back up.. I get this..


  Booting `Ubuntu, kernel 2.6.10-5-amd64-generic Default `

root (hd0,0)
  Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz root=/dev/sda1 ro acpi=off console=tty0 quiet splash

Error 17: Cannot mount selected partition

Press any key to continue...


I'm goin nuts, I've removed drives and checked the cables, checked my bios, and a number of other things, among them I've googled the error, which I found other people had got when trying to Dual boot, but I've switched strictly to Ubuntu about two months ago.. 

If anyone can help I'd appreciate it very, very much.

Thanks,
-Derek


btw..
AMD 64 3200+, 1GB DDR, 2x WD 160GB SATA, 1x WD 160GB IDE, GeForce 6600GT.. anything else ya might need to know?[/QUOTE]

Looks like a harware failure to me. Do you have  Ubuntu Live CD handy (or any other Live CDs)? If you boot from it can it detect and access your hard drive?

---

### Post by dangman4ever on 2005-09-20
[http://ubuntuforums.org/showthread.php?t=65575&highlight=Error+17](http://ubuntuforums.org/showthread.php?t=65575&highlight=Error+17)

That thread contains at least three ways to fix error 17.

---

### Post by n0ah on 2005-09-20
Thanks to both of ya's, I got frustrated and bugged a friend to come help (two heads, one not frustrated) and he reset the bios w/ the jumper, fixed the boot order of the drives and that solved it.. 

What it was (I figured it out after actually thinking about it) was that my IDE drive had had Ubuntu/Windows dual boot previously and it was trying to boot a non-existant OS/parition.. which makes sense now..

Thanks a bunch though (:

-Derek

---

