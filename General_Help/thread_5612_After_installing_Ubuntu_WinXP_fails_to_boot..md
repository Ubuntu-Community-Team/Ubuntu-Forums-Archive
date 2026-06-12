---
title: "After installing Ubuntu WinXP fails to boot."
date: 2004-11-20
forum: General Help
---

### Post by dave on 2004-11-20
Now before you go windows bashing I need it for class... :(

Ok so I backup all my data and reformat the drive to square 1.  I install windows using 15Gb of 120Gb.  I boot and update it.  Now I install ubuntu in the following manor:

hda1 - windows (15gb)
hda2 - /boot  (128mb)
hda3 - swap  (256mb)
hda4 - /home (70Gb)
hda5 - /  (Rest of drive)

Now after doing so, and installing grub to the MBR, i configure grub to boot linux and windows:

title=Ubuntu
root (hd0,1)
kernel (hd0,1)/bzImage root=/dev/hda5 vga=791

title=WinXP
root (hd0,0)
makeactive
chainloader +1

However when trying to boot windows I get that output from grub as though it is trying to boot windows, but it stops, and hangs.  

thanks for any help :)

---

### Post by TravisNewman on 2004-11-20
[QUOTE=dave]Now before you go windows bashing I need it for class... :(

Ok so I backup all my data and reformat the drive to square 1.  I install windows using 15Gb of 120Gb.  I boot and update it.  Now I install ubuntu in the following manor:

hda1 - windows (15gb)
hda2 - /boot  (128mb)
hda3 - swap  (256mb)
hda4 - /home (70Gb)
hda5 - /  (Rest of drive)

Now after doing so, and installing grub to the MBR, i configure grub to boot linux and windows:

title=Ubuntu
root (hd0,1)
kernel (hd0,1)/bzImage root=/dev/hda5 vga=791

title=WinXP
root (hd0,0)
makeactive
chainloader +1

However when trying to boot windows I get that output from grub as though it is trying to boot windows, but it stops, and hangs.  

thanks for any help :)[/QUOTE]
 Go into the bios and set the hard drive read-mode to large or LBA, depending on your board. If you have both try LBA, and if that doesn't work try Large.

---

