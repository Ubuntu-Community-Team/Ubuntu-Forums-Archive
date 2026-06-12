---
title: "FAT32 or EXT4?"
date: 2013-12-11
forum: General Help
---

### Post by chinmoy1955-gmail on 2013-12-11
Hello, this is a very basic question, which sometimes seems to confuse even experienced Linux users.
I have created a Ubntu Studio bootable pen drive using unetbootin. On checking its properties I find that it is formatted in FAT32. I have two questions related to this:
1) Can this pendrive be formatted in ext4 and then made into a bootable Ubuntu Studio medium?
2) Which file system will be better in this case, FAT32 or ext3 or ext4?
Thanks.

---

### Post by philinux on 2013-12-11
The ubuntu startup disk creator does the same thing. This is so the usb stick can be used to boot from any machine. If it was extx it would not boot from a windows machine. I'm not savvy with unetbootin thought.

Some one else ran into this. [http://ubuntuforums.org/showthread.php?t=1594533](http://ubuntuforums.org/showthread.php?t=1594533)

---

### Post by bab1 on 2013-12-11
> **philinux said:**
> The ubuntu startup disk creator does the same thing. This is so the usb stick can be used to boot from any machine. If it was extx it would not boot from a windows machine. I'm not savvy with unetbootin thought.

It's not because " it would not boot from a windows machine".  When you are booting up, the hardware has no OS running at all.  I would imagine that the script was originally written for FAT32.  Since FAT32 is near universal and it works, there is no reason to change it.

---

### Post by philinux on 2013-12-11
> **bab1 said:**
> It's not because " it would not boot from a windows machine".  When you are booting up, the hardware has no OS running at all.  I would imagine that the script was originally written for FAT32.  Since FAT32 is near universal and it works, there is no reason to change it.

Indeed. I replied too quickly.  I meant universal as you say. If you have other files on the stick like photos etc. Windows would not be able to see them.

---

### Post by pbrane on 2013-12-11
> **chinmoy1955-gmail said:**
> Hello, this is a very basic question, which sometimes seems to confuse even experienced Linux users.
I have created a Ubntu Studio bootable pen drive using unetbootin. On checking its properties I find that it is formatted in FAT32. I have two questions related to this:
1) Can this pendrive be formatted in ext4 and then made into a bootable Ubuntu Studio medium?
2) Which file system will be better in this case, FAT32 or ext3 or ext4?
Thanks.

***I assume you are talking about a live Ubuntu Studio image on a USB pendrive or thumbdrive.***
1) yes you can format the USB drive in ext4. And then use [FONT=Courier New]**dd**[/FONT] to write the iso to the pen drive. You don't need to though, as it wil probably end up back at FAT32 anyway after you write the image.
2) As previously stated FAT32 is just fine for this. The actual OS file system is squashfs anyway on a live image, so the USB drive file system isn't important for the live image to run.

---

### Post by sudodus on 2013-12-11
If you want ext4, you can install the system to the USB pendrive in the same way that you install to an internal drive. If you avoid proprietary drivers, it will even be portable. I suggest that you use a USB 3 pendrive to make it fast. This is the case for installed systems as well as persistent live systems, while regular live systems are rather fast also from a USB 2 pendrive. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

