---
title: "Removing disk w/ Grub on"
date: 2007-08-31
forum: General Help
---

### Post by kristianz on 2007-08-31
Hey!

When I installed Ubuntu a few weeks ago, I had my NTFS Windows drive (/dev/hdb) attached as well as the drive I installed Ubuntu on (/dev/sda). Apparently, Ubuntu decided to install Grub on the NTFS drive, which I intended to remove as soon as I had copied some files from it.

When I removed it, my computer wouldn't boot, so I re-attached it and tried to install grub on the main disk with **sudo grub-install /dev/sda**. That didn't work, it gave me a new error saying grub couldn't find the linux image to boot. I don't have the exact error messages written down, but I hope someone can point me to a solution nevertheless.

Basically: How may I physically remove the NTFS IDE drive hdb which currently has Grub on it and have Grub on the Ubuntu root drive sda?

---

### Post by ajgreeny on 2007-08-31
You will now need to boot into the live CD and restore grub, but remember that the removal of the windows disk has probably changed the disk dev naming, so with the windows disk removed, on liveCD enter sudo fdisk -l in terminal and note the name of the disk in dev/**hda1** terms.

Now make a mount point and mount the ubuntu install on that disk with
sudo mkdir /media/ubuntu
then
sudo mount /dev/**hda1** /media/ubuntu -t ext3

Now navigate to /media/ubuntu/boot/grub/menu.lst to see where it points (probably the wrong partition now) and edit the menu.lst file to point to the right partition using sudo gedit /media/ubuntu/boot/grub/menu.lst.

Remember that the **dev/hda1** will be **hd0,0** in grub terminology, **dev/hda2** will be **hd0,1** etc etc.

Now you need to reinstall grub, but this time on the only hard disk you have.  Follow the info in the attached txt file for this.

Good luck.

---

### Post by kristianz on 2007-09-07
Thanks, that worked.

I should add, in case someone else reads this looking to solve a similar issue, that the part about editing menu.lst specifically involved changing (in my case) the line that read

**# kopt=root=UUID=8ef7616f-ed1a-4545-a5c3-e6926a495222 ro**
into
**# kopt=root=/dev/sda1 ro**

(The menu.lst file is really confusing, mixing, as it does, uncommented lines with commented lines that really are comments and commented lines that aren't really commented out.)

---

