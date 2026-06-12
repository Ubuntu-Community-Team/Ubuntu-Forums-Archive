---
title: "Starting Hirens Boot CD PE from Grub2"
date: 2019-01-08
forum: General Help
---

### Post by kerrygee on 2019-01-08
Hi,

i am pretty stuck at this: How can i start a Hirens Boot CD PE from a hdd installed (BIOS and UEFI based) ubuntu systems grub? I couldt work out how to do this by my own. I also couldnt find any example here neither. Running different Linux flavors from grub ([https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)) isnt that difficult and many examples can be found in the www, but HBCD PE is a Windows PE based ISO image and differs totally by its nature internally from Linux ISOs. Any help, especially a working example, would be very nice! *thumbsup* 

[https://www.hirensbootcd.org/](https://www.hirensbootcd.org/)

Thanks in advance

K.

---

### Post by yetimon_64 on 2019-01-08
I am familiar with booting various linux based distros and "tool" disk images from grub2 but have never tried with hiren's boot cd, which as you've noted is a Windows PE based image; it has been quite a few years since I last used Windows on a regular basis. 

After a bit of web searching I found 2 [noparse]linuxquestions.org[/noparse] links, one from 2011 and one from 2013, that may be of some use in working out how to boot the hiren's image. They are ...
1. [[COLOR=#0000ff]Cannot boot Hiren's Boot from an ISO on ext3?[/COLOR]]("https://www.linuxquestions.org/questions/linux-software-2/cannot-boot-hiren%27s-boot-from-an-iso-on-ext3-871370/") (link) and
2. [[COLOR=#0000ff]boot hirens boot iso from grub2[/COLOR]]("https://www.linuxquestions.org/questions/linux-newbie-8/boot-hirens-boot-iso-from-grub2-4175452264/") (link)    

Both seem to indicate you will need to extract the contents of the image and copy menu.lst from the hbcd folder to the root of the storage drive. There is also mention of using grub4dos in one of the threads as another possibility; maybe you should also research chainloading grub4dos from grub2 etc.

Sorry I can't give you a more specific answer and good luck with this.

Regards, yeti.

---

### Post by yancek on 2019-01-09
If you are trying to boot Hirens or other windows iso files in the same manner as explained in the link you posted to the ubuntu site, I very seriously doubt there is any way to do that.  It just won't work.  As suggested above, it might be possible to do it by extracting the folders/files and copying them to a directory on your system.  It might be easier to create a small partition and extract the Hirens iso then copy it to a directory on the partition, preferably formatted ntfs or vfat.  You would then need to add an entry to boot it in grub.cfg or if you want to access it on a permanent basis, to the /etc/grub.d/40_custom file. 

I downloaded the zip version of Hirens several years ago and was able to boot it from Grub2 using the above instructions and putting it on a separate partition (either ntfs or vfat?)  This version had isolinux with an isolinux.cfg file in the isolinux directory.  It was necessary to rename isolinux.cfg to syslinux.cfg and copy it to the root of the partition filesystem.  It booted successfully with the entry below.  If you don't have the isolinux directory this won't work.  You would also need to change the insmod part_msdos to insmod part_gpt if you have a GPT drive and change the set root line to the correct drive/partition.

> menuentry 'CHAINLOAD HBCD' {
insmod part_msdos
insmod chain
set root=(hd0,1)
chainloader +1

---

