---
title: "/media has my external drive mounted and won't let go"
date: 2012-10-16
forum: General Help
---

### Post by finny388 on 2012-10-16
I'm running Voyager 64bit which is basically xubuntu on an 11GB partition.

After installing humble bundle 6 I ran out of space (/ and home on same partition)

I successfully expanded the space with a live boot of gparted last night to 16GB.

Tonight I'm out of space again.

I have an external drive regularly attached that Deluge uses.

I unattached the drive, rebooted, and find part of it still in /media, I guess as much as would fit (properties said 20GB (??))

I probably manually mounted it some time ago when trying to learn how to have it mount automatedly.

How to unmount and just have it mount when attached and not use local space?

---

### Post by Bashing-om on 2012-10-16
finny388; Hi !

Firstly, I would be concerned with the disk space usage, and start with checking my log files for huge ones.

media mounts: do you properly unmount the drive prior to unplugging it?
Is there an entry in /etc/fstab file for media ? As usb devices are auto detected and mounted to media I do not believe there is a need to list the device in fstab ?


[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by finny388 on 2012-10-16
thanks
>  Firstly, I would be concerned with the disk space usage, and start with checking my log files for huge ones.

It appears that /media is the space problem. Many files/folders for my external drive are mirrored there.

I don't know how to check logs

here is my fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=7d503083-eac3-4bb7-af6a-e05cca8157f3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=49d823b5-af8b-494d-86be-df3d29a41636 none            swap    sw              0       0
# FH
#/dev/sda11     /media/LOCAL_HD ext4    umask=000       0       0
#/dev/sdb1      /media/HITACHI  ntfs-3g umask=000       0       0
#HITACHI
#UUID="482EDE3C2EDE22AC"
#LOCAL_HD
#UUID="8484529f-db3d-40dd-b950-8bcf2030cfa6"

```

---

### Post by Bashing-om on 2012-10-17
finny388; yuk!

fstab entry for sda11 is invalid mixture of ubuntu/windows options.

and again I do not see why you need to mount the usb devide in fstab ( i run usb drive formated fat32 with no probs at all auto mounting)
related: is sdb1 the usb drive ?
This is a great tutorial on fstab:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
and a primer:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

lets look at what your partitions look like and your UUID assignments;
terminal code:
```
sudo fdisk -l
sudo blkid

```definitely  check log file sizes:
```
ls -la /var/log/
```anything "large" :
```
cat /var/log/<filename> | less
```to get an idea of what is going on.
then all old files may be safely deleted.
[INDENT]one step at a time gets it done ==>BDQ
 
[/INDENT]

---

### Post by finny388 on 2012-10-17
yes, sdb1 was the external usb drive (below it is my usb key with gparted)

```
> sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29133921

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   104856254    52427103+   7  HPFS/NTFS/exFAT
/dev/sda2       104856255   136327589    15735667+  1c  Hidden W95 FAT32 (LBA)
/dev/sda3       488355840   488397167       20664   ef  EFI (FAT-12/16/32)
/dev/sda4       136331262   482211839   172940289    f  W95 Ext'd (LBA)
/dev/sda5       136331264   146571263     5120000   82  Linux swap / Solaris
/dev/sda6       146573312   171149311    12288000   83  Linux
/dev/sda7       171151360   195727359    12288000   83  Linux
/dev/sda8       195729408   220305407    12288000   83  Linux
/dev/sda9       233971712   269461503    17744896   83  Linux
/dev/sda10      269463552   482211839   106374144   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00041fd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7849447     3924693    b  W95 FAT32

```
```
> sudo blkid
/dev/sda1: LABEL="Windows7" UUID="D074D6AA74D69298" TYPE="ntfs" 
/dev/sda2: LABEL="RECOVERYM-^UGV" UUID="86F4-D40A" TYPE="vfat" 
/dev/sda5: UUID="49d823b5-af8b-494d-86be-df3d29a41636" TYPE="swap" 
/dev/sda6: LABEL="MINT13_XFCE" UUID="13f65ba2-df3f-4823-9f64-3560b9cee6e0" TYPE="ext4" 
/dev/sda7: LABEL="MINT12_KDE" UUID="24b232e3-341f-48d7-b602-4d32a822ce30" TYPE="ext4" 
/dev/sda8: LABEL="UBUNTU1204" UUID="af948a83-eadb-46e1-94fa-8629271a7b0b" TYPE="ext4" 
/dev/sda9: LABEL="VOYAGER" UUID="7d503083-eac3-4bb7-af6a-e05cca8157f3" TYPE="ext4" 
/dev/sda10: LABEL="LOCAL_HD" UUID="8484529f-db3d-40dd-b950-8bcf2030cfa6" TYPE="ext4" 
/dev/sdb1: LABEL="GPARTED" UUID="8616-CB80" TYPE="vfat"
```

ls -la /var/log/

Largest log file is 1.7M. The rest are less than 1M at 15K, 40K, a couple 500K

```
> cat /var/log/<filename> | less
bash: syntax error near unexpected token `|'
```

I do know that all the space used up is in /media. There are many large files in there. I don't need them.

Do I just delete the folder HITACHI and all its contents or do I have to unmount it or both? (HITACHI is the drive name of my Hitachi external harddrive)

---

### Post by Bashing-om on 2012-10-17
I am looking... may take me a while to digest this ... and is late here my time, I am tired and at this point I tend to make stupid judgment calls, so will look this over and advise in my AM.
Obviously will have to edit /etc/fstab.. I will be careful in my advisement.

I notice the boot flag is set for the sdb1 usb device, are you booting ubuntu from the device ?

sda11 ? is that to be a shared data partition ? and shared to all 3 operating systems - I see mint, windows and ubuntu ?

The current /media folder ..insure all are duplicates and as far as correcting fstab --- delete everything. If required we will make a mount point there later.
[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by finny388 on 2012-10-17
Thanks Bashing, I was nodding off myself

regarding fstab, I believe all my manual entries are commented out. Isn't the that the hash sign?

I don't boot from the Hitachi (but to make things confusing, since unplugging the Hitachi, and plugging in my usb key to do live gparted, it has now been assigned sdb1, which of course I boot from)

sda11 is meant to be seen by all as is the hitachi

all the files in /media are duplicates (HITACHI is the only sub folder)

i'll be home again tonight to try the unmount/delete.

thanks again

---

### Post by Bashing-om on 2012-10-17
You are correct. The "#" sign "comments" out the line. They are irrelevant at this time.

sda11: no longer exist and also is irrelevant.
sda8: What is it ?(/home for ubie??) As it is formated "ext4" windows can not recognize it  ...If it is to be a shared directory --will require reformatting to  (suggestion) ntfs.
sda10: ?? same same->What is it ? As it is formated "ext4" windows can not recognize it ...If it is to be a shared directory --will require reformatting to (suggestion) ntfs.
Depending on what you want to do with the sada8/sda10 partitions may need to add them to /etc/fstab.

With the /media/ directory cleaned out, neglecting sda8/sda10 at this time; I expect you to be looking in good shape.

Looking at things, all I see  to deal with is the sda8 and sda10 partitions.

your system as now:
windows is partitions 1,2,3,4
swap for mint and ubuntu partition 5
mint partitions 6 and 7 each with different desk tops
ubie 12.04 partition 8 -> presently unassigned
ubie 12.04 partition 9 as root
unknown partition 10.

If sda8 and 10 partitions are "data" partitions: This is how I have configured my system; For your consideration:
[INDENT] I have my "data" partitions separate and isolated from the rest of my system by having my mount points in the /mnt/ directory and only mounting these partitions ondemand->
```
sudo mkdir /mnt/backup
sudo mount /dev/sdb1 /mnt/backup
sudo chown USER_NAME:USER_NAME /mnt/backup/<anysub-folders>

```when I am done I manually un-mount the partitions:
```
sudo umount /mnt/backup
```backup is my reference point..make yours to whatever reference you want to use.
[/INDENT][LEFT]Do you concur ? If so, we proceed to see what you want to do with sda8 and sda10.[INDENT][INDENT]one step at a time ==> BDQ

[/INDENT][/INDENT][/LEFT]
[INDENT]
[LEFT]
[/LEFT]
[/INDENT]

---

### Post by finny388 on 2012-10-17
When you mount:
```
sudo mount /dev/sdb1 /mnt/backup
```

does it copy sdb1 files to /mnt/backup or does /mnt/backup just point to sdb1?

I thought it was just pointing but my "backup" seems to have copied until the drive was full (I have 4KB available).

First things first: do I umount /media/HITACHI or delete HITACHI?

By the way, I don't understood why my laptop is still working with only 4k available. (df -h  shows 4k avail.)

For your consideration my setup is like this:
Partitions
1-4 Windows
5 Swap for the below OS's
6 experimental OS (for fun)
7 experimental OS (for fun)
8 Ubuntu 12.04 (was Main)
9 Voyage (Now Main)
10 to be assigned (probably to merge this Ubuntu 12.04)
11 Temp Local Storage (temporary, when on the road)

Main storage is the Hitachi external hard drive (occasionally backed up to another external drive) 
:)

---

### Post by Bashing-om on 2012-10-17
This is basic simplicity:
"sudo mkdir /mnt/backup" -> makes an attachment to the root file system such that the system is aware of the directory.
"sudo mount /dev/sdb1 /mnt/backup tells the system we want access to the filesystem at this point, through that attachment.
These assignments do not copy anything at all, only sets up reference points.
Backup is my reference name, can be anything ...such as "hitachi" if you like.

If you desire to mount through /media ...there is no need for an explicit mount point, as the system automagically mounts the usb device upon insertion. So if you are referring to delete a mount point for "HITACHI" in media ...yes you may delete it ...
As the device is automagically mounted there is no need for an entry in fstab....

My example mounting is in reference to what you want to do with the present sda8/10 partitions.

As to only having 4k of overhead --like you I do not see how it can operate (lots of ram ?)

sda11 ...on last "fdisk" did not exist.

a last point to make here ...before removing a usb device it must be unmounted, The easiest method is via the file manager right click the icon and choose "safely remove device" (I have to do this twice for some reason I have nor explored).. The manner in which linux processes files is a caching method, all files are not written/closed until the device is unmounted, then the cache is cleared/flushed and open files closed. Only then can the device be un-attached.

[INDENT]I hope I am Helping <==BDQ

[/INDENT]

---

### Post by finny388 on 2012-10-17
ubuntu automagically mounted things to /media
in my experience

turns out my external drive is not mounted:
```
> mount
/dev/sda9 on / type ext4 (rw,errors=remount-ro)
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
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
gvfs-fuse-daemon on /home/frank/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=frank)
/dev/sda10 on /media/LOCAL_HD type ext4 (rw,nosuid,nodev,uhelper=udisks)

```

I'm pretty sure this is what happened:
I tried to get (let's just call my ext drive hitachi) hitachi to mount automatically through fstab - that's a fact, I don't know what that has to do with this.

Guessing: At some point Deluge didn't see hitachi and created its own files as its default path is /media/HITACHI then it started downloading and filling my hard drive. Because going through the files, there are dozens of empty folders and the only real files are recent downloads. though there are 3 folders there that Deluge has nothing to do with.

Well I'm going rm the files and the plug my hitachi back in and see what happens.

---

### Post by finny388 on 2012-10-17
whoa rm is fast
just deleted 9GB in the blink of an eye

got space? yup.

now to plug in...

okay

things look back to normal

I use xmbc. Everytime I log in and run it can't see the files.
So i go into Thunar, click on the drive (automagically mounting it) and return to xmbc and all is well.

I was just hoping hitachi would stay mounted whenever plugged in. It only seems to mount when I open it a file browser. Is this where fstab comes in?

---

### Post by Bashing-om on 2012-10-17
That is a fact on only mounting through /media ->file manager(usb devices). If you want the usb mounted through fstab ...can be done, will have to jump through some hoops to make it happen.....
 Right off the top of my head I do not recall how...the fstab entry can only have validation if the drive is inserted else your log files fill up with errors and other unwanted side affects. trying to recall about the fstab's mount options ...The important thing is there is a way, will do some research and see what I can come up with.

rm files: yeah, the way linux deals with files is a wonder in it's self (just delete the pointers and free up the inode, no messing around coping data for nothing).

-------------------------------
In my efforts to assist: ->remaining to be done--
1. mount usb device through fstab
2. mount sda8 (does it still have a valid operating system on it ??)
3.mount sda10 Perhaps make it a shared partition between deluge,ubuntu,mint and windows ????? (re -partition to ntfs if so)
4. Do you want to make a sda11 partition ?

Am I all squared away at this time ?
[INDENT]how bout that <==BDQ

[/INDENT]

---

### Post by Wim Sturkenboom on 2012-10-18
> **finny388 said:**
> 
I unattached the drive, rebooted, and find part of it still in /media, I guess as much as would fit (properties said 20GB (??))
That is more than likely the result of a failed mount (e.g. your disk was not connected and deluge started writing there).

Just delete the content (make sure the drive is not connected :))

Edit
I see that you already might have figured that out.

---

### Post by Bashing-om on 2012-10-18
@ Wim Sturkenboom Tks, appreciate others looking over my shoulder - correct me when I am in error !

@ finny388: On target, did the homework, and here is my suggestion for the usb device:
Lets make the mount point in /media -> greater versitility as shows up when mounted in both the places pane and the desktop; thus:

plug in the usb drive and:
verify the uuid (again !):
```
ls /dev/disk/by-uuid -lah
``````
sudo mkdir /media/HITACHI
```make a back-up of the current /etc/fstab -> cause anything can happen !
```
cp /etc/fstab /etc/fstab-old
```now for our edit in /etc/fstab:
```
gksudo gedit /etc/fstab
```copy/paste this as one line line into /etc/fstab:
UUID=8616-CB80 /media/HITACHI vfat user,uid=1000,gid=100,utf8,dmask=027,fmask=137   0  0

is the uuid correct ?
save the changes .. exit out of gedit .....reboot ( I prefer re-boot rather than re-mounting).

Thanks to [COLOR=navy]bodhi.[/COLOR][COLOR=darkgray]zazen [/COLOR]and others !

Please to advise on the results.
[INDENT]after all these years->still learning <==BDQ

[/INDENT]

---

### Post by finny388 on 2012-11-17
Thank you for all your help bashing and all
Sorry such a late reply

I tried to add to fstab as per your instructions bashing-om.

It failed to mount which halted boot with a "Status 32".

This is the line I added:```
UUID=482EDE3C2EDE22AC /media/HITACHI vfat user,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0
```

It is an NTFS drive. Maybe vfat caused the error.

---

### Post by Bashing-om on 2012-11-17
Well, that is a distinct possibility....I go look at the epitome of fstabs:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
and:

[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[INDENT]I'll Be Back <== BDQ

[/INDENT]

---

### Post by Bashing-om on 2012-11-17
I'm Back ->
I agree I should use NTFS hummm do not know why/how I missed that.
1. verify again the proper UUID as discrepancies between what we perceive:
with the usb drive connected, determine the device's UUID:
```
ls /dev/disk/by-uuid -lah
```or this may be more readable:
```
sudo blkid
```2. Insure that the package "ntfs-3g"  is installed (search in synaptic)
3. copy paste this line into /etc/fstab:
```
UUID=youruuidnbr /media/HITACHI ntfs-3g auto,users,permissions 0 0
``` courtesy of  bodhi.zazen; insure a space delimiter after the UUID. 
4. re-mount -> looking for errors
```
sudo mount -a
```[INDENT]looking good ? <== BDQ

[/INDENT]

---

### Post by finny388 on 2012-11-17
looking good!

ntfs-3g wasn't installed so glad you mentioned that. maybe that was my fstab problem all along. (but then not sure what Ubuntu was doing 'automagically')

mount -a complained that the folder didn't exist so created it and voila - it mounted.

Then tried a reboot and no problems.

Thanks Bashing-om! I learned a lot and finally getting this running automatically is a great feeling.

:)

---

### Post by Bashing-om on 2012-11-17
Hey ...In spite of my faults, we DO good work !

I am ever pleased that you are, and your thanks  gratifys .

[INDENT][INDENT]happy ubuntu'n

[/INDENT][/INDENT]

---

