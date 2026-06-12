---
title: "Swap gone?"
date: 2006-12-22
forum: General Help
---

### Post by derby007 on 2006-12-22
I think my SWAP is gone, but i'm not sure. I initially set it up as 1GB. But from looking at the command 'FREE -M' i get the following:

free -m
             total       used       free     shared    buffers     cached
Mem:      502        496          5          0            25            263
-/+ buffers/cache:        208        293
Swap:       0          0          0

Does this mean SWAP has disappeared?
Also: why is so much memory being used?

But when i run 'DF -H' i get : 
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda7              16G  4.2G   11G  29% /
varrun                252M   92K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                   10M  176K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  234M   8% /lib/modules/2.6.17-10-386/volatile
/dev/hda1              47M  7.2M   40M  16% /media/hda1
/dev/hda2              50G   18G   33G  36% /media/hda2
/dev/hda3             3.0G  2.1G  919M  71% /media/hda3
/dev/hda5             5.0G  2.4G  2.7G  47% /media/hda5

Does this mean SWAP is OK, ie. i see 4 * 252MB partitions....

---

### Post by po0f on 2006-12-22
derby007,

Those partitions are of the tmpfs type, and reside in RAM IIRC.  What's the output of:
```
[FONT="Courier New"]$ sudo fdisk -l[/FONT]
```

---

### Post by derby007 on 2006-12-22
As i'm not at home at the mo, & that PC isn't connected to the Net, i cant tell u what the outcome is !!  Sorry....
Can u tell me what the following means: Swap: 0 0 0
Should i see some figures here, as i think i might have messed it up by trying to get another Ubuntu installation going on another partition, but the partition manager during install doesnt like 2 '/'s (roots & 'swap's), so i aborted this idea.

---

### Post by po0f on 2006-12-22
derby007,

It means that there is no swap.  The output of the command I posted will tell us if you have a swap partition.

---

### Post by derby007 on 2006-12-22
The 1GB 'swap'partition is there as i can see it in both WinXP (partition manager) & in the partition manager when trying to install a new Ubuntu, ie. Live CD or Alternate CD. Does this help...maybe i need to tell Ubuntu to see SWAP or try and access it or something...??:-?

---

### Post by po0f on 2006-12-22
derby007,

Just because the partition is there doesn't mean it's set up to be a swap partition.  You might have accidentally put an ext3 filesystem on it during a reinstall.  The only way to tell if it's a swap partition or not is to post the output of `sudo fdisk -l`.  This will tell us all partitions available and their types.

---

### Post by derby007 on 2006-12-22
OK, i'll do that tonite, call back tomorrow ....

---

### Post by derby007 on 2006-12-23
OK, i'm back.....sorry about delay, cant do anything about it !

See below for the fdisk -l & fstab: Note: i then changed the SWAP in fstab to a back-up version, and note the diff in the 'free -m' (below) from the post above  :
So, i think its OK again, is it ??

fdisk -l
Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           6       48163+  de  Dell Utility
/dev/hda2   *           7        6528    52387965    7  HPFS/NTFS
/dev/hda3            9334        9725     3148740   db  CP/M / CTOS / ...
/dev/hda4            6529        9333    22531162+   f  W95 Ext'd (LBA)
/dev/hda5            6529        7174     5188963+   b  W95 FAT32
/dev/hda6            7175        7304     1044193+  82  Linux swap / Solaris
/dev/hda7            7305        9333    16297911   83  Linux

***********************
# /etc/fstab: static file system information.
## <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7 -- converted during upgrade to edgy
UUID=fcf3f5f1-0f38-4044-ab44-8ec1cb370468 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=07D5-0A15 /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=C0CC5DCFCC5DC078 /media/hda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/hda3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5 -- converted during upgrade to edgy
UUID=4497-341C /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=69e7be4e-61a4-42ef-adbe-dc366e30cb11 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

*****************************

FSTAB.PRE-UUID  <<< back-up  >>>

# /etc/fstab: static file system information.
## <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
********************

After, seems OK:>>>>>>>>>>

free -m
        	     total       used       free     shared    buffers     cached
Mem:             502        405         96          0            11        	203
-/+ buffers/cache:   190        311
Swap:         1019          0       1019


> fdisk -l
Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
	   Device Boot      Start              End        Blocks   Id   System
/dev/hda1    	1           6           48163+  	de	   Dell Utility
/dev/hda2   *           7        6528    52387965    	7  	HPFS/NTFS
/dev/hda3            9334        9725     3148740   	db  	CP/M / CTOS / ...
/dev/hda4            6529        9333    22531162+   	f  	W95 Ext'd (LBA)
/dev/hda5            6529        7174     5188963+   	b  	W95 FAT32
/dev/hda6            7175        7304     1044193+  	82  	Linux swap / Solaris
/dev/hda7            7305        9333    16297911   83  Linux

---

