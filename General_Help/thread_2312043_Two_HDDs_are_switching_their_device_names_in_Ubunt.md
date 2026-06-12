---
title: "Two HDDs are switching their device names in Ubuntu Linux"
date: 2016-02-01
forum: General Help
---

### Post by Grigoriy on 2016-02-01
Hello!

Not like it's a problem so far, but mostly my curiosity. I have 2 disks  -- internal and external. The latter is connected via USB3 cable. My  Ubuntu install is on the external drive. W10 is inside my laptop (it's a  dual-boot system). So usually my internal drive is sda and my external  one is sdb in Ubuntu (they're both SATA drives, of course). But today  they switched their device names, so the internal became sdb and  external became sda. After the reboot everything got back to normal. I  personally haven't done anything in this regard. To me that's strange.  Maybe someone could explain that to me, please.

---

### Post by oldfred on 2016-02-01
I have had same issue with my flash drives and my old BIOS system and newer UEFI system.

I believe it is/was because I skipped a SATA port on motherboard. My old system  had 4 drives and flash drive became sde, but on reboot it became sdb. I later learned I had not plugged drives in SATA port order on motherboard.

I of course did the same on my new UEFI build, but had DVD installed and seen sometimes as second device. But sdb was always sdb, but in trying to use grub to boot using sda, but then loopmount ISO from hd1, gave errors, sdb was hd2. I changed DVD and sdb drive SATA ports and now no issue, sdb is hd1.

---

### Post by grahammechanical on 2016-02-01
I can confirm from my own experience that the labels sda, sdb, and so on, are related to sata1, sata2, and so on, as the sata ports are labelled on the motherboard. Disconnect a drive from sata1 and the drive on sata2 becomes sda. When before it was sdb. Replace the drive on sata1 and the drive on sata2 reverts to being sdb again.

And Grub sticks with the hd labelling system starting with hd0.

Isn't life wonderful!

---

### Post by QIII on 2016-02-01
And all of this is a good lesson in why using UUIDs in fstab is a good idea!

---

### Post by Grigoriy on 2016-02-01
Thank you all for your replies!

---

### Post by Habitual on 2016-02-01
Have a look at [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

