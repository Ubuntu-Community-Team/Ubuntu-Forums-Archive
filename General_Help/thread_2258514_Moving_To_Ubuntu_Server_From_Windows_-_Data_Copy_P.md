---
title: "Moving To Ubuntu Server From Windows - Data Copy Problems"
date: 2014-12-28
forum: General Help
---

### Post by ccsnet on 2014-12-28
Hi,

Issue:
Been a Windows GUI person I'm still really getting to grips with the drive concepts and 'mounting' them.
I have about 1.4 TB of data on an external NTFS drive I want to copy to my newly created LVM.
I am assuming I can copy the folder structure from the external drive to the route of the new LVM and once there I can allocate the shares to each users data etc.

Problem 1) I can not see the data to copy although the drive has been plugged in
Problem 2) I'm not sure of the command to use to copy the data although I have found [http://ubuntuforums.org/showthread.php?t=1760718](http://ubuntuforums.org/showthread.php?t=1760718)

If there is a way to remotely mount the LVM space in the same way that I could under Windows ie \\$drive I can then remotely copy the data in over the network

```
NAME                          FSTYPE        SIZE MOUNTPOINT LABELsda                                        74.5G            
&#9500;&#9472;sda1                        ext4         69.9G /          
&#9492;&#9472;sda2                        swap          4.7G [SWAP]     
sdb                           LVM2_member 931.5G            
&#9492;&#9472;Datadrivev-Datadrive (dm-0) ext4          1.8T            
sdc                           LVM2_member 931.5G            
&#9492;&#9472;Datadrivev-Datadrive (dm-0) ext4          1.8T            
sr0                                        1024M 
```

Thanks in advance

Terran

PS I've used Ubuntu for a while as a client but this is the first time I have tried the server install ie no GUI to click on ;)

---

### Post by tgalati4 on 2014-12-28
How many different users are represented on the NTFS drive?  If it is just one or two, then *rsync* or a simple *cp* will do, but you will have to change permissions using *chmod*.

If you have many users, then simply mount the drive in /etc/fstab and send the users an email with a link pointing to the external drive and let them copy the data over.  That way, permissions are preserved.  Give them a few weeks to do it.

---

### Post by ccsnet on 2014-12-28
Not too worried about permissions tbh - and a lot of it is my data like films / music / photos etc.

Interestingly I just looked to see my external drive and I can no longer see it ( was sdh1 iirc ).... and I seem to have issues with the LVM I created....

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00053b12


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   146485247    73241600   83  Linux
/dev/sda2       146485248   156301311     4908032   82  Linux swap / Solaris


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdc doesn't contain a valid partition table


Disk /dev/mapper/Datadrivev-Datadrive: 2000.4 GB, 2000381018112 bytes
255 heads, 63 sectors/track, 243199 cylinders, total 3906994176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/Datadrivev-Datadrive doesn't contain a valid partition table


---

### Post by tgalati4 on 2014-12-28
Let's say you want to copy the data from /media/datadrive-datadrive to /home/ccsnet.  Mount the NTFS drive by putting the correct line in /etc/fstab and rebooting.

Log into the linux machine:

```
cd /media/datadrive-datadrive
cp -R /Music ~/Transfered-Music
cp -R /Photos ~/Transfered-Photos
cp -R /Vidoes ~/Transfered-Videos

```

---

### Post by ccsnet on 2014-12-28
Thanks - that was helpful.

I do have one more issue which I will log a separate post on.

T

---

