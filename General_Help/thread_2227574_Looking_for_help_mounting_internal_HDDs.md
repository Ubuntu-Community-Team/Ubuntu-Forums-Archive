---
title: "Looking for help mounting internal HDDs"
date: 2014-06-02
forum: General Help
---

### Post by dwreid55 on 2014-06-02
My apologies if this has been answered elsewhere. I did several searches and came up empty handed. 

I'm running Ubuntu 13.04. I have the boot volume and then 4 additional internal hard drives. The hard drives don't actually "mount" until I click on the icon for them in the switcher. At that time a mount point is created in /media/<user>/. However, applications can't see the drives until I manually open each one. I'd like to automatically have them mount in the same location and with the same name. There used to be a handy utility named pysdm but it no longer appears in the repositories. I've tried to find an alternative but to no avail. I did find this [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) but this page is sort of like asking how to make toast and getting an answer that explains how to invent plastic and smelt copper to make a toaster and then create a generator to supply electricity... you get the idea. I'm looking for something a bit more simple and fool proof. I tried editing the fstab but after changing one line for one of the drives I had a system that would no longer boot and had to be reloaded from scratch. I'm not anxious to do that again. 

If anyone can point me to a tool with a nice GUI that will allow me to automatically mount the drives at boot time for system wide use without first needing to click on each drive to open it and create the ephemeral mount point I'd be ever so grateful. 

Oh, and I should mention that I did find a program called "disks" that looks like it might do what I want but I can find no documentation for how to use it. That being the case, I'm a bit leery of just poking some stuff into the blanks to see what happens. 

Thanks so much. I appreciate any help you can give.

---

### Post by papibe on 2014-06-02
Hi dwreid55.

A few thoughts:

13.04 is no longer supported, I would recommend upgrading or installing the latest LTS version (14.04).

In 14.04, you can solve this issue using the pre installed application called 'Disks'. You can browse your disks and partitions, and also by pressing the little wheel, you can set the mount options.

If that functionality is not available on 13.04, or you are willing to upgrade, we would gladly help you edit your fstab in a safe way.

If you want to go this last route, please open a terminal, run these commands, and post back the results (you can copy/paste the text):
```
sudo fdisk -l

sudo blkid 

cat /etc/fstab
```
Regards.

---

### Post by dwreid55 on 2014-06-02
Wow! Thanks. I have the disks application on this install but was not sure what to poke into what blanks. I could not find documentation for it. I swear, I did look. :-) I will be upgrading soon but at the moment I have an application that is not approved for use on 14.04. As soon as the vendor gives me the thumbs up, I'll be upgrading. 

I very much appreciate the help. The results you requested are below. I've taken the liberty of also printing the current mount points. I'd like to keep them the same for the simple reason that existing applications already look for them under those names in that location.:

Thanks so much!

david@UBUNTU3:/media/david$ sudo fdisk -l


Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00030608


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   435419135   217708544   83  Linux
/dev/sda2       435421182   468860927    16719873    5  Extended
/dev/sda5       435421184   468860927    16719872   82  Linux swap / Solaris


Disk /dev/sdb: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003778d


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   468860927   234429440   83  Linux


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbb22b7ab


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bba55


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907028991  1953513472   83  Linux


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000aa198


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  1953523711   976760832   83  Linux
david@UBUNTU3:/media/david$ 

-----------------

david@UBUNTU3:/media/david$ sudo blkid
/dev/sda1: UUID="ceae5929-8c1f-4cd3-b887-07bd581ea9b5" TYPE="ext4" 
/dev/sda5: UUID="fe04b33b-0dd0-4639-bb6a-fda53b1850a9" TYPE="swap" 
/dev/sdb1: LABEL="DSK1-SSD" UUID="5fddf170-3548-42da-83c1-86e74b1593f4" TYPE="ext4" 
/dev/sdc1: LABEL="DSK2-3TB" UUID="243e018d-b75c-4edd-929a-9021a79480e7" TYPE="ext4" 
/dev/sdd1: LABEL="DSK3-2TB" UUID="ae5ba6fe-92c2-4585-9d46-bbf9b0d56025" TYPE="ext4" 
/dev/sde1: LABEL="DSK4-1TB" UUID="619acd68-c811-4d3e-b604-1771acb49366" TYPE="ext4" 
david@UBUNTU3:/media/david$ 

------------------

david@UBUNTU3:/media/david$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=ceae5929-8c1f-4cd3-b887-07bd581ea9b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fe04b33b-0dd0-4639-bb6a-fda53b1850a9 none            swap    sw              0       0
david@UBUNTU3:/media/david$ 

-------------------

david@UBUNTU3:/media/david$ ls -a -1
.
..
DSK1-SSD
DSK2-3TB
DSK3-2TB
DSK4-1TB
david@UBUNTU3:/media/david$

---

### Post by Bucky Ball on 2014-06-02
*Thread moved to **General Help**.*

---

### Post by papibe on 2014-06-02
Thanks.

First let's create the mount points, since /media/user is also used to automount external disks, I would use another location. For instance:
```
sudo mkdir /disks
sudo mkdir /disks/DSK1-SSD
sudo mkdir /disks/DSK2-3TB
sudo mkdir /disks/DSK3-2TB
sudo mkdir /disks/DSK4-1TB
```
Then, let's make a copy of the working fstab:
```
sudo cp /etc/fstab /etc/fstab.back
```
(this way, in the rarely case something goes wrong, boot into recovery mode, get a root prompt and you can recover your working fstab very easily).

Install gksudo to run GUI tools as root:
```
sudo apt-get install gksudo
```
Now edit your fstab file:
```
gksudo gedit /etc/fstab
```
go to the end of the file and add these lines:
```

# /dev/sdb1: LABEL="DSK1-SSD"
UUID="5fddf170-3548-42da-83c1-86e74b1593f4"  /disks/DSK1-SSD  ext4  defaults 0 2

# /dev/sdc1: LABEL="DSK2-3TB"
UUID="243e018d-b75c-4edd-929a-9021a79480e7"  /disks/DSK2-3TB  ext4  defaults 0 2

# /dev/sdd1: LABEL="DSK3-2TB"
UUID="ae5ba6fe-92c2-4585-9d46-bbf9b0d56025"  /disks/DSK3-2TB  ext4  defaults 0 2

# /dev/sde1: LABEL="DSK4-1TB"
UUID="619acd68-c811-4d3e-b604-1771acb49366"  /disks/DSK4-1TB  ext4  defaults 0 2
```
Save the file. DO NOT REBOOT just yet.

Open a terminal to test the mount entries:
```
sudo mount -a
```
If you see any error message, stop here, and please post the errors here. If not, check if your disks are mounted by either of these two commands:
```
sudo mount -l

df -h
```
If the disks are there, reboot and test a clean start.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by dwreid55 on 2014-06-07
First off let me say THANK YOU! You so rock. Everyone who replied to me on this forum was amazingly helpful. Papibe - your instructions were darned near perfect. I truly appreciate the time that you took to provide them. Just as an FYI, when I tried to install gksudo I received the "package not found" message from apt-get. Not a problem, I used nano in a terminal window to do the same thing. Once the reboot was complete, I fixed a few things that were looking for the disks in the old location, reshared some folders and I was up and running like a champ. 

I owe you. I truly do. I can't say "thank you" enough. 

+100 karma points.

David

---

### Post by dwreid55 on 2014-06-07
One last thing. (Isn't there always?) As you probably guessed from the disk labels, DSK1-SSD is a solid state drive. Currently I'm using cron jobs to fstrim my 2 SSDs on a daily basis with the output going to a txt file so that I can check for problems. I was told that this made for better system performance than setting the drives to auto-trim. I'd be curious to get your ideas on that. 

Thanks again.

David

---

### Post by papibe on 2014-06-07
Yes, I do the same. Here are some script examples on this other [thread]("http://ubuntuforums.org/showthread.php?t=2228143&highlight=fstrim").

Regards.

---

### Post by Bucky Ball on 2014-06-07
There are a lot of opinions regarding trim and SSDs. Suggest you have a look at the many discussions here and elsewhere and if still in doubt, post a new thread as the query has nothing to do with the title of this one. Good luck. ;)

PS: There was word that 14.04 will come with trim for SSD set up by default. You might want to look into that, too.

---

