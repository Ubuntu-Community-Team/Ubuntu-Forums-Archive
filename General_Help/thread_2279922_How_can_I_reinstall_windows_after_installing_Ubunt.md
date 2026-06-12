---
title: "How can I reinstall windows after installing Ubuntu"
date: 2015-05-26
forum: General Help
---

### Post by MyLegGuy on 2015-05-26
How can I reinstall windows after I installed Ubuntu and removed it?

---

### Post by Vladlenin5000 on 2015-05-26
Hi and welcome.

Installing another OS in the same drive automatically removes what was there before.
Dual-boot is another story... What do you want to do exactly?

---

### Post by MyLegGuy on 2015-05-26
> **Vladlenin5000 said:**
> Hi and welcome.

Installing another OS in the same drive automatically removes what was there before.
Dual-boot is another story... What do you want to do exactly?

Hm... get rid of Ubuntu and just have windows.

---

### Post by kryten35 on 2015-05-26
You need a windows install disk and preferably  a windows drive image created via  file history in control panel.You should have done this before you removed it.
  
A recovery usb drive is no good because it uses a recovery partiton  which is created when you installed windows.If you wiped the drive then its gone. 
If you  try to use the usb drive to restore a disk image,then you cant do that either because it cannot delete/reformat a drive which needs to be done for a linux ext4 drive. 

 However a windows install disk can delete/reformat a drive.  Boot windows disk/at install stage select repair your computer option at botton Lhand corner./select advanced/select option to recover using a drive image. After that just follow the prompts. 

 Idiotic decisions by microsoft mean people who dont have an install disk are humped in the situation where they have wiped the drive and reformatted with ext4.

---

### Post by MyLegGuy on 2015-05-27
> **kryten35 said:**
> You need a windows install disk and preferably  a windows drive image created via  file history in control panel.You should have done this before you removed it.
  
A recovery usb drive is no good because it uses a recovery partiton  which is created when you installed windows.If you wiped the drive then its gone. 
If you  try to use the usb drive to restore a disk image,then you cant do that either because it cannot delete/reformat a drive which needs to be done for a linux ext4 drive. 

 However a windows install disk can delete/reformat a drive.  Boot windows disk/at install stage select repair your computer option at botton Lhand corner./select advanced/select option to recover using a drive image. After that just follow the prompts. 

 Idiotic decisions by microsoft mean people who dont have an install disk are humped in the situation where they have wiped the drive and reformatted with ext4.
I don't have an instillation disk. Does this mean I'm doomed?

---

### Post by kryten35 on 2015-05-27
Yes, you are doomed to a life of linux.Unless you decide to buy a windows disk.

If youd created a drive image and a recovery usb drive, then you could have used a bootable live ubuntu or gparted  disk to manually format the disk to windows ntfs.The recovery drive would then be able to restore the backup image.

---

### Post by westie457 on 2015-05-27
@ MyLegGuy
Which version of Windows did you have originally? Was it 7 or 8/8.1?

---

### Post by MyLegGuy on 2015-05-29
> **westie457 said:**
> @ MyLegGuy
Which version of Windows did you have originally? Was it 7 or 8/8.1?

Uh.. Windows Vista.

---

### Post by westie457 on 2015-05-29
Take a look at the advice in this link. It should be of use to you. [http://www.sevenforums.com/general-discussion/316777-need-vista-home-premium-oem-cd.html](http://www.sevenforums.com/general-discussion/316777-need-vista-home-premium-oem-cd.html)

If it is helpful and you need help to create a bootable medium - dvd or usb - post back here after you have downloaded the iso.

Edit: Having checked the links posted at sevenforums unfortunately all download links for Vista have been pulled and Vista is no longer available legally anywhere.
Your choices now are purchase a legal copy of Windows 7, contact the manufacturer of your system for a set of recovery disks or stick with Linux/Ubuntu.
Apologies for giving you false hope.

---

### Post by MyLegGuy on 2015-05-30
> **westie457 said:**
> Take a look at the advice in this link. It should be of use to you. [http://www.sevenforums.com/general-discussion/316777-need-vista-home-premium-oem-cd.html](http://www.sevenforums.com/general-discussion/316777-need-vista-home-premium-oem-cd.html)

If it is helpful and you need help to create a bootable medium - dvd or usb - post back here after you have downloaded the iso.

Edit: Having checked the links posted at sevenforums unfortunately all download links for Vista have been pulled and Vista is no longer available legally anywhere.
Your choices now are purchase a legal copy of Windows 7, contact the manufacturer of your system for a set of recovery disks or stick with Linux/Ubuntu.
Apologies for giving you false hope.
Oh well.

---

