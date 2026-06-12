---
title: "Partitioning basic setup advice"
date: 2014-05-27
forum: General Help
---

### Post by evilbrent on 2014-05-27
Hi,

I have a computer that's running Ubuntu 12.04 *ok *but it's starting to get buggy in random and obnoxious ways so I'm going to nuke it and start again. 

Can anyone tell me how to set it up so it ends up so that I can have the operating system on one partition and all the files on another? 

What I think I want is:
[LIST]
[*]Hard Disk One (1TB)
[LIST]
[*]100GB (???) Linux Ubuntu operating system
[*]830BG files including all photos and my son's Minecraft crap
[*]31GB pre-existing Windows XP version that I want to keep for mostly nostalgic reasons
[*]8GB Linux Swap file
[/LIST]

[*]Hard Disk Two (2TB)
[LIST]
[*]Auto backup of photos and wanted files / folders
[*]~1.5TB of movie/TV library (the computer functions as a media server a lot of the time).
[/LIST]
[/LIST]

What do you think? I'd love to set it up so that at any point I can wipe the ubuntu partition and not have to back up any of the files, is that possible? Just nuke the 100GB partition and start again? I read somewhere about this. How big would that partition have to be?

(Sneaky bonus question - what do you think about Ubuntu 14.04? Am I going to have fun running it on this computer? I know that even 12.04 made it groan a bit...)

I've included what I THINK is the relevant information about my system setup currently.

[HR][/HR]



[COLOR=#000000][FONT=Times New Roman]

[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"][FONT=monospace]cpu:0[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]CPU[/TD]
[/TR]
[TR]
[TD="class: first"]product:[/TD]
[TD="class: second"]AMD Athlon(tm) X4 620 Processor[/TD]
[/TR]
[TR]
[TD="class: first"]vendor:[/TD]
[TD="class: second"]Hynix Semiconductor (Hyundai Electronics)[/TD]
[/TR]
[TR]
[TD="class: first"]size:[/TD]
[TD="class: second"]2626MHz[/TD]
[/TR]
[TR]
[TD="class: first"]width:[/TD]
[TD="class: second"]64 bits[/TD]
[/TR]
[TR]
[TD="class: first"]clock:[/TD]
[TD="class: second"]200MHz[/TD]
[/TR]
[TR]
[TD="class: first"][/TD]
[TD="class: second"][/TD]
[/TR]
[TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"]cores[/TD]
[TD]=[/TD]
[TD]4[/TD]
[/TR]
[TR]
[TD="class: sub-first"]enabledcores[/TD]
[TD]=[/TD]
[TD]4[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]






[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"][FONT=monospace]memory:0[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]System Memory[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"][FONT=monospace]2b[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]slot:[/TD]
[TD="class: second"]System board or motherboard[/TD]
[/TR]
[TR]
[TD="class: first"]size:[/TD]
[TD="class: second"]4GiB[/TD]
[/TR]
[/TABLE]





[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"][FONT=monospace]disk[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]ATA Disk[/TD]
[/TR]
[TR]
[TD="class: first"]product:[/TD]
[TD="class: second"]WDC WD10EARS-00Y[/TD]
[/TR]
[TR]
[TD="class: first"]vendor:[/TD]
[TD="class: second"]Western Digital[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"][FONT=monospace]0.0.0[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]bus info:[/TD]
[TD="class: second"][FONT=monospace]scsi@0:0.0.0[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]logical name:[/TD]
[TD="class: second"][FONT=monospace]/dev/sda[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]version:[/TD]
[TD="class: second"]80.0[/TD]
[/TR]
[TR]
[TD="class: first"]serial:[/TD]
[TD="class: second"][/TD]
[/TR]
[TR]
[TD="class: first"]size:[/TD]
[TD="class: second"]931GiB (1TB)[/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]partitioned partitioned:dos[/TD]
[/TR]
[TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"]ansiversion[/TD]
[TD]=[/TD]
[TD]5[/TD]
[/TR]
[TR]
[TD="class: sub-first"]signature[/TD]
[TD]=[/TD]
[TD]000ddce7[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"][FONT=monospace]volume:0[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]EXT4 volume[/TD]
[/TR]
[TR]
[TD="class: first"]vendor:[/TD]
[TD="class: second"]Linux[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"][FONT=monospace]1[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]bus info:[/TD]
[TD="class: second"][FONT=monospace]scsi@0:0.0.0,1[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]logical name:[/TD]
[TD="class: second"][FONT=monospace]/dev/sda1[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]logical name:[/TD]
[TD="class: second"][FONT=monospace]/[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]version:[/TD]
[TD="class: second"]1.0[/TD]
[/TR]
[TR]
[TD="class: first"]serial:[/TD]
[TD="class: second"][/TD]
[/TR]
[TR]
[TD="class: first"]size:[/TD]
[TD="class: second"]891GiB[/TD]
[/TR]
[TR]
[TD="class: first"]capacity:[/TD]
[TD="class: second"]891GiB[/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized[/TD]
[/TR]
[TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"]created[/TD]
[TD]=[/TD]
[TD]2013-02-27 08:41:35[/TD]
[/TR]
[TR]
[TD="class: sub-first"]filesystem[/TD]
[TD]=[/TD]
[TD]ext4[/TD]
[/TR]
[TR]
[TD="class: sub-first"]lastmountpoint[/TD]
[TD]=[/TD]
[TD]/[/TD]
[/TR]
[TR]
[TD="class: sub-first"]modified[/TD]
[TD]=[/TD]
[TD]2014-05-26 23:23:36[/TD]
[/TR]
[TR]
[TD="class: sub-first"]mount.fstype[/TD]
[TD]=[/TD]
[TD]ext4[/TD]
[/TR]
[TR]
[TD="class: sub-first"]mount.options[/TD]
[TD]=[/TD]
[TD]rw,relatime,errors=remount-ro,data=ordered[/TD]
[/TR]
[TR]
[TD="class: sub-first"]mounted[/TD]
[TD]=[/TD]
[TD]2014-05-26 23:23:46[/TD]
[/TR]
[TR]
[TD="class: sub-first"]state[/TD]
[TD]=[/TD]
[TD]mounted[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]


[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"][FONT=monospace]volume:1[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]Windows NTFS volume[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"][FONT=monospace]2[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]bus info:[/TD]
[TD="class: second"][FONT=monospace]scsi@0:0.0.0,2[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]logical name:[/TD]
[TD="class: second"][FONT=monospace]/dev/sda2[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]version:[/TD]
[TD="class: second"]3.1[/TD]
[/TR]
[TR]
[TD="class: first"]serial:[/TD]
[TD="class: second"][/TD]
[/TR]
[TR]
[TD="class: first"]size:[/TD]
[TD="class: second"]31GiB[/TD]
[/TR]
[TR]
[TD="class: first"]capacity:[/TD]
[TD="class: second"]31GiB[/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]primary bootable ntfs initialized[/TD]
[/TR]
[TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"]clustersize[/TD]
[TD]=[/TD]
[TD]4096[/TD]
[/TR]
[TR]
[TD="class: sub-first"]created[/TD]
[TD]=[/TD]
[TD]2010-12-21 01:41:19[/TD]
[/TR]
[TR]
[TD="class: sub-first"]filesystem[/TD]
[TD]=[/TD]
[TD]ntfs[/TD]
[/TR]
[TR]
[TD="class: sub-first"]state[/TD]
[TD]=[/TD]
[TD]clean[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]


[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"][FONT=monospace]volume:2[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]Extended partition[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"][FONT=monospace]3[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]bus info:[/TD]
[TD="class: second"][FONT=monospace]scsi@0:0.0.0,3[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]logical name:[/TD]
[TD="class: second"][FONT=monospace]/dev/sda3[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]size:[/TD]
[TD="class: second"]8671MiB[/TD]
[/TR]
[TR]
[TD="class: first"]capacity:[/TD]
[TD="class: second"]8671MiB[/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]primary extended partitioned partitioned:extended[/TD]
[/TR]
[/TABLE]

[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"][FONT=monospace]logicalvolume[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]Linux swap / Solaris partition[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"][FONT=monospace]5[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]logical name:[/TD]
[TD="class: second"][FONT=monospace]/dev/sda5[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]capacity:[/TD]
[TD="class: second"]8671MiB[/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]nofs[/TD]
[/TR]
[/TABLE]





[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"][FONT=monospace]scsi:1[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"][FONT=monospace]11[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]logical name:[/TD]
[TD="class: second"][FONT=monospace]scsi1[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]emulated[/TD]
[/TR]
[/TABLE]

[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"][FONT=monospace]disk[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]ATA Disk[/TD]
[/TR]
[TR]
[TD="class: first"]product:[/TD]
[TD="class: second"]WDC WD20EARX-00P[/TD]
[/TR]
[TR]
[TD="class: first"]vendor:[/TD]
[TD="class: second"]Western Digital[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"][FONT=monospace]0.0.0[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]bus info:[/TD]
[TD="class: second"][FONT=monospace]scsi@1:0.0.0[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]logical name:[/TD]
[TD="class: second"][FONT=monospace]/dev/sdb[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]version:[/TD]
[TD="class: second"]51.0[/TD]
[/TR]
[TR]
[TD="class: first"]serial:[/TD]
[TD="class: second"][/TD]
[/TR]
[TR]
[TD="class: first"]size:[/TD]
[TD="class: second"]1863GiB (2TB)[/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]partitioned partitioned:dos[/TD]
[/TR]
[TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"]ansiversion[/TD]
[TD]=[/TD]
[TD]5[/TD]
[/TR]
[TR]
[TD="class: sub-first"]signature[/TD]
[TD]=[/TD]
[TD]0000b442[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"][FONT=monospace]volume[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]EXT3 volume[/TD]
[/TR]
[TR]
[TD="class: first"]vendor:[/TD]
[TD="class: second"]Linux[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"][FONT=monospace]1[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]bus info:[/TD]
[TD="class: second"][FONT=monospace]scsi@1:0.0.0,1[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]logical name:[/TD]
[TD="class: second"][FONT=monospace]/dev/sdb1[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]logical name:[/TD]
[TD="class: second"][FONT=monospace]/media/2TB[/FONT][/TD]
[/TR]
[TR]
[TD="class: first"]version:[/TD]
[TD="class: second"]1.0[/TD]
[/TR]
[TR]
[TD="class: first"]serial:[/TD]
[TD="class: second"][/TD]
[/TR]
[TR]
[TD="class: first"]size:[/TD]
[TD="class: second"]1851GiB[/TD]
[/TR]
[TR]
[TD="class: first"]capacity:[/TD]
[TD="class: second"]1851GiB[/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]primary journaled extended_attributes large_files recover ext3 ext2 initialized[/TD]
[/TR]
[TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"]created[/TD]
[TD]=[/TD]
[TD]2011-08-11 13:12:56[/TD]
[/TR]
[TR]
[TD="class: sub-first"]filesystem[/TD]
[TD]=[/TD]
[TD]ext3[/TD]
[/TR]
[TR]
[TD="class: sub-first"]label[/TD]
[TD]=[/TD]
[TD]2TB[/TD]
[/TR]
[TR]
[TD="class: sub-first"]modified[/TD]
[TD]=[/TD]
[TD]2014-05-26 23:24:29[/TD]
[/TR]
[TR]
[TD="class: sub-first"]mount.fstype[/TD]
[TD]=[/TD]
[TD]ext3[/TD]
[/TR]
[TR]
[TD="class: sub-first"]mount.options[/TD]
[TD]=[/TD]
[TD]rw,relatime,errors=remount-ro,barrier=1,data=ordered[/TD]
[/TR]
[TR]
[TD="class: sub-first"]mounted[/TD]
[TD]=[/TD]
[TD]2014-05-26 23:24:29[/TD]
[/TR]
[TR]
[TD="class: sub-first"]state[/TD]
[TD]=[/TD]
[TD]mounted[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]




[/FONT][/COLOR]

---

### Post by ajgreeny on 2014-05-27
What you want is certainly possible but to give you good advice we need to know in more detail what current disk and partition layout you have.

Can you show the output of the command ```
sudo fdisk -l
``` in ubuntu terminal which will be much more use than the info you have already shown.  Please enclose the output in code tags (the # in the toolbar of the reply box)

---

### Post by evilbrent on 2014-05-27
Oh, yes, that does look a lot more useful than what I provided.

What's it mean?

```
brent@Martha:~$ sudo fdisk -l
[sudo] password for brent: 


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ddce7


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1869948927   934973440   83  Linux
/dev/sda2   *  1869949935  1935752174    32901120    7  HPFS/NTFS/exFAT
/dev/sda3      1935765502  1953523711     8879105    5  Extended
/dev/sda5      1935765504  1953523711     8879104   82  Linux swap / Solaris


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0000b442


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3883585229  1941792583+  83  Linux
Partition 1 does not start on a physical sector boundary.



```

Thanks

---

### Post by ajgreeny on 2014-05-27
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1869948927   934973440   83  Linux
/dev/sda2   *  1869949935  1935752174    32901120    7  HPFS/NTFS/exFAT
/dev/sda3      1935765502  1953523711     8879105    5  Extended
/dev/sda5      1935765504  1953523711     8879104   82  Linux swap / Solaris
```
This means more or less what you thought it did.

You have on your first disk a ~950GB Ubuntu OS partition (/dev/sda1), a 32GB WinXP partition with the boot flag, needed for windows but not normally needed for linux (/dev/sda2), and an 8GB swap partition (dev/sda5) which is enclosed within the extended wrapper partition (/dev/sda3).
On disk 2 you have a single partition for all your data, which at present is not shared with WinXP, nor can it be, as it is a linux filesystem which windows can not read.

You could repartition your first disk after backing up all the files etc etc, and make a smaller OS partition for Ubuntu (about 20GB) with a separate /home partition, which is then used for all your data files and personal configuration files and folders.

How best to do this will depend to some extent on the current usage of the partitions, so can you now please show the output of the commands ```
mount
``` ```
cat /etc/fstab
``` and finally ```
df -hT
``` which will show the current mountpoints of all partitions and how much space in each is currently filled with data.

---

### Post by evilbrent on 2014-05-27
> [COLOR=#000000]On disk 2 you have a single partition for all your data, which at present is not shared with WinXP, nor can it be, as it is a linux filesystem which windows can not read.[/COLOR]

Yeah, that's fine. That drive only needs to talk to my router as a media server to the telly and tablet.

> [COLOR=#000000]You could repartition your first disk after backing up all the files etc etc, and make a smaller OS partition for Ubuntu (about 20GB) with a separate /home partition, which is then used for all your data files and personal configuration files and folders.[/COLOR]

Awesome!! The way you said it is EXACTLY what I was trying to achieve the last time I did all this partitioning, only it didn't work out how I wanted it.

```
brent@Martha:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sdb1 on /media/2TB type ext3 (rw,errors=remount-ro)
gvfs-fuse-daemon on /home/brent/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brent)

```

```

brent@Martha:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc           proc  nodev,noexec,nosuid       0  0  


# / was on /dev/sda1 during installation
UUID=1ebe4b97-567b-457a-bc83-40ef54677229   /               ext4  errors=remount-ro         0  1  


# swap was on /dev/sda5 during installation
UUID=cc7b51e8-18e0-4d07-9268-c5538a2abf73   none            swap  sw                        0  0  


#ADDED MOUNT START
#UUID=2ec2030a-5ec5-44c7-b251-a3cb78b8d853  /media/2TB      ext3  defaults                  0  2  
#ADDED MOUNT END


/dev/fd0                                    /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb1                                   /media/2TB      ext3  errors=remount-ro         0  0  

```

I should point out here that that's something drastically wrong with my installation, and it refuses to boot without "could not find drive /" and "could not find drive /tmp/2TB" and I have to hit I or F to ignore or fix, which is half of the reason for the impetus to want to reinstall. There's a chance that some of the details of the above are screwy.

```

brent@Martha:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4      878G  406G  428G  49% /
udev           devtmpfs  2.0G  4.0K  2.0G   1% /dev
tmpfs          tmpfs     398M  1.4M  396M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     2.0G  2.2M  2.0G   1% /run/shm
/dev/sdb1      ext3      1.8T  1.7T   42G  98% /media/2TB

```
Still thanking you.

---

### Post by oldfred on 2014-05-27
I am sure at 98% use even Linux has issues. It likes to hide another 5% that you do not see.
But Windows just about stops working when you get down to 10% free.

You may just need to run fsck on your Linux partitions. Was system shutdown abnormally? After a power failure or other abnormal shutdown fsck is almost always required. Run on both sdb1 & sda1.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Usually better to use UUIDs which it looks like you originally had, not device like you now have /dev/sdb1 as mount in fstab.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

I consider my 640GB drive large, so I just carve out another 20 or25GB and install the next version. Then I know what it looks like and follow some of the changes.
Also I liked this logic, another 10GB as a minimum install or 20GB on a 2TB drive is not much:
      
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by evilbrent on 2014-05-29
Thanks for that advice. I have some random and stupid hardware problems (ie I have to get the dvd-burner from THAT computer, and burn an iso disc on THAT computer, and then move the DVD player to THAT computer etc etc etc) so it took me a while to give your advice some effort.

Those commands didn't work for me once I finally managed to get the suns to align and get a working iso DVD AND a working dvd player and finally got a working liveCD of ubuntu 12.04. It said "location /dev/sdb1 doesn't exist" which was strange because I could get it to mount with nautilus just fine. Anyway, I'm going to still nuke the computer anyway. I've made all my backups etc, and I really want to have my / and /home on different partitions.

The only fun part is that I have to physically unplug my 2TB drive in order to do the installation because (see above stupid random problems) I don't have enough power inputs on the computer...................................... wait, you just gave me an idea! I'm going to use the power from a DIFFERENT computer to run the DVD player!! Excellent!

Ok, anyway, you're definitely on to something about my computer - the filesystem is definitely stuffed because my son has started just using the hard reset button when his minecraft crashes, and yes, the 2TB drive really is too full. It could all be potentially fixed by running the right couple of terminal commands by someone who knew what they're doing. I think that a fresh install will help me feel at ease that the million other random things that are going wrong will likely be fixed too.

Anyway, thanks again.

---

### Post by oldfred on 2014-05-29
Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

