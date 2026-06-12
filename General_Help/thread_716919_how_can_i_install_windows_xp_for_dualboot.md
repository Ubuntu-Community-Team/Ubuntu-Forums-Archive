---
title: "how can i install windows xp for dualboot"
date: 2008-03-06
forum: General Help
---

### Post by DeaDWiZ on 2008-03-06
I have in my computer installed ubuntu 7.10.I want to install with dualboot windowsXP.I place the CD in the driver but it does not makes boot from there.It is loading the grub and after the linux starts.I have change the bios to boot first from cd.

---

### Post by milton1 on 2008-03-06
if the bios is set to boot first from cd, and the cd is not booting, this suggests that either the cdrom drive is faulty, or the cd is not bootable. If the cd is a copy of another xp system disc, it may very well be missing the bootable option.

---

### Post by DeaDWiZ on 2008-03-06
In the past i had not problems.Now, when i did format my hard disk drive and i going to install first the windows and after linux i had error22 at grub.Finally i installed first linux but i can not install windows :(

---

### Post by milton1 on 2008-03-06
If the system is reaching the grub stage, it has already chosen to boot from the hard drive. The problem really can only be in one of three places: bios, cd-rom drive, or the cd its self. Try yanking the connection to the hard drive and booting again to see if it will recognize the cd.

---

### Post by DeaDWiZ on 2008-03-06
Look at the pictures.

---

### Post by milton1 on 2008-03-06
these confirm that your system is looking for the cd to boot first. That leaves two possibilities. Either the drive is bad, or the cd is bad. Will your linux install cd boot?

---

### Post by DeaDWiZ on 2008-03-06
yes. i installed linux from cd an hour ago.Can i unistall grub to install windows?

---

### Post by strabes on 2008-03-06
> **DeaDWiZ said:**
> yes. i installed linux from cd an hour ago.Can i unistall grub to install windows?

GRUB or linux is not your problem. Your problem is that your computer is unable to boot from the windows CD.

---

### Post by DeaDWiZ on 2008-03-06
But why i can not boot the windows cd and i can boot linux?
And why after format i had error 22?

---

### Post by prshah on 2008-03-06
Question: Did you change the position of your hard disk drive? Eg from Primary master to secondary master etc? if so better re-detect your HDDs in BIOS. 

There is no connection between GRUB and your windows boot disk. If you are reading the GRUB prompt then your computer has already decided to ignore your CD. 

The previous posters suggestions are best: Check your CD, your drive and your cables in that order. Oh before that, try redetecting your drives in the BIOS (if you have that option: "Automatically Detect (IDE) / (HDD) / (Hard disk drives)."

Also, if you have 2 CDROM drives, make sure that you are putting the Windows disk in the correct CDROM drive.. try both one after the other.

Cheers,
PRShah

---

### Post by prshah on 2008-03-06
If you have formatted your drives, then GRUB is trying the boot from an absent Linux installation. 

To remove grub, boot with your Windows CD, go to the emergency recovery console, and give the command "fdisk /mbr" to wipe your boot record clean.

Install Windows, then Install Ubuntu.

Cheers,
PRShah

---

### Post by xc3RnbFO8P on 2008-03-06
Did you used entire HD when you installed Ubuntu.

---

### Post by DeaDWiZ on 2008-03-06
> **prshah said:**
> If you have formatted your drives, then GRUB is trying the boot from an absent Linux installation. 

To remove grub, boot with your Windows CD, go to the emergency recovery console, and give the command "fdisk /mbr" to wipe your boot record clean.

Install Windows, then Install Ubuntu.

Cheers,
PRShah

Thanks my friend :)
Today i will go to buy a new dvd rom drive because i think this i have has a problem.I will inform you today:)

---

### Post by Shuggeh on 2008-03-06
Hey sorry to hijack the thread but ive got a similar problem im tryin to load Xp onto my acer laptop now i have ubuntu installed and it works fine but id rather go back to XP. Problem i have is that when i put my windows cd it loads up to a point and then it doesnt recognise my hard drive any ideas? thanks

---

### Post by xc3RnbFO8P on 2008-03-06
I belive there is nothing wrong with your drive, you just have to format HD to FAT32.

---

### Post by xc3RnbFO8P on 2008-03-06
> **Shuggeh said:**
> Hey sorry to hijack the thread but ive got a similar problem im tryin to load Xp onto my acer laptop now i have ubuntu installed and it works fine but id rather go back to XP. Problem i have is that when i put my windows cd it loads up to a point and then it doesnt recognise my hard drive any ideas? thanks

In bios disable AHCI

---

### Post by prshah on 2008-03-06
It doesnt recognise your hard drive or just doesnt show any partitions?

Again: if your hdd is not recognised at all, Windows setup will grind to a halt saying that it needs a hard disk to continue... in this case, check your BIOS options as mentioned earlier.

Otherwise: boot using any Ubuntu live CD, remove all linux and swap partitions, reboot using your Windows CD, and try to install. If it does not install, reboot with the same Windows CD and choose "R" for recovery console when prompted, and use the command "fdisk/mbr". Reboot and try to install again.

If it still doesnt work maybe you need to take it up with Microsoft / Acer.

Cheers,
PRShah

---

