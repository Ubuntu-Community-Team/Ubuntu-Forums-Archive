---
title: "Feisty delete old_home folder"
date: 2008-02-13
forum: General Help
---

### Post by phil54601 on 2008-02-13
Hello All;
    I got an 'out of disks space' error a few days ago.   I've spent 4days reading forum posts and trying to create & switch to a new /home folder & then delete my original /home folder.  I was able to shrink /dev/sda6 and create /dev/sda8.  I used the  cpio command below to copy my /home folder to the new partition.  I edited /etc/fstab to add-mount my new partition as /home.

This is part of my /etc/fstab:
# /etc/fstab: static file system information.

# /dev/hda5  'Swap'
UUID=1f0112c7-25ff-43e0-b58f-1429607784df none            swap    sw              	0       0

#/dev/sda8 
#UUID=4aaa128b-cb5c-4b7d-b208-b08ea08e5641 /home ext3 nodev,nosuid      0       2

When I leave the last line commented out, I boot to my old /home, and when I un-comment that last line I boot to the new /home.  But it seems like I'm using both the old /home & the new one.  I've tried booting with the Ubuntu feisty live cd, and rename the old /home to /home_backup(like below), and then edit fstab for the new partition.  But when I reboot I get a series of error messages.  The first error say that /home/phil does not exist!
I had printed the guide below, but am stuck.  

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Quote from link:
Now we're going to back up the /home directory on the old partition and move it to the new partition:
cd /old/home
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home

I didn't backup /home like this, since I had just created a tgz file of /home on another partition.  Also in that block of code above isn't the line  'sudo mkdir /old/home'  out of order?  Doesn't it need to be before 'cd /old/home'?  The 'sudo mv /old/home /old/home_backup' command only renames /home doesn't it? 

Quote continued:
Next, we're going to specify to use the new home partition as /home:
sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab

......(some lines removed)
After you reboot, you should be now using your new /home partition. 
End Quote
Home is 3.5GB, I need the space.
What  am I missing or doing wrong?
Thanks
Phil

---

### Post by pointone on 2008-02-13
Please post your fstab file in full.

---

### Post by phil54601 on 2008-02-13
Hell;
The last section isn't a problem.  Those partitions are on a removeable drive (IBM ultrabay 2000, which isn't installed now.  The Win2000 & Win 98 partitions are hidden & empty, but they still mount under '/media/sda? and are on the desktop as disk1, disk2.

  Here is the fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   		<type>  	<options>            <dump>   <pass>
proc            /proc           proc    defaults        				0       0
# /dev/hda3
UUID=dace520a-fe98-4b7e-a25d-26ba4511ed89 /      ext3    defaults,errors=remount-ro 	0       1
# /dev/hda6
UUID=6149de0c-f511-487e-be78-c7089d143c46 /mnt/Linux2  ext3 defaults,uid=1000,gid=1000  0       1
# /dev/hda7
UUID=46EA-92F2   /mnt/LinWin   vfat    defaults,utf8,uid=1000,gid=1000 		0       1
# /dev/hda1 'Win2000'
#UUID=46EA-92C0  /mnt/sda1     vfat    defaults,utf8,uid=1000,gid=1000 		0       1
# /dev/hda2 'Win98'
#UUID=46EA-92C3  /mnt/sda2     vfat    defaults,utf8,uid=1000,gid=1000 		0       1
# /dev/hda5  'Swap'
UUID=1f0112c7-25ff-43e0-b58f-1429607784df none            swap    sw              	0       0

#/dev/sda8 
#UUID=4aaa128b-cb5c-4b7d-b208-b08ea08e5641 /home ext3 nodev,nosuid      0       2
# Original forum text==   nodev,nosuid 0 2 

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     				0       0
/dev/           /media/floppy0  auto    rw,user,noauto  				0       0


#	The Following is on Disk #2 (Hitachi 60GB)
/dev/sdb6  /mnt/Drv_E_on_Disk2  	vfat auto,utf8,uid=1000,gid=1000     		0       0
/dev/sdb7  /mnt/Linux_Backup     	vfat defaults,utf8,uid=1000,gid=1000 		0       1
/dev/sdb8  /mnt/Drv_2_hdc8_G 		vfat defaults,utf8,uid=1000,gid=1000     	0       0

Thanks
Phil

---

### Post by phil54601 on 2008-02-19
Hello All;
   I solved the problem by deleting the feisty installation, combining 3 partitions, and re-installing.
Thanks any way.
Phil

---

