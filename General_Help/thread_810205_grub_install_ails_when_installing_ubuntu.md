---
title: "grub install ails when installing ubuntu"
date: 2008-05-28
forum: General Help
---

### Post by jorik42 on 2008-05-28
hey all;

     So, im trying to in install xubuntu onto an old trashy computer i have lying around.  the install proceeds normally, until the installer tries to install grub.  then i get the error:


executing 'grub-install (hdo)' failed
this is a fatal error.

running 'sudo fdisk -l' from the live cd returns that disk dev/hda doesnt have a valid partition table, yet when i run the hard drive is clearly shown to be in the following partitions:

/dev/hda1 - unknown     31.5kib
unallocated             8.81Mib
/dev/hda2 - ext3        17.39Gib  (mountpoint /target)
/dev/hda3 - linux-swap  1.68Gib

it should also be noted that the OS installs fine up until it tries to install grub.  

anyone have any idea whats going one here?  Ill also note that i cannot use gparted to remove the unknown partition on /dev/hda1; it always returns an error message.  

EDIT: when trying to delete /dev/hda1 again, the details of the error noted that there was no partition map.  also, everytime i perform an operation in gparted, it re-scans afte the operation competes (as it should).  however, there is always a segmentation error.  

also, i just noticed that its reading /dev/hdc as a read-only file system, if that helps anything....



---jorik

---

### Post by Tspurs on 2008-09-03
J have the same problem,but i have a new computer. The same message comes up, Ubuntu is allmost finished about 94% and the **_grub-install hdo fail_** comes up and goes back too Ubuntu live cd. My computer skills isnt the best, and i dont know any with skills. Please help me

Regards
Trond

---

### Post by jorik42 on 2008-09-03
hey

its been a while, but i think that the problem in questino (at least on my drive) was that the partition table was invalid/corrupted.  that was what was causing the grub install to mess up.  this can be corrected by using the mkfs utility (read the man page (man mkfs) in order to learn more about it; its pretty straightforward though).  If you have any other questions feel free to post and i'll help as i can.


jorik42

---

### Post by Shazaam on 2008-09-03
Some times you need a stand-alone version of gparted. Go here, download and burn a gparted livecd....
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

If there isn't ANYTHING that you need on the drive set the pc to boot from cd. When the gparted livecd boots you will have a choice of video types. Either choose the first one or the second for vesa if the graphics card has a problem. Once you get to the main gparted screen go ahead and delete ALL partitions (one at a time). Then go to "Device>Set Disklabel". Choose the dos default. This usually wipes everything. Hit Apply. Then reboot the pc back to the gparted livecd. The drive should show up as unpartitioned space.
Do the rest one at a time.
Make a swap partition. The size depends on if you are going to try to Suspend/Hibernate. Equal or double your installed RAM is fine for that. Otherwise 1 gig max is ok. Next create an Extended partition to fill up the rest of the drive. Inside the Extended partition make a ext3 Logical partition to hold Xubuntu. Reboot again to the gparted livecd and check the partitions. Completely shutdown the pc.
Boot the Xubuntu livecd; when you get to the partitioning phase choose either Use existing or Manual, point the installer to the partitions you have already created. Xubuntu will automatically re-use the /swap you previously made and install in the Logical partition. If it tells you it is going to format those partitions go ahead and let it.

---

### Post by Tspurs on 2008-09-04
Thanks, im going too try this today, and hope its working:)

Regards
Trond

---

### Post by caljohnsmith on 2008-09-04
> **Tspurs said:**
> J have the same problem,but i have a new computer. The same message comes up, Ubuntu is allmost finished about 94% and the **_grub-install hdo fail_** comes up and goes back too Ubuntu live cd. My computer skills isnt the best, and i dont know any with skills. Please help me

Regards
Trond
Having the install fail at 94% with a Grub error is a known bug that can be circumvented by using an ext2 file system (rather than ext3) for Ubuntu. Try that, and if that lets you successfully install Ubuntu, you can easily "upgrade" your file system to ext3 with the following:
```
sudo tune2fs -j /dev/sdXY
```
Replace sdXY with your Ubuntu partition of course. After that, I believe the only thing you need to do is edit your /etc/fstab so that the Ubuntu partition is mounted with "ext3" instead of "ext2".

---

### Post by Tspurs on 2008-09-04
Thanks:):):) Now ubuntu is installed on my computer....:guitar:

---

### Post by GmanMac on 2009-01-20
> **caljohnsmith said:**
> Having the install fail at 94% with a Grub error is a known bug that can be circumvented by using an ext2 file system (rather than ext3) for Ubuntu. Try that, and if that lets you successfully install Ubuntu, you can easily "upgrade" your file system to ext3 with the following:
```
sudo tune2fs -j /dev/sdXY
```
Replace sdXY with your Ubuntu partition of course. After that, I believe the only thing you need to do is edit your /etc/fstab so that the Ubuntu partition is mounted with "ext3" instead of "ext2".
Hello,

I'm having the same problem, but when I tell it to use ext2 I get a different error message-- No root file system is defined. Please correct from the partition menu. I can;t figure out what settings I need to change to define the root file system

---

### Post by caljohnsmith on 2009-01-20
> **GmanMac said:**
> Hello,

I'm having the same problem, but when I tell it to use ext2 I get a different error message-- No root file system is defined. Please correct from the partition menu. I can;t figure out what settings I need to change to define the root file system
It sounds like you might need to set the "mount point" when you go through the installation process. Whichever is your main Ubuntu partition, set its mount point to be "/" or root. Then see if you can proceed.

---

### Post by GmanMac on 2009-01-20
> **caljohnsmith said:**
> It sounds like you might need to set the "mount point" when you go through the installation process. Whichever is your main Ubuntu partition, set its mount point to be "/" or root. Then see if you can proceed.

Thanks I tried but then I go right back to the Grub Install HDO failure.

---

### Post by caljohnsmith on 2009-01-21
How about when you get to the finally stage of the installation process, click the "advanced" button, and specify to have Grub installed to /dev/sda or whichever is the drive you are installing Ubuntu to. Some people have successfully used that as a workaround for the "94% Fatal Grub Install" bug. Let me know if that makes any difference.

---

### Post by GmanMac on 2009-01-24
> **caljohnsmith said:**
> How about when you get to the finally stage of the installation process, click the "advanced" button, and specify to have Grub installed to /dev/sda or whichever is the drive you are installing Ubuntu to. Some people have successfully used that as a workaround for the "94% Fatal Grub Install" bug. Let me know if that makes any difference.

Well I seem to have made some progress using standalone Gparted and your Mount point suggestions.

Now I get
(initramfs) on boot up.

---

### Post by GmanMac on 2009-01-25
Thanks for your help I got it. I think it was Grub installer to ext2 & / & mount that did it

---

