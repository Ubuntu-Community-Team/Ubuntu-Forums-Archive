---
title: "Grub boots up at command line"
date: 2022-04-19
forum: General Help
---

### Post by drew1121 on 2022-04-19
I recently installed Xubuntu on my computer after switching it from PopOS. I had it dual booting windows with grub before and I replaced the partition with Xubuntu which comes with its own grub. but now when I boot up the computer it starts at a Grub command line. I can either type exit and it goes into a normal grub menu or I am able to press f2 and boot into Ubuntu or Windows by either my computers BIOS or Windows Boot Manager.  I got some boot information from boot repair if that is of any help [https://paste.ubuntu.com/p/wQ92cHzHN3/](https://paste.ubuntu.com/p/wQ92cHzHN3/)

---

### Post by tea for one on 2022-04-19
[COLOR="#0000FF"]Lines 319 to 326[/COLOR]
The default repair of the Boot-Repair utility would reinstall the grub-efi of sda3,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file
Blockers in case of suggested repair: 
Please use this software in a [COLOR="#0000FF"]live-session[/COLOR] (live-CD or live-USB). This will enable this feature. 

Have you tried the repair in a live session?

Although, it is not strictly essential as you can boot into both Windows and Xubuntu via your UEFI boot menu.

---

