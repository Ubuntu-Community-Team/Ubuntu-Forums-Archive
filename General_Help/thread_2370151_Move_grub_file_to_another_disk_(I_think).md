---
title: "Move grub file to another disk (I think)"
date: 2017-08-31
forum: General Help
---

### Post by James Wilde on 2017-08-31
My machine is running 16.04,  I have recently been experimenting with alternative distros to get rid of a) unity interface and b) the partial scroll bars which so many operating systems seem to like these days-  In the process I installed Ubuntu-Mate on a usb disk I have, and now I find that my internal disk does not appear to be bootable other than from the usb disk.  On that disk I have a grub file which shows first the Ubuntu-Mate on the usb disk and then the Ubuntu normal on the internal disk.

To get there I have to go into the bios controls to select the start-up disk.  I would like to either copy or move the grub file from the usb disk to the internal disk so that it will be possible to get to the os choice screen directly when the machine starts up.

How do I do that?

Thanks in advance for any help.

---

### Post by ajgreeny on 2017-08-31
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and will give some of our experts a chance to help you.

---

### Post by James Wilde on 2017-09-01
Thanks, AJGreeny

Here's the file from Boot-info


[https://paste.ubuntu.com/25444337/](https://paste.ubuntu.com/25444337/)

---

### Post by oldfred on 2017-09-01
Do not run Boot-Repair's auto fix. That installs one grub in all drives. You want each drive to have each drive's install's copy of grub in MBR.

The grub in sda is looking for an UUID that does not seem to exist.

But you should be able to boot sdb, and then boot into the install on sda.
The run this to install sda's grub to MBR of sda.

 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo parted -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub 

If re-installing grub from your sdb install into sda, you have to mount the sda partition.
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 


But Boot-Repair's advanced option is usually easier, just choose which install & which drive's MBR to install grub into.

You may want to run this in both installs.

 sudo apt-get autoremove  #removes dependencies no longer needed with newer Ubuntu will also remove old kernels

---

### Post by James Wilde on 2017-09-18
Sorry for the long delay.  Have had major problems in the home network which ended when I reset the router and re-installed it.  Thanks, Oldfred, for your input.  I'm now able to boot from the new drive.  Actually, to make things easier, I changed disks, so I now boot from the former usb disk, /dev/sdb, which has become /dev/sda since it is now the internal disk.  It still offers me the choice to boot from the old disk, but I don't need to now I have Ubuntu-Mate on the new internal disk working as I like.  I'm just using the old disk as a repository for all my files until I get them over to the new internal disk.

---

