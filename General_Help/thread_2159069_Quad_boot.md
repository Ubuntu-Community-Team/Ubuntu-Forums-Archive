---
title: "Quad boot"
date: 2013-07-01
forum: General Help
---

### Post by cuzzo13 on 2013-07-01
Ok I have windows 7 (installed 1st) xp (2nd) ubuntu (3rd) and Windows 8 (last) Windows 8 blue bootloader was installed then i used easybcd trying to get ubuntu on it the other ones were already there. I want to know how can i get ubuntu and the other os's on the blue windows 8 bootloader so they will all boot to the correct os's right? im using a toshiba satellite l455d-s5976.

---

### Post by oldfred on 2013-07-01
Do not know about EasyBCD. But Windows moves all boot files to first install with boot flag as that is the "active" partition in Windows and the only one it can boot from.
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words. Discusses Vista, but applies to all BIOS based Windows installs (not UEFI).
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

