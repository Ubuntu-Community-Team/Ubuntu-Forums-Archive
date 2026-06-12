---
title: "md software RAID issues after upgrading from 2.6.24-17 to 2.6.24-19"
date: 2008-06-28
forum: General Help
---

### Post by J3anyus on 2008-06-28
Hey everyone,

I'm having some strange issues with my software RAID 5 ever since upgrading to the most recent kernel.  I've done several kernel upgrades before this one and haven't had any problems, so I'm not sure what's going wrong here.  I was out of the country for awhile and missed kernel 2.6.24-18, so I skipped from 2.6.24-17 to 2.6.24-19.

I have a non-RAID'd drive that I'm using to store the OS, homedirs, and the basic stuff.  I then have a RAID 5 array of three 320GB drives that I'm using for storage. Anyway, the basic issue is that md is failing to assemble the array at boot.  If I boot back into 2.6.24-17, then everything works flawlessly.

Here's what everything looks like in 2.6.24-17:

```
jake@ridley:~$ uname -a
Linux ridley 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

jake@ridley:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb1[0] sdd1[2] sdc1[1]
      625137152 blocks level 5, 128k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>

 jake@ridley:~$ mount | grep md
/dev/md0 on /storage2 type ext3 (rw)
```

In 2.6.24-19, right at the beginning of boot (during the 'Loading hardware drivers' phase), I see these error messages:

```
md: could not bd_claim sdd1
md: could not bd_claim sdd1
shpchp: shpc_init: cannot reserve MMIO region
```

The boot then hangs at those messages for 3-4 minutes, and then I see [fail] in red text.  The machine continues trying to boot, but fails at 'Checking file systems' with these errors:

```
fsck.ext3: Device or resource busy while trying to open /dev/sda3
Filesystem mounted or opened exclusively by another program?
fsck.ext3: Invalid argument while trying to open /dev/md0
/dev/md0:
The superblock could not be read or does not describe a correct ext2 filesystem.
fsck died with exit status 8
* File system check failed
```

At this point it drops me to a root shell, where I can do some poking around:

```
root@ridley:~# uname -a
Linux ridley 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

root@ridley:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdd1[2](S)
      312568576 blocks
      
unused devices: <none>
```

Running mount shows that none of the RAID volumes are mounted anywhere, and cat /etc/fstab shows that they're not trying to be mounted anywhere.

If I run this command, the RAID array gets assembled properly and I can then mount it without any trouble:

```
mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1
```

After I do that, dmesg shows about a million of these:

```
[ 1016.410711] md: array md0 already has disks!
[ 1016.414061] md: array md0 already has disks!
[ 1016.417374] md: array md0 already has disks!
[ 1016.420696] md: array md0 already has disks!
[ 1016.423928] md: array md0 already has disks!
[ 1016.427186] md: array md0 already has disks!
[ 1016.430434] md: array md0 already has disks!
[ 1016.433728] md: array md0 already has disks!
[ 1016.437078] md: array md0 already has disks!
[ 1016.440386] md: array md0 already has disks!
[ 1016.443715] md: array md0 already has disks!
[ 1016.446984] md: array md0 already has disks!
```

And then this:

```
[ 1016.573980] md: md0 stopped.
[ 1016.573992] md: unbind<sdd1>
[ 1016.573996] md: export_rdev(sdd1)
[ 1016.577587] md: bind<sdc1>
[ 1016.577812] md: bind<sdd1>
[ 1016.577988] md: bind<sdb1>
[ 1016.816121] raid5: device sdb1 operational as raid disk 0
[ 1016.816124] raid5: device sdd1 operational as raid disk 2
[ 1016.816126] raid5: device sdc1 operational as raid disk 1
[ 1016.816383] raid5: allocated 3170kB for md0
[ 1016.816385] raid5: raid level 5 set md0 active with 3 out of 3 devices, algorithm 2
[ 1016.816387] RAID5 conf printout:
[ 1016.816388]  --- rd:3 wd:3
[ 1016.816389]  disk 0, o:1, dev:sdb1
[ 1016.816391]  disk 1, o:1, dev:sdc1
[ 1016.816392]  disk 2, o:1, dev:sdd1
```

Soooo...I can work around this issue by manually assembling the array from the root shell every time I boot, but I'd rather find the real issue here and fix it.

Any suggestions?  Thanks for all the help :D

---

### Post by fjgaude on 2008-06-28
Show us your 

```
gksu gedit /etc/fstab
```

file. That might say something... after you have manually assembled and mounted the array what does 

```
sudo mdadm -D /dev/md0
```

show?

I've been running the same array from about 2.6.18 or before without issues...

---

### Post by J3anyus on 2008-06-28
> **fjgaude said:**
> Show us your 

```
gksu gedit /etc/fstab
```

file. That might say something... after you have manually assembled and mounted the array what does 

```
sudo mdadm -D /dev/md0
```

show?

I've been running the same array from about 2.6.18 or before without issues...

Sure thing :)

```
jake@ridley:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8e62d342-734b-47ba-9940-c326e25e80ce /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda3
UUID=7f023c51-a88c-4910-89ef-cb3c8c6cf349 /storage1       ext3    relatime        0       2
# /dev/hda2
UUID=c259d88c-eb37-4fac-9f8d-f31b0a0696f3 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/md0	/storage2	ext3	defaults	0	2
```

And:

```
jake@ridley:~$ sudo mdadm -D /dev/md0
[sudo] password for jake: 
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat May  3 01:10:12 2008
     Raid Level : raid5
     Array Size : 625137152 (596.18 GiB 640.14 GB)
  Used Dev Size : 312568576 (298.09 GiB 320.07 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jun 28 15:34:44 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : 3d5a9baf:c41f3ecf:8df8c997:5044aebc (local to host ridley)
         Events : 0.16

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
```

---

### Post by fjgaude on 2008-06-28
Well, everything looks good... if you can run fsck on /dev/md0, with it **unmounted**, I guess we will know if you have a bad disk or two in the array. Please never use fsck on a mounted drive or array. Bad, bad...

Even though the -D command shows everything as okay, it only reads the superblocks and they are all okay. The fact that you can't get through the normal boot fsck points to bad drive or two.

I've seen, heard of so many bad Seagates in the last four or so months... can't say for sure but I think Seagate has let out some bad drives and the dealers are selling them.

---

### Post by J3anyus on 2008-06-29
I'm 99% sure this isn't a problem caused by a failing drive, because this issue always happens when I boot into 2.6.24-19 and never happens when I boot into 2.6.24-17.  That makes me almost certain that this is a software/configuration issue.

Also, I mentioned earlier that if I manually run mdadm --assemble when I get dropped to a root shell during boot, I'm able to assemble and mount the array without any problems.  However, I just realized that this doesn't always work - I have to try the same command several times before it finally works.  Here's what happens:

```
root@ridley:~# mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: cannot open device /dev/sdc1: Device or resource busy
```

That happens a few times, and after I've run that exact same mdadm --assemble command enough times, the array actually assembles, mounts, and works properly.  This combined with the bd_claim error indicate that something else has the partitions on my RAID drives opened, but mount, df, my fstab, and lsof don't show anything related to those partitions.

Any other ideas?

Thanks! :)

---

### Post by fjgaude on 2008-06-30
Okay, but strange... I can't think of anything else to do. Maybe someone else has seen this situation and has an idea of how to solve it.

If you can run fsck successfully on the array, unmounted, in -17 kernel, I just don't have a clue.

Good luck!

---

### Post by J3anyus on 2008-07-01
Bump.

---

### Post by fjgaude on 2008-07-01
Okay, just thought of something else. You might try failing, removing, and then adding that drive back into the array:

```
sudo mdadm /dev/md0 -f /dev/sdd1 -r /dev/sdd1 -a /dev/sdd1
```

You can do it in one command as shown.

Let us know what happens.

---

### Post by lil_elvis2000 on 2008-07-01
I am having similar issues, but only after a cold boot. and it happened in -17 and -19.

Essentially the RAID doesn't start and my boot drive containing the OS, swap etc.. also doesn't fully mount. Only two of the partitions are mounted. And...the device names for the hard drives are changed.

sda -> sdc (boot)
sdb -> sda?
sdc -> sdb?

During the boot when I am dropped in to the shell.
  I just type sudo mdadm --run /dev/md3
the array starts. I can then mount -a and all partitions are mounted and can continue the boot of the system.

   Celeron 766Mhz, 640MB ram, 1Gig IDE disk (boot disk, OS, etc..)
    2x320Gig SATA disks (/home) .. PCI SATA card (SiL 3512)

I am not useing the fakeRAID capabilities. For now I just keep it on 24/7.

---

### Post by lil_elvis2000 on 2008-07-02
I think there is one of two solutions to this problem:
 place break=mount in your GRUB menu
or add a sleep into the boot process just before the mount process

look at this and see if this helps:
[https://bugs.launchpad.net/ubuntu/+bug/104790/comments/2](https://bugs.launchpad.net/ubuntu/+bug/104790/comments/2)

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/79204](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/79204)

good luck.

---

