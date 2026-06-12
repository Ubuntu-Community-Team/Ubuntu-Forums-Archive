---
title: "Can't read backup drive - filesystem loop causing lose of backup file"
date: 2008-07-02
forum: General Help
---

### Post by sofasurfer on 2008-07-02
sda1 is my boot partition. sdb1 is my backup partition.
When I first created backup I used 'Storage Device Manager' to mount and unmount. This worked fine for a while. And I could find my backup (a TAR file)with my browser.

After a while 'Storage Device Manager' started showing my devices as incorrect... such as 3 partitions on sda instead of 2, and 2 partitions on sdb instead of 3. At these times, when I would browse to my backup, I would see my filesystem instead of my backup file.

This problem would come and go. Soon it would not go away at all. My backup file is now inaccessable. But my filesystem appears in its place.

In trying to sort this out I used the find command to locate the backup file (tempsave-backup.tgz.07.01.08). This is the resulting output...

```
desktop:~$ sudo find / -name tempsave-backup.tgz.07.01.08
[sudo] password for daryl: 
find: Filesystem loop detected; `/mnt/backup' has the same device number and inode as a directory which is 2 levels higher in the filesystem hierarchy.
find: /home/daryl/.gvfs: Permission denied
```

If I run this command with 'sudo' I get a list of directories with 'permission denied' messages.

I know my backup file still exists. How can I fix this problem?

---

### Post by sofasurfer on 2008-07-02
I installed 'livecd' and mounted my boot partition and my backup partition at /mnt/sda1 and /mnt/sdb1.

I then browsed to /mnt/sda1 and /mnt/sdb1 and at BOTH locations my TAR backup file (tempsave-backup.tgz.07.01.08) shows up.

Also with 'livecd' I ran gparted. 
My boot partition is shown as sda1 and is shown to have a mount point of /mnt/sda1, /mnt/sdb1.

This is over my head. I hope someone can help.

---

### Post by sofasurfer on 2008-07-03
I deleted the entry in /fstab, disconnected my boot drive and repartitioned and formatted the backup drive. Then I created /mnt/backup and the mounted in terminal like sudo mount /dev/sdb1 /mnt/backup. So far things are working alright.

I suspect that my problem was because I originally set up my backup drive in /etc/fstab amd later used a mounting tool which then added the entry to /etc/mtab. Even though I had eventially deleted the /fstab entry there was still a problem. 

I clean mount being sure to ONLY use the manual method may be the answer.

---

### Post by sofasurfer on 2008-07-03
Nope!!! Same problem. I just browsed to my backup drive and found my file system listed there.

HELP!!

---

### Post by sofasurfer on 2008-07-03
I seem to have found what is causing me to not be able to access my backup drive.

Every time I boot my system, the boot drive and the backup drive are switched around as to which one is assigned to /sda1 and sdb1.

So the first time I boot my system I get this result from 'sudo fdisk -l':

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045568

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12748   102398278+  83  Linux
/dev/sda2           12749       26771   112639747+  83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44694469

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30140   242099518+  83  Linux
/dev/sdb2           30141       30515     3012187+   5  Extended
/dev/sdb5           30141       30515     3012156   82  Linux swap / Solaris

```

The next time I boot up I get this result from 'sudo fdisk -l':

```

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44694469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30140   242099518+  83  Linux
/dev/sda2           30141       30515     3012187+   5  Extended
/dev/sda5           30141       30515     3012156   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045568

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12748   102398278+  83  Linux
/dev/sdb2           12749       26771   112639747+  83  Linux

```

Each time I boot they are switched around. So when I mount my backup drive I must remember to run 'sudo fdisk -l' to determine which 'dev' label to use in my 'mount' command.

I have no clue why this is happening but I hope some else does. 

Possibly this has something to do with the fact that one of my hard disks is a IDE and one is a SATA.

In the meantime, if anyone else has this problem, here is the way around it.

---

### Post by gdp5701 on 2008-07-04
Post your /etc/fstab file.

---

### Post by mcduck on 2008-07-04
Yes, the device names for hard drives change depending on the order in which they get recognized and configured. That's why Ubuntu, by default, mounts drives usuing UUID's instead of the device names.

You should do the same, instead of using /dev/sda and /deb/sdb you should run "blkid" to get the correct UUID's for your partitions, and then configure their mounting in fstab using the UUID.

---

### Post by sofasurfer on 2008-07-04
Heres my /fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc           proc         defaults                    0  0  
/dev/sda1                                   /               ext3         relatime,errors=remount-ro  0  1  
#UUID=37d56b00-3d01-4379-9892-a5a1774509df  /               ext3         relatime,errors=remount-ro  0  1  
/dev/sda5                                   none            swap         sw                          0  0  
# UUID=bd7a5cbd-9bbc-4822-b403-d90d987b1d4a none            swap    sw              0       0
/dev/scd0                                   /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  

```

Heres my /mtab:

```

/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/daryl/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=daryl 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,nosuid,nodev,utf8,user=daryl 0 0
/dev/sdb1 /mnt/backuptar ext3 rw 0 0

```

My understanding is that you don't need a /dev line in /fstab if you are going to mount manually. When you mount manually your /dev line appears in /mtab as a currently mounted device and when you unmount it disappears.

---

### Post by sofasurfer on 2008-07-05
I edited my fstab file to use the uuids instead of the /dev ids. I still have to check my fdisk -l to determine whether my backup drive will be /sda or /sdb to use in my 'mount' command.

---

### Post by mcduck on 2008-07-07
> **sofasurfer said:**
> 
My understanding is that you don't need a /dev line in /fstab if you are going to mount manually. When you mount manually your /dev line appears in /mtab as a currently mounted device and when you unmount it disappears.

True. But if you want to mount the drives always into the same place and to get rid of the problem with changing device names you _will_ have to configure those drives in fstab. (Using UUID's doesn't stop the device names from changing, it allows you to always mount the same drive in same place regardless of it's device name.)

If you don't want those drives to be always mounted, add "noauto" to mount options in fstab.

Edit: by the way, if you don't want to automount the backup drive because of safety reasons I can tell you it makes no difference. As long as the drive is inside your computer and connected to PSU & motherboard it's still likely to fail together with your main drive if the PSU fails, for example. It makes no difference if the drive is mounted or not. Personally, I wouldn't consider anything that's always connected to the computer as "backup".

---

### Post by sofasurfer on 2008-07-08
Ok, I mounted the drives in fstab. For a day or 2 I could boot up and my drives would be properly named (boot=sda1,5 back=sdb1,2) and backup partitions were accessable at /mnt/backuptar and /mnt/backuprsync.

At this stage I had the boot partitions configured as UUIDs and the backups as /dev/***.

Then, tonight I come home and /backuprsync is accessable but /backuptar is NOT.
I checked fdisk and the drives are named backwards (sda instead of sdb and sdb instead of sda).

I edited fstab so all drives are listed as UUIDs and it made no differance.

Why am I having all this trouble accessing my backup drive? This makes no sense to me.

---

### Post by mcduck on 2008-07-08
> **sofasurfer said:**
> Ok, I mounted the drives in fstab. For a day or 2 I could boot up and my drives would be properly named (boot=sda1,5 back=sdb1,2) and backup partitions were accessable at /mnt/backuptar and /mnt/backuprsync.

At this stage I had the boot partitions configured as UUIDs and the backups as /dev/***.

Then, tonight I come home and /backuprsync is accessable but /backuptar is NOT.
I checked fdisk and the drives are named backwards (sda instead of sdb and sdb instead of sda).

I edited fstab so all drives are listed as UUIDs and it made no differance.

Why am I having all this trouble accessing my backup drive? This makes no sense to me.

Like I said, using UUID will not stop the device names from changing. You can't change that. Instead using UUID allows you to configure the same drive to always mount into same place, regardless of what it's device name is.

---

### Post by sofasurfer on 2008-07-08
But obviously I am NOT able to mount the drive properly whenever I want. Its a hit n miss thing. Is there by any chance a problem with having an IDE hard disk along side of a SATA hard disk? In gparted used as a boot disk my sata is recognized as a sd* and my IDE is recognized as a HD*. But in gparted under ubuntu both SATA and IDE are recognized as sd*.

---

### Post by mcduck on 2008-07-08
> **sofasurfer said:**
> But obviously I am NOT able to mount the drive properly whenever I want. Its a hit n miss thing. Is there by any chance a problem with having an IDE hard disk along side of a SATA hard disk? In gparted used as a boot disk my sata is recognized as a sd* and my IDE is recognized as a HD*. But in gparted under ubuntu both SATA and IDE are recognized as sd*.
No, there are no problems with using PATA and SATA dsks together. The confusion with the names comes from the recent change to using SATA/SCSI driver for all hard disks, including PATA ones (the developers found out thta SATA driver worked with them even better than the actual PATA driver did..). So the old way was to call PATA drives as hdX and SATA/SCSI drives as sdX, while today they are all called sdX. One more reason to use UUID instead of device names. ;)

Anyway, what's wrong with simply configuring the drive to automount into right place at boot?

If you configure all your drives in fstab, and use the "noauto" option for the backup drive (if you really feel that you need to) you shouldn't have any problems. When properly configured in fstab you should be able to mount the drive even from the Places-menu.. Also after configurin the drive in fstab you can mount the drive from command line *without using the device name*, with "sudo mount /path/to/mountpoint".

So, stop worrying about device names. You don't need them for this. :)

---

### Post by sofasurfer on 2008-07-08
Here is my fstab file...

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc              /proc          proc    defaults          0      0  

#### BOOT DRIVE ###

#T/dev/sda1                          /                ext3         relatime,errors=remount-ro  0  1  
UUID=5a09371b-94a1-4de5-8998-269be325d9a1    /        ext3         relatime,errors=remount-ro  0  1  

#/dev/sda5                                   none            swap  sw                          0  0  
UUID=bd7a5cbd-9bbc-4822-b403-d90d987b1d4a none            swap    sw              0       0

### CDROM ###

#/dev/scd0                                /media/cdrom0   udf,iso9660 user,noauto,exec,utf8    0  0  
UUID=0401a757-5481-4716-8228-cca8ce3ec010    /                ext3   defaults                    0  0

### BACKUP DRIVE ###

#/dev/sdb1                                   /mnt/backuptar   ext3    defaults                    0  0
UUID="0401a757-5481-4716-8228-cca8ce3ec010  /mnt/backuptar   ext3   defaults                    0  0

#/dev/sdb2                                   /mnt/backuprsync ext3    defaults                    0  0
UUID="3dee0578-5e82-4769-a779-858677ba893d  /mnt/backuprsync ext3   defaults                   0  0 

```

I think my problem may be 'defaults' part of the backup drive UUID lines. But I am not sure of the options that should be in there but I think it should contain a 'auto' option.

---

