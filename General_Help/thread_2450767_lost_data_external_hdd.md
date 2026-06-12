---
title: "lost data external hdd"
date: 2020-09-20
forum: General Help
---

### Post by jacob722 on 2020-09-20
Hello,

I have Ubuntu 20.04 LTS and i needed to instal Windows 8.1 on it as well, so i did that. when i had Windows running i could not boot up Ubuntu any more. So i copied the windows partition on to my external hdd via windows 8.1 disk management program.

Now my laptop don't recognize/see the external hdd when its mounted. i searched online and found a few videos. they say i need to use fdisk and copy a image of the external hdd. my problem is thay my laptop only has 265gb and the files on the external hdd are 500+gb. 

my question is how can i get my files back?
Is there a way to get my files back without having me to back up the files?

---

### Post by CelticWarrior on 2020-09-20
Welcome.

Sorry to say, you pilled a series of "don't", one on top of the previous.

> [COLOR=#000000]I have Ubuntu 20.04 LTS and i needed to instal Windows 8.1 on it as well, so i did that. when i had Windows running i could not boot up Ubuntu any more.[/COLOR]
No, you don't need Windows, nobody does, but this not being the problem in itself I wouldn't be discussing it except to say that choosing Windows 8.1 instead of 10 is a really dumb choice but alas, if properly installed, the dual-boot should work. So, assuming it was correctly installed, that it change the bootloader order to itself is totally expected. Now, if UEFI, all you had to do was opening UEFI settings > Boot and change it back to "Ubuntu" (from "Windows bootloader manager"), then boot Ubuntu and run 'sudo update-grub' to re-detect all OSes and add a new entry (Windows) to the Grub menu. However, if BIOS, you'd need to reinstall Grub in the MBR.

> [COLOR=#000000]So i copied the windows partition on to my external hdd via windows 8.1 disk management program.[/COLOR]
What was the purpose or reasoning for this? Windows can't be installed or boot from external drives. And did you managed to do it exactly? How this was done determines what you can do now to recover files (if at all possible).

The problem is not knowing enough to do what you did, not knowing that probably you shouldn't do it at all, and **not having backups**&#8203;, something you should always have and especially when dealing with OS installations or managing partitions.

---

### Post by oldfred on 2020-09-20
In addition Windows 8 or 10 uses fast startup which sets the hibernation flag. And resets it with updates.
And then the Linux NTFS driver will not open the NTFS partitions with normal read/write to prevent damage.

You may be able to manually mount in read only mode, but should have turned fast start up off in Windows if dual booting.

Change example with sdb1 to your NTFS partition. ro is read only.
mkdir /media/win
sudo ntfs-3g -o ro /dev/sdb1 /media/win

---

