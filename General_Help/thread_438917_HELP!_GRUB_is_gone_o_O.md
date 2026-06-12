---
title: "HELP! GRUB is gone o_O"
date: 2007-05-10
forum: General Help
---

### Post by theaverageidiot on 2007-05-10
Okay, I dual-boot Windows and Ubuntu. I had Windows installed first and I installed Ubuntu and GRUB automatically was shown every time I booted up. It's been great. But my Windows has gotten far too slow (I like gaming on XP, Call of Duty and stuff) so I decided to reformat it. I put in the XP disc, choose to overwrite my old XP, and it did so. I'm 95% sure it left Ubuntu alone, but now my computer automatically boots into XP with no GRUB! I REALLY REALLY REALLY need to get into both XP and Ubuntu today. Someone, please help!! :(

---

### Post by ikonia on 2007-05-10
Grub is not installed on ubuntu - its installed on the master boot record of your hard disk. 

Be re-isntalling windows it will boot a new "windows" boot record on the master boot record thus overwriting grub.

your ubuntu install and data is still there, as is your grub config. Boot from the ubuntu cd and re-install grub using either grub-install or the "grub" shell.

you'll find it fine then.

---

