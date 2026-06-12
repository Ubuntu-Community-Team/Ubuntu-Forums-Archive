---
title: "[SOLVED] The Disk Drive Is Not Ready Yet Or Not Present??"
date: 2013-06-30
forum: General Help
---

### Post by Akacheebe on 2013-06-30
[SIZE=3][FONT=times new roman]I've got a mount problem that I didn't have until I reloaded sda1, which contains Windows XP x64.  Before this all 5 of my hard drives would auto mount at boot and I was able to share their contents on my network.  After the reload of sda1 I now get the following error at boot up "The disk drive for /media/sda1 is not ready or not present" and have to press "s" to continue booting.  

After boot up, that drive is visible in home menu but I'm not able to access it at all getting this error, "Error mounting: mount exited with exit code 1: helper failed with: mount: only root can mount /dev/sda1 on /media/sda1"??  

Since all these drives were configured using NTFS Configuration tool when Ubuntu 12.04-2 was loaded a few months back I tried to reconfigure that sda1 for auto mount again but it's a no go.  I also went into SAMBA setup and reconfigured that drive there and it still won't auto mount at boot and it's NOT accessible at all even from Ubuntu.  NOTHING I've tried has worked so far.  

When I go to Disk Utility and try to mount it there I get the following error, "Error mounting: mount exited with exit code 1: helper failed with:  mount: only root can mount /dev/sda1 on /media/sda1" which is the same error I get when I try to access it from "home".

I ran chkdisk /r on that Windows partition and it passed but in Ubuntu Disk Utility it gives the drive a green dot in SMART status and notes that it has a "few bad sectors".  I wasn't having any problems with the Windows load.  The reason for the reload was that the system had been on that drive for about 6 or 7 years and I just did a reload before anything serious showed up.  

So can someone tell me how to fix this issue?  I've done a couple of searches on here but nothing I've found in those threads works for me.  Here is some info that is probably needed in order to see what's going on.

EDIT:  I just booted on a Ubuntu live CD and I WAS able to access that sda1 drive??  But STILL not able to access it from Ubuntu 12.04 that I'm running now?

***UPDATE:  THIS PROBLEM WAS CAUSE BY ME WHEN I CONFIGURED SDA1 FROM SAMBA.  POST #25 WILL EXPLAIN WHAT I DID AND HOW I FIXED IT.***



```
xxxx@ubuntu-shop:~$ sudo fdisk -l
[sudo] password for xxxx: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde73de73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   163846934    81923436    7  HPFS/NTFS/exFAT
/dev/sda2       163846935   976768064   406460565    f  W95 Ext'd (LBA)
/dev/sda5       163846998   976768064   406460533+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45bf45be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    93064544    46532241    7  HPFS/NTFS/exFAT
/dev/sdb2        93128805  1953520064   930195630    5  Extended
/dev/sdb5        93128869  1953520064   930195598    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x96cea8d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   488392064   244196001    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc38688a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048    39872511    19935232    7  HPFS/NTFS/exFAT

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7e61057

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63   163766609    81883273+   7  HPFS/NTFS/exFAT
/dev/sde2       163766610   488392064   162312727+   f  W95 Ext'd (LBA)
/dev/sde5       163766673   488392064   162312696    7  HPFS/NTFS/exFAT

Disk /dev/sdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00078df7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *        2048   147916799    73957376   83  Linux
/dev/sdf2       147918846   156301311     4191233    5  Extended
/dev/sdf5       147918848   156301311     4191232   82  Linux swap / Solaris
xxxx@ubuntu-shop:~$ 





xxxx@ubuntu-shop:~$ sudo blkid
[sudo] password for xxxx: 
/dev/sda1: UUID="3694FEA494FE6631" TYPE="ntfs" 
/dev/sda5: UUID="8088B7CE88B7C148" TYPE="ntfs" 
/dev/sdb1: UUID="7A14AC1D14ABDB01" TYPE="ntfs" 
/dev/sdb5: UUID="CFF510FDBBF04069" TYPE="ntfs" 
/dev/sdc1: UUID="A8AA14ACAA1478D0" TYPE="ntfs" 
/dev/sdd1: UUID="B6FA0D8EFA0D4BD5" TYPE="ntfs" 
/dev/sde1: UUID="B234158534154DAB" TYPE="ntfs" 
/dev/sde5: LABEL="Local Disk" UUID="8088B7CE88B7C148" TYPE="ntfs" 
/dev/sdf1: UUID="7ea56b88-7e9d-4f83-badd-664e84bfa0f7" TYPE="ext4" 
/dev/sdf5: UUID="59b68caa-460e-43a4-864c-c248768a8273" TYPE="swap" 



xxxx@ubuntu-shop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdf1 :
UUID=7ea56b88-7e9d-4f83-badd-664e84bfa0f7    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=3694FEA494FE6631    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sda5    /media/sda5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb1 :
UUID=7A14AC1D14ABDB01    /media/sdb1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb5 :
UUID=CFF510FDBBF04069    /media/sdb5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdc1 :
UUID=A8AA14ACAA1478D0    /media/sdc1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdd1 :
UUID=B6FA0D8EFA0D4BD5    /media/sdd1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sde1 :
UUID=B234158534154DAB    /media/sde1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sde5    /media/sde5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
UUID=F0302D81302D5040    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdf5 :
UUID=59b68caa-460e-43a4-864c-c248768a8273    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0
xxxx@ubuntu-shop:~$ 
```

[/FONT][/SIZE]

---

### Post by Bashing-om on 2013-06-30
Akacheebe; Hi !

As you "reloaded" sda ... recon the UUID of the drive changed ? Check
```
sudo blkid
cat /etc/fstab
``` and insure the UUIDs are same same.

[INDENT][INDENT]just what I think[/INDENT][/INDENT]

---

### Post by ajgreeny on 2013-06-30
I'm not sure if this is anything to do with your problem, but if you have perhaps updated to 12.10 or 13.04 I believe disks are normally mounted to /media/<user>/mountpoint thugh p[erhaps that is only removable usb attached devices; I am still on 12.04 so am not totally sure about this.

Your UUIDs seem to match as they should, so it is a bit baffling to me!

---

### Post by Bashing-om on 2013-06-30
Akacheebe & aj...........
I guess I must have been to hasty ..perceives only what I was lookin for;  and initially missed that ! Apology to OP in order. Yeah All I can think of presently is check that mount point... and see what results when mounting sda1 manually ? If a failure manually, may give us more info on the errors generated in terminal.

[INDENT][INDENT]regards[/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-06-30
FYI, I'm not real good with command line stuff.  All that info I posted up the page came from command like stuff I had read in other threads so I figured I needed to run those and post that info here.  OK so can someone tell me the command line to mount that disk manually in terminal then?  

Just so you guys know and understand this, that drive in question is a 500 GB drive that is divided into 2 partitions.  The primary (boot) partition is around 84GB and the rest is a storage D: drive and BTW, I am able to access that D: partition from Ubuntu and also from my network.  Both partitions are NTFS.  

Thanks

---

### Post by Bashing-om on 2013-06-30
Akacheebe; Hey ..
Ok.. Let's take this approach, As you know we must have a mount point,
Does it exist ?
```
ls -la /media/
```
Is it viable ?
```
ls -la /media/sda1
```
Post those outputs so we see what the system has to say.
Now let us establish a new mount mount (uncontaminated):
```
sudo mkdir /mnt/test
```
Relinguish the old mount point:
```
sudo umount /media/sda1
```
Mount sda1 to the new mount point:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt/test
```
And now lets see that you have access to sda1:
```
ls -la /mnt/test
ls -la /mnt/test/<some-directories>/

```
and when done looking and whatever operation one has completed; un mount ***IMPORTANT****
```
sudo umount /mnt/test

```

Now what do we know ?

[INDENT][INDENT]it is only a process[/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-07-01
[SIZE=4][FONT=times new roman]Here's the output from the first two commands.
[/FONT][/SIZE]
```
xxxx@ubuntu-shop:~$ ls -la /media/
total 136
drwxr-xr-x 11 root root  4096 Jul  1 09:30 .
drwxr-xr-x 24 root root  4096 Jun 14 12:25 ..
-rw-r--r--  1 root root    95 Jun 30 13:47 .created_by_python-fstab
lrwxrwxrwx  1 root root     7 May  6 11:10 floppy -> floppy0
drwxr-xr-x  2 root root  4096 May  6 11:10 floppy0
drwxr-xr-x  2 root root  4096 May  6 13:21 sda1
drwxrwxrwx  1 root root 32768 Jun 30 10:49 sda5
drwxrwxrwx  1 root root  8192 Jun 30 10:49 sdb1
drwxrwxrwx  1 root root 12288 Jun 30 10:49 sdb5
drwxrwxrwx  1 root root 12288 Jun 30 11:18 sdc1
drwxrwxrwx  1 root root  8192 Jun 30 10:49 sdd1
drwxrwxrwx  1 root root 16384 Jun 30 10:49 sde1
drwxrwxrwx  1 root root 28672 Jun 30 10:49 sde5


xxxx@ubuntu-shop:~$ ls -la /media/sda1
total 8
drwxr-xr-x  2 root root 4096 May  6 13:21 .
drwxr-xr-x 11 root root 4096 Jul  1 09:30 ..
xxxx@ubuntu-shop:~$ 
```

[SIZE=4][FONT=times new roman]And yes, I was able to access the cboggs folder on that drive during this test.  Now how do we fix it? [/FONT][/SIZE]:confused:[SIZE=4][FONT=times new roman] 

Thanks
[/FONT][/SIZE]
```
xxxx@ubuntu-shop:~$ ls -la /mnt/test/cboggs/
total 4208
drwxrwxrwx 1 root root   4096 Jun 29 15:09 .
drwxrwxrwx 1 root root  12288 Jun 30 18:50 ..
-rwxrwxrwx 2 root root 435200 Nov 22  2010 head 001.jpg
-rwxrwxrwx 2 root root 423345 Nov 22  2010 head 002.jpg
-rwxrwxrwx 2 root root 429088 Nov 22  2010 head 003.jpg
-rwxrwxrwx 2 root root 422446 Nov 22  2010 head 005.jpg
-rwxrwxrwx 2 root root 430617 Nov 22  2010 head 006.jpg
-rwxrwxrwx 2 root root 431008 Nov 22  2010 head 007.jpg
-rwxrwxrwx 2 root root 423900 Nov 22  2010 head 008.jpg
-rwxrwxrwx 2 root root 426911 Nov 22  2010 head 009.jpg
-rwxrwxrwx 2 root root 416803 Nov 22  2010 head 010.jpg
-rwxrwxrwx 1 root root 427549 Nov 22  2010 head4.jpg
xxxx@ubuntu-shop:~$ 

```

---

### Post by Bashing-om on 2013-07-01
Akacheebe; .... 

All of your mounts are owned by root ,,, and not by you .... Maybe what you want for security reasons ... but sure can be a challenge to make it accessable by you as a "user"...
What is going to have to be done as the partitions are NTFS is to set up those access permissions in the mount directive in /etc/fstab.
Please bear with me ... I have not been associated with Windows in years and have no access to Windows for a testing platform, thus I will have to research the proper format of the mounting to achieve your stated goal.
See:
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)
As of now .. We know your data exist .. and it is available to "root"..........An alternate mount point has no problem with that partition as "root"......So,
All of your mounts are owned by root and I ask: What means are you employing to access the other drives/partitions ? Which leads to the question as to why you are only seeing a problem with sda1 ? ...If there is no difference in what/how between any of the drives/partitions and there is only a problem with sda1 then I would question the integrity of that mount point and (re-)create it. Or, as another thought ... is some other process attempting to access sda1 before it is mounted and ready to be accessed ? ... suggesting that you take a look at your start-up scripts and verify nothing is racing onto sda1.

[INDENT][INDENT]it's in the process[/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-07-01
OK just so you know, OS prober is disabled in Grub as I select my boot device via BIOS.  I had too many problems early on with Grub writing to my 'Windows drives and screwing the boot sector up so now I don't let Grub do anything on this system as far as multi-boot goes.

This version of Ubuntu was just loaded on this computer about 2 or 3 months ago after I screwed up the other install trying to update the kernel to 3.5.  After the Ubuntu reinstall and OS prober disable I then connect up the other drives and boot to Ubuntu.  Then I use NTFS Configuration tool to make the drives read and write capable for everyone then SAMBA is used to make them available on my network.  

All this has been working fine up until I did the reload on sda1 the other day and it's been down hill since then as far as that partition is concerned.  All the rest of the drives/partitions are available as they were before the reload of sda1.

And yes I saw where the read and write permissions were not the same for sda1 as they are for the other partitions?  

This is getting to a point where if I can just get the mount failure notice to stop at boot up I could care less if that drive is available or not since I don't save anything I need to share on that partition anyway.  So can I edit fstab and remove any reference to sda1 so it's not a hindrance to the system booting?  

Thanks

---

### Post by Bashing-om on 2013-07-01
Akacheebe;

Not a problem at all to take out the auto-mount of sda1 from /etc/fstab ... one could still mount that drive on-demand from the terminal anytime that access was wanted... it might prove of interest to find out the cause of the problem. It is only of general interest on my part to determine it... For the sake of expediency just place a # at the start of that line referencing sda1 ... and it will no longer be processed.

Always a good idea to make a backup of the file prior to editing... never can foresee what might happen during the edit... power failures happen !

We can always at a later time edit out that "#" and trouble shoot this issue at a more opportune time. It is your system .. what you want to do is what we will do.

At this time ... would not take much just to remove the current mount point in /media/sda1 and "mkdir" once more and see if that resolves the problem ???? But if this machine is on production ... do not want any down time !

[INDENT][INDENT][INDENT]My regards[/INDENT][/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-07-01
Bashing thanks for your help and no, this isn't any sort of production box.  So if you want to keep at it then tell me what to do next.  I just didn't want to trouble you any more with it but if you're like me, there comes a point where stuff like this gets personal!!  ;)

---

### Post by Bashing-om on 2013-07-01
Akacheebe;

What can I say ... I am glad to help ... that is a main reason I am here ...But please keep in mind I am no longer Windows' literate, and have no desire to be so ... I left Windows behind with XP(SP3) and have never looked back. I can and will assist you in determining why, in mounting the NTFS sda1 the system screams and hollers when it is mounted...Let's take this approach seeing what the system has to say:

```

mount
cat /etc/mtab
dmesg | grep sda1

```
trying to see where the difference is in the auto-mount via /media/sda1 does not work ... but a manual mount via /mnt/test .. has no problem at all.

[INDENT][INDENT][INDENT]we be a look'n[/INDENT][/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-07-02
[SIZE=3][FONT=times new roman]Here ya go.[/FONT][/SIZE]

```
xxxx@ubuntu-shop:~$ mount
/dev/sdf1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/sdb5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /media/sdd1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1 on /media/sde1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde5 on /media/sde5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
gvfs-fuse-daemon on /home/xxx/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xxxx)


xxxx@ubuntu-shop:~$ cat /etc/mtab
/dev/sdf1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda5 /media/sda5 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/sdb1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb5 /media/sdb5 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdc1 /media/sdc1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdd1 /media/sdd1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sde1 /media/sde1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sde5 /media/sde5 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
gvfs-fuse-daemon /home/xxxx/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=xxxx 0 0


xxxx@ubuntu-shop:~$ dmesg | grep sda1
[    1.443608]  sda: sda1 sda2 < sda5 >


xxxx@ubuntu-shop:~$ 

```

---

### Post by Bashing-om on 2013-07-02
Akacheebe; Good morning ...

I do not see that sda1 is mounted ... is that partition enabled to mount in /etc/fstab ?

If no .. enable it (remove the # from the line) and run that last sequence of commands once more, and in addition:
I am concerned that I see sda5 as an extended partition ... makes little sense to me at this time.
Please also do terminal code:
```
sudo parted /dev/sda unit s print
``` and we will see from another perspective how that disk is partitioned.

[INDENT][INDENT]inquiring minds want to know[/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-07-02
[SIZE=4][FONT=times new roman]I've included a copy paste of fstab that shows sda1 doesn't have the #?  Dunno.  Keep in mind that nothing was done to sda5 and that partition is accessable in Ubuntu, on my network and is mounted at boot.  

I checked this morning and when booted up on sda1 (Windows XP x64) I am able to access that drive on my network so all the Windows stuff is working fine?

Here's the stuff again.[/FONT][/SIZE]

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdf1 :
UUID=7ea56b88-7e9d-4f83-badd-664e84bfa0f7    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=3694FEA494FE6631    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sda5    /media/sda5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb1 :
UUID=7A14AC1D14ABDB01    /media/sdb1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb5 :
UUID=CFF510FDBBF04069    /media/sdb5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdc1 :
UUID=A8AA14ACAA1478D0    /media/sdc1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdd1 :
UUID=B6FA0D8EFA0D4BD5    /media/sdd1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sde1 :
UUID=B234158534154DAB    /media/sde1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sde5    /media/sde5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
UUID=F0302D81302D5040    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdf5 :
UUID=59b68caa-460e-43a4-864c-c248768a8273    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0


xxxx@ubuntu-shop:~$ mount
/dev/sdf1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/sdb5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /media/sdd1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1 on /media/sde1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde5 on /media/sde5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
gvfs-fuse-daemon on /home/xxxx/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xxxx)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
xxxx@ubuntu-shop:~$ 


xxxx@ubuntu-shop:~$ cat /etc/mtab
/dev/sdf1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda5 /media/sda5 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/sdb1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb5 /media/sdb5 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdc1 /media/sdc1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdd1 /media/sdd1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sde1 /media/sde1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sde5 /media/sde5 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
gvfs-fuse-daemon /home/xxxx/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=xxxx 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
xxxx@ubuntu-shop:~$ 


xxxx@ubuntu-shop:~$ dmesg | grep sda1
[    1.444914]  sda: sda1 sda2 < sda5 >
xxxx@ubuntu-shop:~$

```

---

### Post by Bashing-om on 2013-07-02
Akacheebe; Hey..
This is about the darndest thing I have encountered in a while...fstab says what to mount (10 external mounts !), mount and mtab commands agree, dmesg  sees sda1 and reports no problems, but in spite of everything else mounting .... sda1 is not mounting !!!

What do we see in terminal when the sda1 partition is (un-)mounted ... and then (re-)mounted manually...as we know there is no fault with the file system on sda1 by being able to mount and access it from an alternate mount point without a problem; There must be a fault in the mount point for some reason. We are going to look first hand.
```
sudo umount /media/sda1 ##does the system let us ... any error reported ?
sudo mount /media/sda1
ls -la /media/sda1/
ls -la /media/sda1/<some-directories> ##do you have full access ??
sudo umount /media/sda1 ##remember, we mounted it manually and must be (un)mounted prior to logging of the system.

```

---

### Post by Akacheebe on 2013-07-03
[SIZE=4][FONT=times new roman]Interesting stuff here now.  I put some notes on the code part with ## in front of them.  This has got to be something simple that we're overlooking??  Doesn't Grub have something to do with mounting these drives at boot??  Just asking................and yes, I have run the command to update Grub but that didn't fix it.  That is IF I did the right command that is.[/FONT][/SIZE]

```
xxxx@ubuntu-shop:~$ sudo umount /media/sda1  ##NO ERRORS
[sudo] password for xxxx: 
umount: /media/sda1: not mounted
xxxx@ubuntu-shop:~$ 

xxxx@ubuntu-shop:~$ sudo mount /media/sda1  ##After this I am able to access that drive from my home folder (GUI) and I can see everything on it??
xxxx@ubuntu-shop:~$

xxxx@ubuntu-shop:~$ ls -la /media/sda1/
total 2096121
drwxrwxrwx  1 root root      12288 Jun 30 18:50 .
drwxr-xr-x 11 root root       4096 Jul  1 09:30 ..
drwxrwxrwx  1 root root       8192 Jun 29 15:07 Agent
drwxrwxrwx  1 root root          0 Jun 29 15:07 Agent Blender
drwxrwxrwx  1 root root          0 Jun 29 15:07 Agent Presto
-rwxrwxrwx  1 root root        163 Jun 29 17:02 ASWL2K.ini
drwxrwxrwx  1 root root          0 Jun 29 15:07 ATI
-rwxrwxrwx  1 root root          0 Jun 29 14:45 AUTOEXEC.BAT
drwxrwxrwx  1 root root      32768 Jun 29 15:08 AZBox Files
-rwxrwxrwx  1 root root        213 Jun 29 14:40 boot.ini
drwxrwxrwx  1 root root      24576 Jun 30 10:59 Camaro Pics_Stuff
drwxrwxrwx  1 root root       4096 Jun 29 15:09 Carb Stuff
drwxrwxrwx  1 root root       4096 Jun 29 15:09 Cband stuff
drwxrwxrwx  1 root root       4096 Jun 29 15:09 cboggs
drwxrwxrwx  1 root root       4096 Jun 29 15:09 computer pics
-rwxrwxrwx  1 root root          0 Jun 29 14:45 CONFIG.SYS
drwxrwxrwx  1 root root       4096 Jun 29 14:55 Documents and Settings
drwxrwxrwx  1 root root       8192 Jun 29 21:10 Downloads
drwxrwxrwx  1 root root      24576 Jul  2 19:30 Downloads_C_x64
drwxrwxrwx  1 root root      28672 Jun 29 15:10 Dragster Pics_Stuff
drwxrwxrwx  1 root root          0 Jun 29 15:44 Intel
-rwxrwxrwx  1 root root          0 Jun 29 14:45 IO.SYS
drwxrwxrwx  1 root root      12288 Jun 29 15:11 LogWorks_dragster
drwxrwxrwx  1 root root       4096 Jun 29 15:11 Mama's Rings
-rwxrwxrwx  1 root root          0 Jun 29 14:45 MSDOS.SYS
-rwxrwxrwx  1 root root      47772 Mar 29  2006 NTDETECT.COM
-rwxrwxrwx  1 root root     297072 Jun 29 17:59 ntldr
drwxrwxrwx  1 root root      12288 Jun 29 15:11 Openbox S9 Stuff
-rwxrwxrwx  1 root root 2145386496 Jul  2 21:27 pagefile.sys
drwxrwxrwx  1 root root          0 Jun 29 15:11 Performance Trends
drwxrwxrwx  1 root root          0 Jun 29 15:11 perftrns.pti
drwxrwxrwx  1 root root       4096 Jun 29 15:07 PIPE36
drwxrwxrwx  1 root root       4096 Jun 29 21:52 Program Files
drwxrwxrwx  1 root root       8192 Jul  2 19:28 Program Files (x86)
drwxrwxrwx  1 root root       4096 Jun 30 10:19 Quake2_original
drwxrwxrwx  1 root root       4096 Jun 29 15:07 Race Car Data
drwxrwxrwx  1 root root       4096 Jun 29 15:07 Race Data Card Copy
drwxrwxrwx  1 root root      77824 Jun 30 20:14 RACER
drwxrwxrwx  1 root root     135168 Jun 29 15:07 RACER_Camaro
drwxrwxrwx  1 root root     135168 Jun 30 10:13 RACER_Dragster
drwxrwxrwx  1 root root          0 Jun 29 17:41 RECYCLER
drwxrwxrwx  1 root root       4096 Jun 29 14:49 System Volume Information
drwxrwxrwx  1 root root       4096 Jun 29 21:17 UnrealTournament
drwxrwxrwx  1 root root     110592 Jul  1 20:27 WINDOWS
drwxrwxrwx  1 root root       4096 Jun 29 15:38 XP x64
xxxx@ubuntu-shop:~$ 

xxxx@ubuntu-shop:~$ ls -la /media/sda1/cboggs  ##Yes, I was able to access info in the cboggs folder in terminal and also from "Home".
total 4208
drwxrwxrwx 1 root root   4096 Jun 29 15:09 .
drwxrwxrwx 1 root root  12288 Jun 30 18:50 ..
-rwxrwxrwx 2 root root 435200 Nov 22  2010 head 001.jpg
-rwxrwxrwx 2 root root 423345 Nov 22  2010 head 002.jpg
-rwxrwxrwx 2 root root 429088 Nov 22  2010 head 003.jpg
-rwxrwxrwx 2 root root 422446 Nov 22  2010 head 005.jpg
-rwxrwxrwx 2 root root 430617 Nov 22  2010 head 006.jpg
-rwxrwxrwx 2 root root 431008 Nov 22  2010 head 007.jpg
-rwxrwxrwx 2 root root 423900 Nov 22  2010 head 008.jpg
-rwxrwxrwx 2 root root 426911 Nov 22  2010 head 009.jpg
-rwxrwxrwx 2 root root 416803 Nov 22  2010 head 010.jpg
-rwxrwxrwx 1 root root 427549 Nov 22  2010 head4.jpg
xxxx@ubuntu-shop:~$ 

unmount seemed to be successful

 
```

---

### Post by Bashing-om on 2013-07-03
Akacheebe; Morning ...

I do not pretend to comprehend all that goes on "under the hood" within this wonderful operating system.. however, this is my thinking at this time...When you redid the sda1 partition the existing links between fstab, the mount point, and the actual device (sda1) were broken. That link has not been reestablished thus not able to mount from the /etc/fstab directive. Everything is in place and indications are that those links are broken in that original set up.

I will not propose any action that I even consider might break your system .. What I am going to do is set up a test bed on my system under a controlled environment and do some testing to see what results. It will take a bit of time for me to think this action through and set it up and then conduct my tests. Upon conclusion, believe me, I will know more of what is happening "under the hood" ! I will then pass my knowledge onto you.

Bear in mind we know of a safe work-a-round to get that partition to automount .. but that will not resolve the underlying condition. If it is expedient to get that partition auto mounting .... can do !

[INDENT][INDENT]what one does not know can hurt
[/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-07-03
> **Bashing-om said:**
> Akacheebe; Morning ...

Bear in mind we know of a safe work-a-round to get that partition to automount .. but that will not resolve the underlying condition. If it is expedient to get that partition auto mounting .... can do !
[INDENT][INDENT]what one does not know can hurt
[/INDENT]
[/INDENT]


Not sure I understand this part as it still will not automount?  In fact, THAT is the part that aggravates me the most as I have to baby sit Ubuntu when it doesn't find sda1 at boot?  

It seems it can be mounted manually but at this point there's nothing on that drive to share with the network that can't be done in Windows.  I can boot up XP x64 and any computer on the network can see it.

And as far as the sda1 partition is concerned, all I did was a simple format before I reinstalled Windows XP.  Nothing was done to the partition on the drive as I left it the same size as it was to begin with.  The boot sector was probably rewritten though by the new install of Windows.

Ennywho, if it's going to take you a while to figure this out, I need to see if I can find a way to make Ubuntu stop looking for that drive at boot.  Any suggestions for doing that?

Thanks

---

### Post by steeldriver on 2013-07-03
I wonder if it is just that the HDD is spun down when the mounting process starts, and that the /dev/sda1 fails (rather than /dev/sda2 etc.) simply because it its the first listed partition in your fstab? Then by the time it tries to mount the other partitions, the device has spun up and is responsive. Just thinking out loud... you could try swapping the order of the partitions in your fstab to see if it's always the first listed one that fails?

If so there may be a mount option that will delay mounting enough to let the device spin up? Meanwhile you could add the option 'nofail' to the fstab entry for sda1 which (I think) will allow mount to ignore it if it is 'missing' but still allow you to mount it later e.g. using 'mount -a'

---

### Post by Bashing-om on 2013-07-03
Akacheebe; Sure !

Fast work-a-round to allow auto mounting:
1. Make a new mount point in the directory "/media", as for example:
```
sudo mkdir /media/sda1-new
```
Reboot the system to clear any blkid cache and then insure the UUID of sda1 remains same same.
2. edit "/etc/fstab" to reflect the new mount point, verify the UUID is correct and change:
>  UUID=3694FEA494FE6631    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
the portion /media/sda1 to be /media/sda1-new.
3.run the mount command just to insure there are no typos in "/etc/fstab"
```
 sudo mount -a
``` no output is good -> command accepted with no errors.

Reboot once more to see effect... at this time sda1 should auto mount with out problems...

Let's look:
```
mount
``` and sda1 should be listed as mounted.

[INDENT][INDENT]workie great last long time[/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-07-03
[SIZE=4][FONT=times new roman]OOPS!  ERROR?  This UUID was in one of the first fstab posts I made?  In fact, one of the early posts had two sda1 listed and this one was one of them.  I've included another cat of fstab that shows we have two drives designated as sda1 with this one that produced the error at the bottom.  FYI I'm going to comment that one out with ## and see if that makes a difference.    [/FONT][/SIZE]

```
xxxx@ubuntu-shop:~$ sudo mount -a
ntfs-3g: Failed to access volume 'UUID=F0302D81302D5040': No such file or directory

ntfs-3g 2012.1.15AR.1 external FUSE 28 - Third Generation NTFS Driver
        Configuration type 7, XATTRS are on, POSIX ACLS are on

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2011 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

News, support and information:  http://tuxera.com
xxxx@ubuntu-shop:~$ 

xxxx@ubuntu-shop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdf1 :
UUID=7ea56b88-7e9d-4f83-badd-664e84bfa0f7    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=3694FEA494FE6631    /media/sda1-new    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sda5    /media/sda5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb1 :
UUID=7A14AC1D14ABDB01    /media/sdb1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb5 :
UUID=CFF510FDBBF04069    /media/sdb5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdc1 :
UUID=A8AA14ACAA1478D0    /media/sdc1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdd1 :
UUID=B6FA0D8EFA0D4BD5    /media/sdd1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sde1 :
UUID=B234158534154DAB    /media/sde1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sde5    /media/sde5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
UUID=F0302D81302D5040    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdf5 :
UUID=59b68caa-460e-43a4-864c-c248768a8273    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0


xxxx@ubuntu-shop:~$ 

```

[SIZE=4][FONT=times new roman]UPDATE:  IT'S WORKING NOW!!  I just rebooted and Ubuntu came right up so it was obviously seeing two sda1 drives in fstab and wouldn't mount either.  [/FONT][/SIZE]

---

### Post by Bashing-om on 2013-07-03
Akacheebe; Well well ..

Let me take another gander at /etc/fstab with a new perspective ...To now I have not seen anything that would mount sda1 twice.. reason that I asked earlier if there was something in your startup scripts prematurely accessing sda1. But, I do want to know the whereof and howso. Maybe a duplication of UUIDs ??... I will compare and see what I can see ... back at ya soonest.

Pleasing that at least now it is mounting !

[INDENT][INDENT]I be look'n
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-03
Akacheebe; Plot thickens ->

The error associated with UUID "F0302D81302D5040" is NOT in reference to sda1.
And I still have some reservations is respect to sda5;
Let get a fresh look at what the system has assigned as UUID's to the partitions:
```
sudo /sbin/blkid ##to refresh the cache
sudo blkid ##shows updated assighnments.

```
And, I really suggest that "sda5" in /etc/fstab also be accessed by UUID rather than the device name ... maybe the system is experiencing a problem translating "/dev/sda5" to the actual UUID ... I have seen that happen. There is a strong reason why the use of UUIDs are so strongly recommended within the fstab file.
> 
 # Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).


As of now -neglecting the sda5 issue- I see no duplication in the uuid's within /etc/fstab. Let see what the updated "blkid" has to convey.

[INDENT][INDENT]that is what I think
[/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-07-03
[SIZE=4][FONT=times new roman]Before we go any further let me give you some FYI here.  

I got to thinking after I saw that second sda1 listed in cat fstab that when I first reconnected all the drives and then booted into Ubuntu I went straight into NTFS configuration tool and checked to see if sda1 was listed, and it was.  I made sure that it was set like the rest of the partitions and closed out the tool.  

I then went into SAMBA and looked for sda1 to make it share on the network but it wasn't listed??  I clicked "add" and then instead of using the "Browse" button and looking in the /media directory I just wrote in that sda1, saved it and then configured it for network sharing.  

So, what I did was actually create another sda1 that was written to fstab from SAMBA that actually WASN'T actually there, ie, UUID F030etc and seeing as how I had made this one in SAMBA and not the other, Ubuntu kept trying to mount a partition that wasn't there.  At least this is my take on it.  So it was basically a problem with the loose nut behind the keyboard that caused the problem.  

Enywho, I'm on my other system now and getting ready for bed so I won't be able to give you any more info until tomorrow morning after I get up and get out into the shop.  

Thanks[/FONT][/SIZE]

---

### Post by Bashing-om on 2013-07-04
Akacheebe; hello..
Samba making the assignment makes a lot of sense.
Remains to identify the partition that F0302D81302D5040 is associated to.
My last to refresh the blkid cache and output the new blkid IDs and as well It still might be good to see the actual partitioning of the sda drive:
```
sudo parted /dev/sda unit s print
``` and that will cross relate sda5.

Then we can look at samba's config files and check for a misdirection there too.

I too have grown heavy in the mind .. and will meet ya in the mid am.

[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-07-04
[SIZE=4][FONT=times new roman]I think I can also answer your question regarding the "Local Disk" label on sde5.  After the reload of sda1 the drive letter assignment didn't come up the way it previously was as sda5 was known by the letter "J" on my system.  Since all my Windows systems (and Ubuntu) use that "J" drive for storage of documents, pictures and downloads, etc I went in and changed the drive letter from it's new designation of "K" to it's old designation of "J" so I wouldn't have to go in and tell all these Windows systems the new "K" location for data storage.  At some point in that process I do remember seeing that "Local Disk" name but it didn't show up in Windows Explorer.  At this point there are no problems with sde5 and with that drive having 700+ GB of stuff on it I'm not too keen on doing much with it as long as it's working like it is.

Does this answer your questions on sde5?

Here's the other info you requested.

Thanks, 

Edit:  here's another cat of fstab and the local disk is gone.  I fixed that.

[/FONT][/SIZE]


```
 xxxx@ubuntu-shop:~$ sudo /sbin/blkid
[sudo] password for xxxx: 
/dev/sda1: UUID="3694FEA494FE6631" TYPE="ntfs" 
/dev/sda5: UUID="8088B7CE88B7C148" TYPE="ntfs" 
/dev/sdb1: UUID="7A14AC1D14ABDB01" TYPE="ntfs" 
/dev/sdb5: UUID="CFF510FDBBF04069" TYPE="ntfs" 
/dev/sdc1: UUID="A8AA14ACAA1478D0" TYPE="ntfs" 
/dev/sdd1: UUID="B6FA0D8EFA0D4BD5" TYPE="ntfs" 
/dev/sde1: UUID="B234158534154DAB" TYPE="ntfs" 
/dev/sde5: LABEL="Local Disk" UUID="8088B7CE88B7C148" TYPE="ntfs" 
/dev/sdf1: UUID="7ea56b88-7e9d-4f83-badd-664e84bfa0f7" TYPE="ext4" 
/dev/sdf5: UUID="59b68caa-460e-43a4-864c-c248768a8273" TYPE="swap" 
xxxx@ubuntu-shop:~$ 


xxxx@ubuntu-shop:~$ sudo blkid
/dev/sda1: UUID="3694FEA494FE6631" TYPE="ntfs" 
/dev/sda5: UUID="8088B7CE88B7C148" TYPE="ntfs" 
/dev/sdb1: UUID="7A14AC1D14ABDB01" TYPE="ntfs" 
/dev/sdb5: UUID="CFF510FDBBF04069" TYPE="ntfs" 
/dev/sdc1: UUID="A8AA14ACAA1478D0" TYPE="ntfs" 
/dev/sdd1: UUID="B6FA0D8EFA0D4BD5" TYPE="ntfs" 
/dev/sde1: UUID="B234158534154DAB" TYPE="ntfs" 
/dev/sde5: LABEL="Local Disk" UUID="8088B7CE88B7C148" TYPE="ntfs" 
/dev/sdf1: UUID="7ea56b88-7e9d-4f83-badd-664e84bfa0f7" TYPE="ext4" 
/dev/sdf5: UUID="59b68caa-460e-43a4-864c-c248768a8273" TYPE="swap" 
xxxx@ubuntu-shop:~$ 



xxxx@ubuntu-shop:~$ sudo parted /dev/sda unit s print
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system  Flags
 1      63s         163846934s  163846872s  primary   ntfs         boot
 2      163846935s  976768064s  812921130s  extended               lba
 5      163846998s  976768064s  812921067s  logical   ntfs

xxxx@ubuntu-shop:~$ 

```

UPDATE:

```
xxxx@ubuntu-shop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdf1 :
UUID=7ea56b88-7e9d-4f83-badd-664e84bfa0f7    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=3694FEA494FE6631    /media/sda1-new    ntfs-3g    defaults,locale=en_US.UTF-8    00
/dev/sda5    /media/sda5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb1 :
UUID=7A14AC1D14ABDB01    /media/sdb1    ntfs-3g    defaults,locale=en_US.UTF-8    00
#Entry for /dev/sdb5 :
UUID=CFF510FDBBF04069    /media/sdb5    ntfs-3g    defaults,locale=en_US.UTF-8    00
#Entry for /dev/sdc1 :
UUID=A8AA14ACAA1478D0    /media/sdc1    ntfs-3g    defaults,locale=en_US.UTF-8    00
#Entry for /dev/sdd1 :
UUID=B6FA0D8EFA0D4BD5    /media/sdd1    ntfs-3g    defaults,locale=en_US.UTF-8    00
#Entry for /dev/sde1 :
UUID=B234158534154DAB    /media/sde1    ntfs-3g    defaults,locale=en_US.UTF-8    00
/dev/sde5    /media/sde5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
##UUID=F0302D81302D5040    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    00
#Entry for /dev/sdf5 :
UUID=59b68caa-460e-43a4-864c-c248768a8273    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0


xxxx@ubuntu-shop:~$ 
```

---

### Post by Bashing-om on 2013-07-04
Akacheebe; Still going around and around !

Look at the blkid output...UUID 8088B7CE88B7C148 as doubly assigned and causing conflicts. It is assigned to both sda5 and too sde5.

Here is what I show and this chart filled in will help a bunch:

> 
 ========================== blkid--fstab---- mntpt------------mount---------------mtab-----------------fdisk
ea56b88-7e9d-4f83-badd-664e84bfa0f7 ==sdf1      sdf1      /
3694FEA494FE6631 -------------------------------sda1      sda1  media/sda1-new
7A14AC1D14ABDB01------------------------------sdb1      sdb1  media/sdb1
CFF510FDBBF04069 -------------------------------sdb5      sdb5  media/sdb5
A8AA14ACAA1478D0------------------------------sdc1      sdc1  media/sdc1
B6FA0D8EFA0D4BD5------------------------------sdd1      sdd1  media/sdd1
B234158534154DAB------------------------------sde1      sde1  media/dfe1
=========================   sde5  media/sde5*
59b68caa-460e-43a4-864c-c248768a8273   swap      sdf5   SWAP
8088B7CE88B7C148------------------------------sde5&sda5  NO!
                                                                                       sda5 (!)                   
                                                 
F0302D81302D5040 -> old sda1(?) mount(fstab) current as sde5 (#)


F0302D81302D5040 -> which partition is this ?
Not seen in mount:
8088B7CE88B7C148 which is blkid sda5
-------
blkid:
/dev/sda5: UUID="8088B7CE88B7C148" TYPE="ntfs"
/dev/sde5: LABEL="Local Disk" UUID="8088B7CE88B7C148" TYPE="ntfs"


In order to complete the picture
```

mount
cat /etc/mtab
sudo fdisk -lu

```

I do not know how to maintain my formatting in the chart from my original... but you get the idea ... things are not matching up.

We will keep pounding away at it 'till we get it right ... I keep pounding on sda5.
[INDENT][INDENT]I just try'n to help
[/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-07-05
[SIZE=4][FONT=times new roman]OK here's the output from your last request.  Dunno what's up but everything is working fine from this end??  [/FONT][/SIZE]

```
xxxx@ubuntu-shop:~$ mount
/dev/sdf1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /media/sda1-new type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/sdb5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /media/sdd1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1 on /media/sde1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde5 on /media/sde5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
gvfs-fuse-daemon on /home/xxxx/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xxxx)
xxxx@ubuntu-shop:~$ 

xxxx@ubuntu-shop:~$ cat /etc/mtab
/dev/sdf1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda1 /media/sda1-new fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda5 /media/sda5 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/sdb1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb5 /media/sdb5 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdc1 /media/sdc1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdd1 /media/sdd1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sde1 /media/sde1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sde5 /media/sde5 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
gvfs-fuse-daemon /home/xxxx/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=xxxx 0 0
xxxx@ubuntu-shop:~$ 

xxxx@ubuntu-shop:~$ sudo fdisk -lu
[sudo] password for xxxx: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde73de73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   163846934    81923436    7  HPFS/NTFS/exFAT
/dev/sda2       163846935   976768064   406460565    f  W95 Ext'd (LBA)
/dev/sda5       163846998   976768064   406460533+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45bf45be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    93064544    46532241    7  HPFS/NTFS/exFAT
/dev/sdb2        93128805  1953520064   930195630    5  Extended
/dev/sdb5        93128869  1953520064   930195598    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x96cea8d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   488392064   244196001    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc38688a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048    39872511    19935232    7  HPFS/NTFS/exFAT

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7e61057

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63   163766609    81883273+   7  HPFS/NTFS/exFAT
/dev/sde2       163766610   488392064   162312727+   f  W95 Ext'd (LBA)
/dev/sde5       163766673   488392064   162312696    7  HPFS/NTFS/exFAT

Disk /dev/sdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00078df7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *        2048   147916799    73957376   83  Linux
/dev/sdf2       147918846   156301311     4191233    5  Extended
/dev/sdf5       147918848   156301311     4191232   82  Linux swap / Solaris
xxxx@ubuntu-shop:~$ 
 
```

---

### Post by Bashing-om on 2013-07-05
Akacheebe; Roger that .. 

I be checking ... there is at some point going to be conflicts, 2 partitions asighned to the same UUID is going to confuse something sometime.

[INDENT][INDENT]work'n on it[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-05
Akacheebe;  I am back !

Ok, excepting sda5/sde5, and UUID "F0302D81302D5040"  all appears in order:
> 
-------UUIDs----------------------------------------------------blkid-----fstab----mntpt----------------mount---mtab--fdisk
7ea56b88-7e9d-4f83-badd-664e84bfa0f7 ====sdf1------sdf1-----/-----------------------ok-----ok----ok
3694FEA494FE6631 ==----------------------------------sda1------sda1--media/sda1-new---ok-----ok----ok
7A14AC1D14ABDB01 ==--------------------------------sdb1------sdb1--media/sdb1----------ok-----ok----ok     
CFF510FDBBF04069 ==---------------------------------sdb5------sdb5--media/sdb5----------ok-----ok----ok
8AA14ACAA1478D0 == ---------------------------------sdc1------sdc1--media/sdc1-----------ok-----ok----ok
B6FA0D8EFA0D4BD5 ==-------------------------------sdd1------sdd1--media/sdd1-----------ok-----ok----ok
B234158534154DAB ==--------------------------------sde1------sde1--media/sde1------------ok-----ok----ok
--------------------------------------------------------???------sde5  media/sde5*----------------------sde5---sde5--sde5
59b68caa-460e-43a4-864c-c248768a8273-------swap-------sdf5   SWAP-------------------n/a----n/a---ok
8088B7CE88B7C148--------------------sde5&sda5  NO!--media/sda5----------------------------------------ok
======================sda5 (!)--sda5--------------------------------------ok------ok--sda5                 
================mount on demand(?)===============================sde5(?)
================mount on demand=================================sda2
================mount on demand=================================sda5
================mount on demand=================================sdf1
================mount on demand=================================sdf2
================mount on demand=================================sdf5
                                                 
F0302D81302D5040 -> old sda1(?) mount(fstab) current as sde5 (#)


F0302D81302D5040 -> which partition is this ?
//
Not seen in mount: And may be just fine. IF sde5 is (re-)assigned
8088B7CE88B7C148 which is blkid sda5 AND sde5


So let us see what the system has to tell:
```

ls -l /dev/disk/by-uuid/F0302D81302D5040
ls -l /dev/disk/by-uuid/8088B7CE88B7C148
sudo blkid /dev/sda5 -c /dev/null
sudo blkid /dev/sde5 -c /dev/null

```

Maybe we can tell what is what .. and assign the partitions.

[INDENT][INDENT][INDENT]almost done ![/INDENT][/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-07-06
[SIZE=4][FONT=times new roman]F0302D81302D5040 is the one I created by accident in SAMBA.  Notice in the cat fstab I just posted that it's commented out, ie, ## in front of that line.  THAT was how I got the "drive not ready or missing" error to stop at boot up.  I can delete that if needed but it's not hurting anything like it is now.  

As for sda5 and sde5 having the same UUID, I got no clue but I can tell you that it's not causing any problems at all now?  I just went to another computer on my LAN and I could access both those partitions while booted in Linux on BOTH machines.  sde5 is the drive that formerly had "Local Disk" listed in it's name in cat fstab?  I removed that the other day just to make everything look the same.  sde5 is a 166GB D: partition on a 250GB drive.  sda5 is a 416GB D: partition on a 500GB drive.  

Here's the stuff you requested plus another copy of cat fstab.

```
xxxx@ubuntu-shop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdf1 :
UUID=7ea56b88-7e9d-4f83-badd-664e84bfa0f7    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=3694FEA494FE6631    /media/sda1-new    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sda5    /media/sda5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb1 :
UUID=7A14AC1D14ABDB01    /media/sdb1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb5 :
UUID=CFF510FDBBF04069    /media/sdb5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdc1 :
UUID=A8AA14ACAA1478D0    /media/sdc1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdd1 :
UUID=B6FA0D8EFA0D4BD5    /media/sdd1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sde1 :
UUID=B234158534154DAB    /media/sde1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sde5    /media/sde5    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
##UUID=F0302D81302D5040    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdf5 :
UUID=59b68caa-460e-43a4-864c-c248768a8273    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0


xxxx@ubuntu-shop:~$ ls -l /dev/disk/by-uuid/F0302D81302D5040
ls: cannot access /dev/disk/by-uuid/F0302D81302D5040: No such file or directory
xxxx@ubuntu-shop:~$

 
xxxx@ubuntu-shop:~$ ls -l /dev/disk/by-uuid/8088B7CE88B7C148
lrwxrwxrwx 1 root root 10 Jul  6 14:36 /dev/disk/by-uuid/8088B7CE88B7C148 -> ../../sde5
xxxx@ubuntu-shop:~$

 
xxxx@ubuntu-shop:~$ sudo blkid /dev/sda5 -c /dev/null
/dev/sda5: UUID="8088B7CE88B7C148" TYPE="ntfs"
xxxx@ubuntu-shop:~$

xxxx@ubuntu-shop:~$ sudo blkid /dev/sde5 -c /dev/null
/dev/sde5: UUID="8088B7CE88B7C148" TYPE="ntfs"
xxxx@ubuntu-shop:~$
 
``` 




[/FONT][/SIZE]

---

### Post by Bashing-om on 2013-07-06
Akacheebe; Hello,

Busy Saturday ...
Be assured my priority is that you have a solid stable operating system.
To that end I do not see how your system can be stable with partitions sda5 and sde5 both assigned to UUID "8088B7CE88B7C148".
What puzzles me is where the assignments are being made; OR reassigned (??). Both are mounted in /etc/fstab by device rather than by UUID.
Perhaps a miss match in the /media/ folder ?? Is there duplicated assignments ?
```
ls -la /media/
```One more time - current info.

UUID "F0302D81302D5040" is presently not an issue as it no longer exist (formerly assigned to sda1 problem partition).

I have never before encountered such a situation.. got me to studying and thinking !

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Akacheebe on 2013-07-07
[SIZE=4][FONT=times new roman]Well, I guess this is probably the first time you ever ran up on anyone with a computer with this many operating systems/hard drives?  I'll bet you hope it's your last too!  6 hard drives and each one has an OS on it and a couple have storage partitions.  Believe it or not, it gives me very few problems though.  

Here's your last request and I'm going to mark this thread as solved even though we still don't know why sda5 and sde5 have the same UUID.  It's working and I guess that's all that matters at this point!

Thanks
[/FONT][/SIZE]


```
 xxxx@ubuntu-shop:~$ ls -la /media/
total 148
drwxr-xr-x 12 root root  4096 Jul  6 13:34 .
drwxr-xr-x 24 root root  4096 Jun 14 12:25 ..
-rw-r--r--  1 root root    95 Jul  4 11:16 .created_by_python-fstab
lrwxrwxrwx  1 root root     7 May  6 11:10 floppy -> floppy0
drwxr-xr-x  2 root root  4096 May  6 11:10 floppy0
drwxr-xr-x  2 root root  4096 May  6 13:21 sda1
drwxrwxrwx  1 root root 12288 Jul  7 10:54 sda1-new
drwxrwxrwx  1 root root 32768 Jul  7 10:54 sda5
drwxrwxrwx  1 root root  8192 Jul  7 10:54 sdb1
drwxrwxrwx  1 root root 12288 Jul  7 10:54 sdb5
drwxrwxrwx  1 root root 12288 Jul  7 10:54 sdc1
drwxrwxrwx  1 root root  8192 Jul  7 10:54 sdd1
drwxrwxrwx  1 root root 16384 Jul  7 10:54 sde1
drwxrwxrwx  1 root root 28672 Jul  7 10:54 sde5
xxxx@ubuntu-shop:~$ 

```

---

### Post by Bashing-om on 2013-07-07
Akacheebe; Good 'nuff...

To bolster your confidence in my recommendations. Be advised I was formerly (back when AT&T's monopoly on telecommunications was broke) the senior technical controller for large companies in that emerging market. I have been associated with computers since the 60's in many types, sizes and designs and applications; Written programs and prologs for many many things, applying my skills and knowledge to problem resolution at many levels. Now, I still enjoy solving puzzles. 

To this day I still want to know what makes an Operating System tick and my operating system of choice is ubuntu. Along my path I will help anyone I can requesting assistance. -> there is more that I do not know than what I do know !

[INDENT][INDENT]still learning even after all these years[/INDENT][/INDENT]

---

