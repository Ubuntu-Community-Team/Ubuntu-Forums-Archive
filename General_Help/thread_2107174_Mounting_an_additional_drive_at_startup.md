---
title: "Mounting an additional drive at startup"
date: 2013-01-21
forum: General Help
---

### Post by nickdc on 2013-01-21
It seemed straightforward enough but now I'm getting nervous and seeking help before making any changes. My pc has several internal drives, all originally installed under Windows xp. All my music is in a folder on a drive labelled 'Media'. I want it to be mounted at startup, to avoid getting annoying messages from Asunder if I go to rip a cd without having first mounted Media. I've done some research and learned that I need to edit /etc/fstab and I've installed MountManager to make that easier (and I've read the warnings associated with that too ... started getting wary). I open MountManager and because it doesn't list volume labels I'm not even sure which is the Media drive, so I open GParted to ascertain. And immediately I'm puzzled, as until now, because I was accessing all my media, including music on that drive, originally formatted under Windows as ntfs, and saving stuff to it, in Ubuntu, I naively assumed it was all going to the same place. I don't recall ever partitioning that drive, under Windows or Ubuntu. However, MountManager and GParted both seem to agree that there are several partitions on it. GParted shows the drive as /dev/sdd (698.64 GiB) There is an ntfs partition, sdd1 (348.07 GiB), label: Media (presumably Windows accessible) with a Mount Point /media/Media. It has over 100GiB unused space on it. Then there's an extended partition, /dev/sdd2, of 350.57 GiB, containing /dev/sdd5 and /dev/sdd6 (not sure of the terminology for these - logical partitions?? Are they partitions, even??) sdd5 is ext4 and sdd6 is linux-swap. Less than 10 GiB of it has been used - the stuff I've added since switching to Ubuntu?
So, a whole load of questions:

Did Ubuntu partition the drive when it installed, or did I, then suffer from amnesia?

Am I right in thinking stuff I've added since using Ubuntu will have gone into the ext4 part so won't be accessible in Windows? (Can check that myself next time I load Windows (groan!))

If I want to leave things on the drive as they are, which is the partition I need to identify in MountManager and tick the box for mounting at bootup? GParted only shows a mount point for sdd1, the ntfs partition. Is that a windows mount point, or is it the point Ubuntu uses when I access it manually?

If I want to abandon the idea of Windows access, and reclaim some of that space on sdd1, what's the best way (is there a way?) of combining sdd1 and sdd2 into a single linux area of ext4, without losing all the media (a lot more than just music) originally saved there under Windows?

Apologies for the long post, but I realise I've still so much to learn!

---

### Post by Morbius1 on 2013-01-21
In order for anyone to help you they are going to need some information. Please post the output of the following commands:

This will give you the UUID and LABEL's of all your partitions and how they are formatted:
```
sudo blkid -c /dev/null
```This will show how you are automounting your current partitions:
```
cat /etc/fstab
```And this will show what is currently mounted and where:
```
mount
```[I]
[COLOR=Blue]BTW, I don't like mountmanager or any of the other fstab editors so if it were me I'd stop using it - far too great a danger of messing things up.[/COLOR][/I]

---

### Post by ajgreeny on 2013-01-21
To add another command to Morbius1's reply, we would also find ```
sudo fdisk -l
``` output very useful, as it will show all the disks and partitions on your machine, whether mounted or not at the time you run it.  It should show the same number of partitions as the blkid command, but in a different way.

It's just an added safety point, but the last thing you want to do is delete any files or partitions by mistake.

Knowledge is power!

---

### Post by nickdc on 2013-01-21
Thanks for coming to my aid so promptly. Blimey! I didn't anticipate it getting quite so complicated ...

Here's the info you've both requested:

sudo blkid -c /dev/null 

 /dev/sda1: LABEL="System" UUID="BAD8DDF0D8DDAB41" TYPE="ntfs"  
 /dev/sda5: LABEL="Temp" UUID="15EB59726327BD91" TYPE="ntfs"  
 /dev/sda6: UUID="87dc126f-798c-4860-b136-69ac7e8ebadb" TYPE="ext4"  
 /dev/sda7: UUID="602bb3d9-5b25-4f50-ae99-0911ec4d7a3e" TYPE="swap"  
 /dev/sdb1: LABEL="AV transcode" UUID="E8503ED4503EA8E8" TYPE="ntfs"  
 /dev/sdc1: LABEL="AV Export" UUID="8CB4AB90B4AB7B7A" TYPE="ntfs"  
 /dev/sdd1: LABEL="Media" UUID="B4B8EEE2B8EEA1DA" TYPE="ntfs"  
 /dev/sdd5: UUID="fb16e6d5-ae70-456b-ade7-64bad87c07a7" TYPE="ext4"  
 /dev/sdd6: UUID="57909b38-5ac5-4201-81cc-3c215ba81b5b" TYPE="swap" 
 

cat /etc/fstab 

proc            /proc           proc    nodev,noexec,nosuid 0       0 
 UUID=87dc126f-798c-4860-b136-69ac7e8ebadb /               ext4    errors=remount-ro,user_xattr 0       1 
 UUID=602bb3d9-5b25-4f50-ae99-0911ec4d7a3e none            swap    sw              0       0 
 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 
 

 mount 

/dev/sda6 on / type ext4 (rw,errors=remount-ro,user_xattr) 
 proc on /proc type proc (rw,noexec,nosuid,nodev) 
 sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
 none on /sys/fs/fuse/connections type fusectl (rw) 
 none on /sys/kernel/debug type debugfs (rw) 
 none on /sys/kernel/security type securityfs (rw) 
 udev on /dev type devtmpfs (rw,mode=0755) 
 devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
 tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) 
 none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) 
 none on /run/shm type tmpfs (rw,nosuid,nodev) 
 binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) 
 gvfs-fuse-daemon on /home/nick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nick) 
 /dev/sdd1 on /media/Media type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096) 
 

 sudo fdisk -l 

Disk /dev/sda: 500.1 GB, 500107862016 bytes 
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x0f0e0f0d 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *          63   410621399   205310668+   7  HPFS/NTFS/exFAT 
 /dev/sda2       410621950   976768064   283073057+   f  W95 Ext'd (LBA) 
 /dev/sda5       731005758   976768064   122881153+   7  HPFS/NTFS/exFAT 
 /dev/sda6       410621952   718927871   154152960   83  Linux 
 /dev/sda7       718929920   731004927     6037504   82  Linux swap / Solaris 
  
 Partition table entries are not in disk order 
  
 Disk /dev/sdb: 200.0 GB, 200049647616 bytes 
 255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0xbdcfe60c 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdb1              63   390716864   195358401    7  HPFS/NTFS/exFAT 
  
 Disk /dev/sdc: 164.7 GB, 164696555520 bytes 
 255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0xca14ca14 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdc1              63   321669494   160834716    7  HPFS/NTFS/exFAT 
  
 Disk /dev/sdd: 750.2 GB, 750156374016 bytes 
 255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x78b5a2c4 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdd1              63   729955141   364977539+   7  HPFS/NTFS/exFAT 
 /dev/sdd2       729956350  1465147391   367595521    5  Extended 
 /dev/sdd5       729956352  1453070335   361556992   83  Linux 
 /dev/sdd6      1453072384  1465147391     6037504   82  Linux swap / Solaris
  

Where do I go from here?

---

### Post by grahammechanical on 2013-01-21
do not take me for an expert but this is what I see. 

4 disks = sda; sdb; sdc; sdd. The sd = Sata Drive and they are labelled in alphabetical order.

The boot repair printout shows that you have Ubuntu 12.04.1 on 5th partition on the first hard disk = sda5 with its swap partition on the 6th partition = sda6. Partitions are in numerical order.

Primary, Extended, Logical are all types of partition.

But the fdsk -l printout shows this

> Device Boot Start End Blocks Id System 
/dev/sdd1 63 729955141 364977539+ 7 HPFS/NTFS/exFAT 
/dev/sdd2 729956350 1465147391 367595521 5 Extended 
/dev/sdd5 729956352 1453070335 361556992 83 Linux 
/dev/sdd6 1453072384 1465147391 6037504 82 Linux swap / Solaris

That is telling me that you have another Linux file system on partition 5 of the 4th hard disk = sdd5. And a swap partition on the 6th partition of the 4th hard drive = sdd6.

Is this another operating system? Is it another Ubuntu or some other Linux distribution? Have you re-installed Ubuntu at some point and installed it into a different hard drive. Which is this MEDIA drive? Is it sdd, the 4th drive?

Have you at some point removed/deleted a Linux/Ubuntu installation but have not updated the Grub configuration files on Ubuntu 12.04.1 so you have a boot menu option to a version of Ubuntu that does not exist?

Regards.

---

### Post by nickdc on 2013-01-21
grahammechanical - thanks for this. You may not reckon yourself to be an expert, but I wish I could interpret the data the way you just have. And you're right - I'd completely forgotten when I made my original post that I do indeed have an earlier version of Ubuntu (10.04) on my machine. I installed it for a particular purpose, I don't use it very often and had momentarily forgotten about it. So far as I'm aware it works fine and grub lists it as an option, along with WinXP of course, when I boot up. But, now you point it out to me, I did install it on to that Media Drive, damn it,, as it had more space and it kept that 10.04 install completely separate from my current, daily-use install. So that complicates things. I think I might just uninstall 10.04, though I'm still interested in answers to my original questions about auto mounting, though obviously the question about how the two main partitions on that drive got created (and how to re-merge them) is now redundant: it was indeed amnesia! :oops:

---

### Post by Morbius1 on 2013-01-21
Let's take the original problem concerning the "Media" partition:
>   /dev/sdd1: LABEL="Media" UUID="B4B8EEE2B8EEA1DA" TYPE="ntfs"  [1] Unmount the partition:
```
sudo umount /media/Media
```[2] Create a permanent mount point:
```
sudo mkdir /media/Media
```[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```[4] Add the following line to the end of fstab
```
UUID=B4B8EEE2B8EEA1DA /media/Media ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```[5] Save the file and run the following command which will test for any syntax errors and if there are none mount the partition without requiring a reboot:
```
sudo mount -a
```Now go to /media/Media and verify that everything is where it should be.

---

### Post by nickdc on 2013-01-21
Thanks Morbius1, you're a star! Those five steps have done the trick; thank you so much.

Presumably if I do decide to take Ubuntu 10.04 off that disc, once it's uninstalled I'll be able to revert to a single partition, using GParted if the uninstall process hasn't done it automatically?

---

