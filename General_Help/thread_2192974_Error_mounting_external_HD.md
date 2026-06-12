---
title: "Error mounting external HD"
date: 2013-12-10
forum: General Help
---

### Post by Robbyx on 2013-12-10
The error message is:

[I]Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc2 is already mounted on /media/system_and_data_on_external_hd
mount failed[/I]

How do I stop the error message as it is referring to drive letters that are no longer in fstab, but are in mtab. I understand from other queries that mtab is generated internally but I do not what is doing it.


mtab shows a nuber of drives that are no longer on the system. 

```
/dev/sda2 / ext4 rw,errors=remount-ro 0 0
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
/dev/sda5 /home ext4 rw 0 0
/dev/sda6 /media/mydocs ext4 rw 0 0
/dev/sda7 /media/audio_visual ext4 rw 0 0
/dev/sdc3 /media/old_back_ups_on_external_HD ext4 rw 0 0
/dev/sdc2 /media/system_and_data_on_external_hd ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/robins/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=robins 0 0
/dev/sdb1 /media/SPARE4 vfat rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks 0 0
/dev/sdb3 /media/old_back_ups_on_external_HD ext4 rw 0 0
/dev/sdb2 /media/system_and_data_on_external_hd ext4 rw 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
```

Fstab shows

```
# /etc/fstab: static file system information. 
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9f5074c3-e7d5-4d39-bb80-6191188ded9e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=803eff26-0660-46d4-8cbd-8f182f904ed5 /home           ext4    defaults        0       2
# /dev/sda6: LABEL="mydocs" 
UUID=cb25d8db-9697-4245-acdd-90db9cf655c6 /media/mydocs ext4 defaults        0       2
# /dev/sda7: LABEL=audio_visual 
UUID=224b1762-f128-4b07-9039-a77bd2f4a7ef /media/audio_visual ext4 defaults        0       2
# swap was on /dev/sda8 during installation
UUID=389c68f7-5a16-4625-aabe-02ede5569695 none            swap    sw              0       0


#/dev/sdb1: 
# UUID=E0D0-35DF /media/flash_drive1 vfat defaults 0   2 

# /dev/sde1: LABEL=SPARE4 UUID=13AC-9C9E vfat 
# /dev/sde2: LABEL=xhd system data 
UUID=23fcb4e3-c94e-44de-b7a9-105da58918c6 /media/system_and_data_on_external_hd ext4 defaults        0       2
# /dev/sde3: LABEL=xhd old bacs 
UUID=c99be12f-3a2d-4411-ab7c-5696167482dc /media/old_back_ups_on_external_HD ext4 defaults        0       2

```

blkid

```
robins@office:~$ sudo blkid
[sudo] password for robins: 
/dev/sda1: UUID="389c68f7-5a16-4625-aabe-02ede5569695" TYPE="swap" 
/dev/sda2: LABEL="Ubuntu Sys Activ" UUID="9f5074c3-e7d5-4d39-bb80-6191188ded9e" TYPE="ext4" 
/dev/sda5: LABEL="Home" UUID="803eff26-0660-46d4-8cbd-8f182f904ed5" TYPE="ext4" 
/dev/sda6: LABEL="mydocs" UUID="cb25d8db-9697-4245-acdd-90db9cf655c6" TYPE="ext4" 
/dev/sda7: LABEL="audio_visual" UUID="224b1762-f128-4b07-9039-a77bd2f4a7ef" TYPE="ext4" 
/dev/sdb1: LABEL="SPARE4" UUID="13AC-9C9E" TYPE="vfat" 
/dev/sdb2: LABEL="xhd system data" UUID="23fcb4e3-c94e-44de-b7a9-105da58918c6" TYPE="ext4" 
/dev/sdb3: LABEL="xhd old bacs" UUID="c99be12f-3a2d-4411-ab7c-5696167482dc" TYPE="ext4" 
robins@office:~$ 

```

Robin

---

### Post by Bashing-om on 2013-12-10
Robbyx; Hello ;

Not at all obvious to me either why the system is seeing a device "sdc" .
The UUIDs are mapped to sdb2 and sdb3.

May we see the output of terminal command:
```

ls -la /media

```
See if sense can be made of this ??

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Robbyx on 2013-12-10
robins@office:~$ ls -la /media
total 48
drwxr-xr-x 12 root   root   4096 Dec 10 18:52 .
drwxr-xr-x 25 root   root   4096 Dec  4 22:27 ..
drwxr-xr-x 35 robins robins 4096 Nov 13 22:38 audio_visual
drwx------  2 root   root   4096 Nov  8 19:13 c99be12f-3a2d-4411-ab7c-5696167482dc
drwxr-xr-x  2 root   root   4096 Nov 10 20:14 flash_drive1
drwxr-xr-x 23 robins robins 4096 Dec 10 19:15 mydocs
drwx------  2 root   root   4096 Aug 26 10:51 NEW VOLUME
drwxr-xr-x 10 robins robins 4096 Nov  8 22:03 old_back_ups_on_external_HD
drwxr-xr-x  2 root   root   4096 Nov  2 14:22 spare4
drwx------  3 robins robins 4096 Jan  1  1970 SPARE4
drwxr-xr-x  3 root   root   4096 Sep 26 22:04 system_and_data_on_external_hd
drwx------  2 root   root   4096 Aug 26 13:33 WINXPSP3OEM
robins@office:~$

---

### Post by Bashing-om on 2013-12-10
Robbyx; Nope,

Still do not see how "sdc" comes into the picture.
The UUIDS are mapped to the second hard drive.
What does the system show as mounted ?
```

mount

```
Do you get the expected file listings from:
```

ls -la /media/system_and_data_on_external_hd
ls -la /media/old_back_ups_on_external_HD

```
Which should be the contents of the 2 partitions of that second drive.
Going 'round and around in my mind, but so far as I am aware, a mount point is a mount point is a mount point.

[INDENT][INDENT]sometimes I wonder, othertimes I just do not know
[/INDENT][/INDENT]

---

### Post by drmrgd on 2013-12-10
My first thought on this earlier was "did you unmount those partitions before you created the new fstab entry?"  I see the mount points you mentioned were on sdc located in /media:

```

robins@office:~$ ls -la /media
total 48
drwxr-xr-x 12 root root 4096 Dec 10 18:52 .
drwxr-xr-x 25 root root 4096 Dec 4 22:27 ..
drwxr-xr-x 35 robins robins 4096 Nov 13 22:38 audio_visual
drwx------ 2 root root 4096 Nov 8 19:13 c99be12f-3a2d-4411-ab7c-5696167482dc
drwxr-xr-x 2 root root 4096 Nov 10 20:14 flash_drive1
drwxr-xr-x 23 robins robins 4096 Dec 10 19:15 mydocs
drwx------ 2 root root 4096 Aug 26 10:51 NEW VOLUME
**[COLOR=#ff0000]drwxr-xr-x 10 robins robins 4096 Nov 8 22:03 old_back_ups_on_external_HD[/COLOR]**
drwxr-xr-x 2 root root 4096 Nov 2 14:22 spare4
drwx------ 3 robins robins 4096 Jan 1 1970 SPARE4
[COLOR=#ff0000]**drwxr-xr-x 3 root root 4096 Sep 26 22:04 system_and_data_on_external_hd**[/COLOR]
drwx------ 2 root root 4096 Aug 26 13:33 WINXPSP3OEM

```

If you try to get a directory listing on those mount points, do you get any results?  Also, what happens when you try to unmount them:

```

sudo umount /media/system_and_data_on_external_hd

```

It's try that fstab should have created the mtab file and those entries should not be there.  But, perhaps something gets hung up if you don't unmount the partitions before messing with their fstab entries?  Just a bit of a shot in the dark.

---

