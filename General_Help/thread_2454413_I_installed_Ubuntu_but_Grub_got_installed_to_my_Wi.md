---
title: "I installed Ubuntu but Grub got installed to my Windows partition instead of my secon"
date: 2020-11-29
forum: General Help
---

### Post by starcitizen on 2020-11-29
Hi,

I installed Ubuntu (Budgie version) to my Secondary SSD (labelled sda by the installer) but somehow grub got installed to my Windows SSD (sdb), so that every time I start my computer grub comes up.

How do I remove Grub completely from this Windows SSD?

---

### Post by starcitizen on 2020-11-29
Solution found that works:

[TABLE="width: 64"]
[TR]
   [TD="class: xl65, width: 64"][https://www.binaryera.com/2020/08/RemoveGrubFromWindow10.html](https://www.binaryera.com/2020/08/RemoveGrubFromWindow10.html)[/TD]
 [/TR]
[/TABLE]

---

### Post by oldfred on 2020-11-29
You need grub to boot Ubuntu.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive.

---

