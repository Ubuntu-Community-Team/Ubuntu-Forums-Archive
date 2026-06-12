---
title: "Dual Boot 2 Hard Drives. Ubuntu 13.10 and Windows 8.1 64-bit"
date: 2014-03-21
forum: General Help
---

### Post by shoki on 2014-03-21
[FONT=arial][COLOR=#333333]Can you: Install Ubuntu on Hard Drive#1 

Take out Drive#1 and then Install Windows 8.1 on Drive#2 

Install both Drives and then pick which one to boot from on startup?
[/COLOR]
[COLOR=#333333]I prefer if at all possible to leave the drives "clean" installs that do not link to each other. This way at any time I can remove one drive or the other and have a perfectly normal environment.
[/COLOR]
[COLOR=#333333]I would even go so far as to have a bootable USB key (or even a 3rd drive) that handled the selection of boot drive. I imagine I could pick a drive from the BIOS boot menu but a cool Chameleon like boot manager would be nice.
[/COLOR]
[COLOR=#333333]I used to do this back in the old days and it was a really nice set up.[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
[/COLOR]
[COLOR=#333333]Thank you,[/COLOR]
[COLOR=#333333]--shoki[/COLOR][/FONT]

---

### Post by Kris_Spencer on 2014-03-21
That sounds complelely do-able. You'd have to select which disk to boot from because the boot managers would be on their respected disks. So you'd have to either switch the boot priorities around in BIOS, or pull up the 'boot from what device' menu at BIOS time. The latter might be better/easier with a system that has UEFI. The boot loader isn't even written to the boot section of the disk. It makes booting from USB awesome!

---

