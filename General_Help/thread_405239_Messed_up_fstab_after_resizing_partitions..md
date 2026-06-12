---
title: "Messed up fstab after resizing partitions."
date: 2007-04-09
forum: General Help
---

### Post by brakmaren on 2007-04-09
Hi fellows
Changed the size of 2 partitions using gparted.

Before: 
sdb1 - 190G
sdb2 - 40G
sdb3 - swap

After:
sdb1 - 220G
sdb2 - 10G
sdb3 - swap

This is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  	<options>       			<dump>  <pass>
proc            		/proc              proc    	    defaults        			            0              0
# /dev/sda3
UUID=2be8c4d2-0d9e-4aef-8f8c-f039e68db92b  /  ext3  defaults,errors=remount-ro  0       1
# /dev/sda1
UUID=00E0E4212FA90A2D  /media/sda1  ntfs  defaults,nls=utf8,umask=007,gid=46 	0       1
# /dev/sda2
UUID=5926656B75719718  /media/sda2  ntfs  defaults,nls=utf8,umask=007,gid=46 	0       1
# /dev/sdb1
UUID=c084ba8f-8721-cd04-1b48-1e3ac4248105  /media/sdb1  ext3  defaults  0       2
# /dev/sdb2
UUID=2637fbc0-a839-4642-913e-28ae9aec944f   /media/sdb2  ext3  defaults  0       2
# /dev/sdb3
UUID=a665bc03-e45d-472a-bf45-c4f44736fb82  none  swap  sw              		0       0
/dev/hdc        			/media/cdrom0   udf,iso9660 	user,noauto     			0       0
/dev/hda        			/media/cdrom1   udf,iso9660 	user,noauto     			0       0

```

After the change the desktop icon for sda2 id gone.

And when starting up i get an error:
File system check failed.
Please repair manually.

/var/log/fsck/checkfs say
```
Log of fsck -C -R -A -a 
Mon Apr  9 19:11:59 2007

fsck 1.39 (29-May-2006)
Data: clean, 63465/28934144 files, 53843218/57850057 blocks
fsck.ext3: Unable to resolve 'UUID=2637fbc0-a839-4642-913e-28ae9aec944f'

fsck died with exit status 8

Mon Apr  9 19:11:59 2007
```

I have never seen this 'UUID=2637fbc0-a839-4642-913e-28ae9aec944f' in fstab before.
So i got no idea how to solve the problem.
Any tipps or pointers is apriciated.
Thank's

---

### Post by klytu on 2007-04-09
> **brakmaren said:**
> Hi fellows
Changed the size of 2 partitions using gparted.

Before: 
sdb1 - 190G
sdb2 - 40G
sdb3 - swap

After:
sdb1 - 220G
sdb2 - 10G
sdb3 - swap

This is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  	<options>       			<dump>  <pass>
proc            		/proc              proc    	    defaults        			            0              0
# /dev/sda3
UUID=2be8c4d2-0d9e-4aef-8f8c-f039e68db92b  /  ext3  defaults,errors=remount-ro  0       1
# /dev/sda1
UUID=00E0E4212FA90A2D  /media/sda1  ntfs  defaults,nls=utf8,umask=007,gid=46 	0       1
# /dev/sda2
UUID=5926656B75719718  /media/sda2  ntfs  defaults,nls=utf8,umask=007,gid=46 	0       1
# /dev/sdb1
UUID=c084ba8f-8721-cd04-1b48-1e3ac4248105  /media/sdb1  ext3  defaults  0       2
# /dev/sdb2
UUID=2637fbc0-a839-4642-913e-28ae9aec944f   /media/sdb2  ext3  defaults  0       2
# /dev/sdb3
UUID=a665bc03-e45d-472a-bf45-c4f44736fb82  none  swap  sw              		0       0
/dev/hdc        			/media/cdrom0   udf,iso9660 	user,noauto     			0       0
/dev/hda        			/media/cdrom1   udf,iso9660 	user,noauto     			0       0

```

After the change the desktop icon for sda2 id gone.

And when starting up i get an error:
File system check failed.
Please repair manually.

/var/log/fsck/checkfs say
```
Log of fsck -C -R -A -a 
Mon Apr  9 19:11:59 2007

fsck 1.39 (29-May-2006)
Data: clean, 63465/28934144 files, 53843218/57850057 blocks
fsck.ext3: Unable to resolve 'UUID=2637fbc0-a839-4642-913e-28ae9aec944f'

fsck died with exit status 8

Mon Apr  9 19:11:59 2007
```

I have never seen this 'UUID=2637fbc0-a839-4642-913e-28ae9aec944f' in fstab before.
So i got no idea how to solve the problem.
Any tipps or pointers is apriciated.
Thank's

EDIT: I have corrected some information I posted a while ago. Corrected info is in [COLOR="Blue"]**blue**[/COLOR] below.

The way I understand it (which may very well be incomplete or incorrect) is that UUID's (or Labels) are a flexible way to mount removable devices whose "dev" entries may vary at each boot.[COLOR="Blue"] More precisely the man page for fstab states[/COLOR]:   > instead  of  giving  the  device  explicitly, one may indicate the (ext2 or xfs) filesystem that is to be mounted by its UUID or volume label (cf. e2label or xfs_admin), writing LABEL=<label> or UUID=<uuid>, e.g., &#8216;LABEL=Boot&#8217; or &#8216;UUID=3e6be9de-8139-11d1-9106-a43f08d823a6&#8217;.   This  will
make the system more robust: adding or removing a SCSI disk changes the disk device name but not the filesystem volume label.
If your partitioning somehow altered some of the UUID's, that would explain the error you are getting. You could try looking at the output of dmesg to see what /dev device entries were assigned and then use tune2fs to check each one for it's UUID. For example:
```
sudo tune2fs -l /dev/sda1 | grep UUID
```

[COLOR="Blue"]But tune2fs only works for ext2 and ext3 filesystems; also you'd need to invoke as root user. The command above should FAIL with an error message based on your current fstab file. But this invocation should work for /dev/sdb1: [/COLOR] ```
sudo tune2fs -l /dev/sdb1 | grep UUID 
```

Note what appears after the Filesystem UUID for each device. You could then back up your current fstab and try editing it with the updated UUIDs you obtain. 

You could try to mount your ntfs partitions using the device names instead of the UUIDs in fstab. For example, change these lines: > # /dev/sda1
UUID=00E0E4212FA90A2D  /media/sda1  ntfs  defaults,nls=utf8,umask=007,gid=46 	0       1
# /dev/sda2
UUID=5926656B75719718  /media/sda2  ntfs  defaults,nls=utf8,umask=007,gid=46 	0       1
 to these:>  #UUID=00E0E4212FA90A2D
/dev/sda1  /media/sda1  ntfs  defaults,nls=utf8,umask=007,gid=46 	0       1
#UUID=5926656B75719718
/dev/sda2  /media/sda2  ntfs  defaults,nls=utf8,umask=007,gid=46 	0       1

---

### Post by brakmaren on 2007-04-10
You're a life saver.
Not only did you nail the fault, you cleared up my brain too :-)
As well as tought me a new command to play with.
Thank's a million mate.
Case closed.

---

