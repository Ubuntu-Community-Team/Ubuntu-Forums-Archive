---
title: "Issues with hard drives"
date: 2015-07-22
forum: General Help
---

### Post by ryantrappy on 2015-07-22
Hello all I am running ubuntu server 14.04 trusty and I am having memory issues.  As of right now I have two external hard drives attached to my computer, both 1tb and then also another 1tb internal hard drives that I thought for some reason I should create an lvm of 30gb for the operating system even though I have no experience with them at all.  So here is my fdisk -ls, I am sorry it is very long.  The vg_swap I want to mount/create a link at /media/foldername and when I create the link and check the size of even /vg_swap it says it is 3gb for some reason. I also included the df -h in case that would also be helpful.  Thanks in advance
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000171f4


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1953523711   976510976   8e  Linux LVM


Disk /dev/mapper/trappserver--vg-root: 11.7 GB, 11697913856 bytes
255 heads, 63 sectors/track, 1422 cylinders, total 22847488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/trappserver--vg-root doesn't contain a valid partition table


Disk /dev/mapper/trappserver--vg-swap_1: 988.2 GB, 988245131264 bytes
255 heads, 63 sectors/track, 120147 cylinders, total 1930166272 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/trappserver--vg-swap_1 doesn't contain a valid partition table


Disk /dev/sdb: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc62bece6


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953525104   976762521    b  W95 FAT32


Disk /dev/sdc: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcacfd609


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63  1953520127   976760032+   b  W95 FAT32
```
```
   Device Boot      Start         End      Blocks   Id  System/dev/sdc1   *          63  1953520127   976760032+   b  W95 FAT32
trappserver@trappserver:~$ df -h
Filesystem                        Size  Used Avail Use% Mounted on
/dev/mapper/trappserver--vg-root   11G  9.0G  1.2G  89% /
none                              4.0K     0  4.0K   0% /sys/fs/cgroup
udev                              3.8G  8.0K  3.8G   1% /dev
tmpfs                             772M  1.4M  771M   1% /run
none                              5.0M     0  5.0M   0% /run/lock
none                              3.8G   80K  3.8G   1% /run/shm
none                              100M   12K  100M   1% /run/user
/dev/sda1                         236M   38M  186M  17% /boot
/dev/sdb1                         932G  822G  110G  89% /media/externals
```

---

### Post by Bucky Ball on 2015-07-22
You are having problems with your memory? Memory is RAM. Do you mean you are having problems with your hard drives??? :-k

---

### Post by oldfred on 2015-07-22
The main advantage of LVM is ease of changing partitions. It normally is a full drive or even more than one drive install. But adds another layer of complication as it is software logical partitions inside the physical partitions. And then different tools and ways to do things.

I do not know nor use LVM. Link below is from a user who uses it for some systems and seems to like it.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

### Post by ryantrappy on 2015-07-22
Yes lol sorry my bad wasn't really thinking!

Also oldfred do you know if there is any way other than complete format to get rid of it or make it mimic a normally partitioned drive?

---

### Post by bab1 on 2015-07-23
> **ryantrappy said:**
> Hello all I am running ubuntu server 14.04 trusty and I am having memory issues.  As of right now I have two external hard drives attached to my computer, both 1tb and then also another 1tb internal hard drives...

So you have 3TB of storage available.  Looking at your dh -h listing shows that the partitions on the drives are NOT mounted (see **[COLOR="#FF0000"]red[/COLOR]** below).
> 

```
   Device Boot      Start         End      Blocks   Id  System/dev/sdc1   *          63  1953520127   976760032+   b  W95 FAT32
trappserver@trappserver:~$ df -h
Filesystem                        Size  Used Avail Use% Mounted on
/dev/mapper/trappserver--vg-root   11G  9.0G  1.2G  89% /
none                              4.0K     0  4.0K   0% /sys/fs/cgroup
udev                              3.8G  8.0K  3.8G   1% /dev
tmpfs                             772M  1.4M  771M   1% /run
none                              5.0M     0  5.0M   0% /run/lock
none                              3.8G   80K  3.8G   1% /run/shm
none                              100M   12K  100M   1% /run/user
/dev/sda1                         236M   38M  186M  17% /boot
[COLOR="#FF0000"]**/dev/sdb1                         932G  822G  110G  89% /media/externals**[/COLOR]
```

... I thought for some reason I should create an lvm of 30gb for the operating system even though I have no experience with them at all. 

LVM seems to be a mystery to folks that don't use it all the time.  It is useful to understand the various terms used.  In Linux speak a "drive" is the physical device (e.g. the HDD).  A partition is a section of the HDD storage area.  I can be the whole drive but it does not need to be.  For example.  I have a machine that has a 30GB partition on a 700GB HDD (roughly).  There is a second partition on that HDD that is 670GB.  That machine also has a 1TB HDD that has one partition of approximately 1TB.  I can combine the two unused partitions using LVM.  This abstraction now looks like one large partition of 1.67 TB.

The LVM volume spans the partitions you add to it.  There is no way to remove the LV and leave the 30GB partition intact.  You can remove partitions from a VG with no problems until you either run out of storage space for your data or there is only one partition in the VG.

In your case I would think you should start over completely.  Bear in mind that there is no need for LVM if you only have one partition in the VG.  I do use LVM to combine partitions on separate HDD's so that the user sees only one large partition.  Never for the operating system partition.  I see that you have also attempted to have a separate boot partition (/boot).  There is no need for that on a typical Ubuntu install.  I recommend something like this ```

sda1=/ (30GB)
sda2=swap (1.5xRAM (max 4GB))
sda3=/home (whatever size you need or is left)

All other disks (sdb, sdc, etc) can be partitioned for use in a LVM if you like

``` 

Once you have created the LV you can mount it whereever you like as a singular partition as that is what it will look like. 

Explain exactly what you are attempting to do and I will provide you with more information if you like.

---

### Post by bab1 on 2015-07-23
> **oldfred said:**
> The main advantage of LVM is ease of changing partitions. It normally is a full drive or even more than one drive install. But adds another layer of complication as it is software logical partitions inside the physical partitions. And then different tools and ways to do things.

This is not really how you should look at what LVM is.  I wouldn't call it "logical partitions inside physical partitions"; more like one logical volume of multiple partitions that can be mounted as a single volume (container/partition).  So it can be said that its usefulness It is to aggregate partitions of any size into a single volume (it spans partitions).  It is indeed a waste of time if you only have one partition or one disk with multiple partitions. 
> 

I do not know nor use LVM. 
:-(

---

### Post by ryantrappy on 2015-07-23
What if I simply had two lvms on the disk and had one of roughly 30gb and the other of everything else? Is that possible? I am sorry but I am trying to avoid completely wiping my system.. Also thanks a ton for the explanation I think I understand it! This is the last time I blindly follow an internet tuturial without first understanding what I am doing! Also I did a mount -l and it does say that both my externals are mounted which is confusing as it does not seem as though they are (drives name photos and photos back)

```
trappserver@trappserver:~$ mount -l/dev/mapper/trappserver--vg-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot type ext2 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/dev/sdb1 on /media/externals type vfat (rw) [PHOTOS BACK]
/dev/sdc1 on /media/externals type vfat (rw) [PHOTOS]
```

---

### Post by bab1 on 2015-07-23
> **ryantrappy said:**
> What if I simply had two lvms on the disk and had one of roughly 30gb and the other of everything else? Is that possible? I am sorry but I am trying to avoid completely wiping my system.. Also thanks a ton for the explanation I think I understand it! This is the last time I blindly follow an internet tuturial without first understanding what I am doing! Also I did a mount -l and it does say that both my externals are mounted which is confusing as it does not seem as though they are (drives name photos and photos back)

```
trappserver@trappserver:~$ mount -l

/dev/mapper/trappserver--vg-root on / type ext4 (rw,errors=remount-ro)

/dev/sda1 on /boot type ext2 (rw)

/dev/sdb1 on /media/externals type vfat (rw) [PHOTOS BACK]

/dev/sdc1 on /media/externals type vfat (rw) [PHOTOS]
```

The root partition is only 11GB in size.  The minimum should be 20GB.  As you can see you have already filled almost 90%```
/dev/mapper/trappserver--vg-root   11G  9.0G  1.2G  [COLOR="#FF0000"]**89%**[/COLOR] /
```

I have never used LVM with vfat formatted drives.  I'm not sure that it will even work.  Do you have a backup of your data in your /home/$USER directories?  Sometimes its better to bite the bullet early on and get it straight.  It won't be any easier later on.  In fact it will only get worse.

Can you have multiple LV?  Yes, but in your case; to what end?

Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup!

The OS is easy to install, the data can be restored from the backed up data.

---

### Post by ryantrappy on 2015-07-23
Lucky since I have all my data on those two externals the only thing that is on that lvm is the operating system.  So I would have to reinstall all my programs but I guess it is better to do that and have everything correct the first time rather than try and fight through it.  Thanks for the help and I think I will just restart

---

### Post by bab1 on 2015-07-23
> **ryantrappy said:**
> Lucky since I have all my data on those two externals the only thing that is on that lvm is the operating system.  So I would have to reinstall all my programs but I guess it is better to do that and have everything correct the first time rather than try and fight through it.  Thanks for the help and I think I will just restart

Think for a second about what you want to do.  How big is the HDD you are going to put the OS on?  As I said before I think that you should have 3 partitions on with a basic install.  20GB for the root partition (/) and 2x the amount of RAM for swap and the rest for the /home partition.

---

### Post by ryantrappy on 2015-07-23
Wait why would I need a partition for swap? Sorry

---

### Post by bab1 on 2015-07-23
> **ryantrappy said:**
> Wait why would I need a partition for swap? Sorry

It depends on how you use the system.  Some of the needs are due to how much RAM you have and/or whether you use the "suspend" suspend functionality.

---

### Post by ryantrappy on 2015-07-23
It's just a basic media server and it has plenty of RAM to deal with that so would it still be necessary? Sorry if these are dumb questions

---

### Post by oldfred on 2015-07-24
I always suggest some like 2GB. 
But some with lots of RAM have said it works without swap.

 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

