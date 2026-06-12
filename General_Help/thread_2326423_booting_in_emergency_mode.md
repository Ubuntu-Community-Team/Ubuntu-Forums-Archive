---
title: "booting in emergency mode"
date: 2016-05-31
forum: General Help
---

### Post by beba on 2016-05-31
Hi

ive been on ubuntu for a few weeks (ever since my old SSD crashed) and have been enjoying it, however yesterday i got a new ssd and installed windows 10 on it (keeping my ubuntu on a separate drive)
my intention is to create an image of my ubuntu drive and then run it as a virtual machine

so i put in the SSD yesterday and installed windows 10 on it, went into my bios and changed boot settings so that the new ssd was first in boot order
it boots windows 10 perfectly

the issue however, happened this morning when i went back into the bios and changed the boot order to my ubuntu drive
it boots straight into Emergency Mode

i tried unplugging the SSD and restarting, same problem
i ran the advanced options (under grub, when it boots up initially) and ran a repair of ubuntu, but it didnt work

how do i fix this so i can boot back into ubuntu (or is there any way i can create an image of the ubuntu system from windows 10, or from a live cd of some sort)?

---

### Post by yancek on 2016-05-31
Did you install windows 10 in UEFI with GPT?  Was Ubuntu installed UEFI?  They both need to be UEFI or both MBR installs or the result is what you get.  Check the link below for more info on this.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> or is there any way i can create an image of the ubuntu system from windows 10

Good luck with that,  a default windows system can't even read a Linux filesystem.  You might be able to use third party software or you could use clonezilla to image Ubuntu.

---

