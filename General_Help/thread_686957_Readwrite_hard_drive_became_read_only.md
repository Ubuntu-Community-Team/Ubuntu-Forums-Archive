---
title: "Read/write hard drive became read only"
date: 2008-02-03
forum: General Help
---

### Post by Stoodle on 2008-02-03
I was trying to download stuff from the Internet and onto my external hard drive. OUT OF NOWHERE, it went from read/write to read only. It said I didn't have permissions (all of the sudden) so I went to root. Then it said it was read only. I tried chmod 777 and it was a "read-only filesystem". It's vfat (should I change it? What's the best one that can be read across all OSs?) Also, how do I change the name of an external hard drive?

---

### Post by geraldm on 2008-02-03
Check for a line in your /etc/fstab for that device that mounts it as read-only.
Also, the permissions on the device must be set to allow read/write.
If you had write permission earlier, there is likely something that was done that allowed
the change to occur; it does not come out of nowhere.

Changing the permissions of others to allow read/write/execute is asking for trouble; allowing that while also allowing internet access allows foolishness.  It is better to disallow others, and create a new group, and provide controlled behavior to  trusted users.

Gerald

---

### Post by Stoodle on 2008-02-04
I'm not really sure how to make groups. Also, I can't find it in fstab actually even though it mounts. But how do I change it from read only to read and write?

Here's the fstab file, it should mount as /media/ILOVEYOU (girlfriend named it :oops:)

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda9
UUID=f8911c5b-5ebf-4eae-938e-6ec00ccd2a66 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=98381371-8aae-4180-9112-87b1783aca8f /boot           ext3    defaults        0       2
# /dev/hda7
UUID=175c2e46-aabe-4fbf-a591-bf2cb73a278e /home           ext3    defaults        0       2
# /dev/hda1
UUID=3F51-2587  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=12B8A58AB8A56D43 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=99c43720-1986-4ffa-8bc9-5a20449d96d5 /usr            ext3    defaults        0       2
# /dev/hda8
UUID=a3edf542-acca-4056-9b2a-0b1d7d19b156 /var            ext3    defaults        0       2
# /dev/hda5
UUID=bc9755c8-b6b2-4b1a-8941-56c6897de281 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc2 /media/iPod vfat
nosuid,noauto,nodev,rw,umask=077,gid=1000,user,defaults,noatime,iocharset=utf8 0 0

```

---

### Post by Stoodle on 2008-02-06
I think that what happened was that I lost power in my room so it could have messed up the hard drive. Do you guys think I can fix it with fsck.vfat?

---

### Post by geirha on 2008-02-06
FAT-filesystems are best left for M$ software to check and fix, so if you have access to a windows box, run scandisk from there. If not, then try with fsck.vfat. It sounds plausible to me that the power outage caused this problem.

---

### Post by Stoodle on 2008-02-06
Yeah, I'll try scandisk. Where can I find it?

---

### Post by geirha on 2008-02-08
> **Stoodle said:**
> Yeah, I'll try scandisk. Where can I find it?

You probably just right-click the device in "My Computer", and there should be an option for checking the disk. In the old days when I was using windows, that program was called scandisk, might be called something else now.

---

### Post by z-itou16 on 2008-02-08
hello everyone

 > # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda9
UUID=f8911c5b-5ebf-4eae-938e-6ec00ccd2a66 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=98381371-8aae-4180-9112-87b1783aca8f /boot           ext3    defaults        0       2
# /dev/hda7
UUID=175c2e46-aabe-4fbf-a591-bf2cb73a278e /home           ext3    defaults        0       2
# /dev/hda1
UUID=3F51-2587  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=12B8A58AB8A56D43 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=99c43720-1986-4ffa-8bc9-5a20449d96d5 /usr            ext3    defaults        0       2
# /dev/hda8
UUID=a3edf542-acca-4056-9b2a-0b1d7d19b156 /var            ext3    defaults        0       2
# /dev/hda5
UUID=bc9755c8-b6b2-4b1a-8941-56c6897de281 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc2 /media/iPod vfat
nosuid,noauto,nodev,rw,umask=077,gid=1000,user,defaults,noatime,iocharset=utf8 0 0

to be honest i dont see any mount point "/media/ILOVEYOU" there. (that is so cute of your gfriend)

i had read that windows file system cannot be chown nor chmod since it is define by umask. i think you may want to have the xhdd (external hdd) auto(meaning it will be mount at boot) or maybe i am wrong. 

what i will do first is to have it as defaults. if that doesnt work then auto,rw,user,sync. if that still is ro, then add "umask=0000"

let us know. thank you

---

### Post by vanadium on 2008-02-08
Because the vfat file system has no secrets, it is perfectly safe and acceptible to use fsck.vfat (just fsck will do: it cals fsck.vfat when detecting a fat volume). Indeed, according to your /etc/fstab, tehre is one fat drive mounted on /media/hda1.

---

### Post by Stoodle on 2008-02-08
Why can I read/write in Windows but not in Linux?

Also, could I get an explanation of what exactly fstab does? How does my ext hd automount without being in fstab? I thought it had to be there to be automounted. Also, why where could I find the ext hd to remount it if I chose?

What does some of the stuff in fstab mean like gid and noatime(guessing that's north america time but I don't know the purpose)?

What's the difference of something showing up under /dev vs /media?

---

### Post by geirha on 2008-02-08
> **Stoodle said:**
> Why can I read/write in Windows but not in Linux?

Also, could I get an explanation of what exactly fstab does? How does my ext hd automount without being in fstab? I thought it had to be there to be automounted. Also, why where could I find the ext hd to remount it if I chose?

What does some of the stuff in fstab mean like gid and noatime(guessing that's north america time but I don't know the purpose)?

What's the difference of something showing up under /dev vs /media?

fstab is short for file system table. It's a list of devices, where to mount them, what options to mount them with and whether to do file system checks on them. The man-page for mount and fstab explains this, including what options like gid and noatime mean. ```
man fstab
man mount
```

It doesn't need to have an entry in fstab to be automounted. You can have an entry for it in fstab if you need to have different permissions and the likes.

The hal daemon detects when an usb mass storage device is inserted, then checks if there's an entry in fstab, and mounts it accordingly, if not, it will be mounted to /media/<label>/ with write permissions for the user currently logged in.

What's the output of the following two commands when the hard drive has been automounted?
```
mount
ls -ld /media/ILOVEYOU
```

---

### Post by chrisccoulson on 2008-02-08
^^^Yes, what he said. Just another point, fstab is where you normally define *static* filesystems - ie, filesystems that are usually always there (such as internal hard drives).

The behaviour of your external drive that you describe (suddenly going read-only), is normal behaviour when errors are detected on the disk, and should happen with any filesystem. This is a damage limitation mechanism, and you should run fsck on it to fix it - but make sure the disk is unmounted first.

---

### Post by Stoodle on 2008-02-08
How do I access the ext hd after unmounting? I can't find it after I unmount.

---

### Post by geirha on 2008-02-09
> **Stoodle said:**
> How do I access the ext hd after unmounting? I can't find it after I unmount.

You want to run fsck on it?

When it's mounted, type "mount" in a terminal, find the line for the external hdd and note the device node name. Something like /dev/sdb1 probably. Unmount, and use that as argument for fsck.

As another option you can run "sudo fdisk -l" (regardless of it being mounted or not) and identify the device node name by the size of the disk and partition type.

---

### Post by Stoodle on 2008-02-09
Why can't I remount? I found it and it said

```

 mount /dev/sda1
[mntent]: warning: no final newline at the end of /etc/fstab
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

```

Also, during fsck, I don't know what happened completely.
```

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action

```
I chose 1) but I don't know what it was saying or what actually happened when I chose 1.

```

/Kenshin  and
/Recycled/Df5.rar
  share clusters.
1) Truncate first to 0 bytes
2) Truncate second to 0 bytes

```
What does that mean? I'm guessing truncating basically means delete.
What are clusters and what are cluster chain lengths?

```

Free cluster summary wrong (14222754 vs. really 14222784)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sda1: 87682 files, 1035570/15258354 clusters

```

What does it mean by file system unchanged and the Free cluster summary?

---

### Post by chrisccoulson on 2008-02-09
I'm confused as well. Are you really sure your external drive is /dev/sda1?

With the drive connected and mounted (just plug it in), could you post the output of:
```
cat /etc/mtab
```

It will be easier for someone to help you then

---

### Post by Stoodle on 2008-02-09
```

/dev/hda9 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/hda3 /boot ext3 rw 0 0
/dev/hda7 /home ext3 rw 0 0
/dev/hda1 /media/hda1 vfat rw,utf8,umask=007,gid=46 0 0
/dev/hda2 /media/hda2 fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/hda6 /usr ext3 rw 0 0
/dev/hda8 /var ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sda1 /media/ILOVEYOU vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0

```

---

### Post by chrisccoulson on 2008-02-09
Did you unmount it before running fsck? If not, you need to do
```
sudo umount /dev/sda1
```

Then run fsck:
```
sudo dosfsck -r -v /dev/sda1
```
The -r option, from 'man dosfsck':
```
       -r     Interactively  repair  the  file  system.  The user is asked for
              advice whenever there is more than one approach to fix an incon&#8208;
              sistency.


```
If you want to automatically repair, then substitute -r with -a:
```
       -a     Automatically repair the file system. No  user  intervention  is
              necessary.   Whenever  there  is more than one method to solve a
              problem, the least destructive approach is used.

```

---

### Post by Stoodle on 2008-02-09
I unmounted and ran sudo fsck /dev/sda1. I know that I had the right one because it was talking about files that were on it. Doesn't fsck do the same thing with or without -r?

---

### Post by chrisccoulson on 2008-02-09
> **Stoodle said:**
> I unmounted and ran sudo fsck /dev/sda1. I know that I had the right one because it was talking about files that were on it. Doesn't fsck do the same thing with or without -r?

I believe that it defaults to the -r option. Try using the autorepair option:
```
sudo dosfsck -a -v /dev/sda1
```

---

### Post by chrisccoulson on 2008-02-09
Actually, if you don't specify the -r option, it doesn't attempt to repair it. So you need to specify either -r or -a. From dosfsck man page:
```
If -a and -r are absent, the file  system  is  only  checked,  but  not
       repaired.
```

---

### Post by Stoodle on 2008-02-09
What options do you guys suggest I use while doing fsck? And what are clusters?

---

### Post by chrisccoulson on 2008-02-09
You should do:
```
sudo dosfsck -r -v /dev/sda1
```

---

### Post by Stoodle on 2008-02-09
Uh, I only did sudo fsck -r /dev/sda1. Is that okay? I think it made changes but the question is, how do I remount it? It says
```

[mntent]: warning: no final newline at the end of /etc/fstab
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

```

---

### Post by chrisccoulson on 2008-02-09
Omitting the -v option is okay. That option just increases verbosity.

You can't mount it using mount /dev/sda1 because the entry is not in your fstab. The easiest way to remount it again is to just unplug it, wait a few seconds and then plug it back in again

---

### Post by Stoodle on 2008-02-22
Well, it's giving me these problems again. I've managed to get it to automount by creating an fstab entry. However, apparently I did something wrong because I'm now getting this.

```

mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

```Here's my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda9
UUID=f8911c5b-5ebf-4eae-938e-6ec00ccd2a66 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=98381371-8aae-4180-9112-87b1783aca8f /boot           ext3    defaults        0       2
# /dev/hda7
UUID=175c2e46-aabe-4fbf-a591-bf2cb73a278e /home           ext3    defaults        0       2
# /dev/hda1
UUID=3F51-2587  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=12B8A58AB8A56D43 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=99c43720-1986-4ffa-8bc9-5a20449d96d5 /usr            ext3    defaults        0       2
# /dev/hda8
UUID=a3edf542-acca-4056-9b2a-0b1d7d19b156 /var            ext3    defaults        0       2
# /dev/hda5
UUID=bc9755c8-b6b2-4b1a-8941-56c6897de281 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc2 /media/iPod vfat
nosuid,noauto,nodev,rw,umask=077,gid=1000,user,defaults,noatime,iocharset=utf8 0 0
**_/dev/sda1 /media/Seagate vfat rw,auto,user, umask=000 0 0_**

```

---

### Post by chrisccoulson on 2008-02-23
What happens if you remove the entry from your fstab, then unplug and reconnect the drive? For automounting, you shouldn't *need* an entry in your fstab. For one thing, you can not guarantee that your external drive will get the same device node next time you reconnect it (it depends on what else you have connected to the machine).

Your fstab is primarily for *static* filesystems, as opposed to removable media. Unless you need to specify any unusual mount options to get the device to work, you shouldn't need to add removable devices to your fstab.

You have specified the 'auto' option for your removable device, which is wrong. this means that mount will spit out an error if the device isn't connected or can't be found at /dev/sda1. This is probably the error you're seeing now.

Also, the line I've highlighted in red is wrong - the device node is incomplete. The line you've added for your removable drive (highlighted orange) also has an error - there is an extra whitespace between 'user,' and 'umask='

```
# /etc/fstab: static file system information

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda9
UUID=f8911c5b-5ebf-4eae-938e-6ec00ccd2a66 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=98381371-8aae-4180-9112-87b1783aca8f /boot           ext3    defaults        0       2
# /dev/hda7
UUID=175c2e46-aabe-4fbf-a591-bf2cb73a278e /home           ext3    defaults        0       2
# /dev/hda1
UUID=3F51-2587  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=12B8A58AB8A56D43 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=99c43720-1986-4ffa-8bc9-5a20449d96d5 /usr            ext3    defaults        0       2
# /dev/hda8
UUID=a3edf542-acca-4056-9b2a-0b1d7d19b156 /var            ext3    defaults        0       2
# /dev/hda5
UUID=bc9755c8-b6b2-4b1a-8941-56c6897de281 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
[COLOR="Red"]/dev/           /media/floppy0  auto    rw,user,noauto  0       0[/COLOR]
/dev/sdc2 /media/iPod vfat
nosuid,noauto,nodev,rw,umask=077,gid=1000,user,defaults,noatime,iocharset=utf8 0 0
[COLOR="Orange"]/dev/sda1 /media/Seagate vfat rw,auto,user, umask=000 0 0[/COLOR]
```

---

### Post by Stoodle on 2008-02-23
Well, it seems that my external hard drive does load in the same place all the time. With no entry in fstab, it won't mount period.

Also, in that red line, there's nothing about umask and whitespace isn't an issue in fstab. I also didn't create that line about the floppy.

---

### Post by Stoodle on 2008-02-23
Oh, I see what you were saying...still, I don't know how to access my external hard drive otherwise.
How do I figure out what device it is?

---

### Post by chrisccoulson on 2008-02-23
There's no reason why the device shouldn't automount without the entry in your fstab. Without the entry in your fstab, type the following in to a terminal:
```
tail -f /var/log/syslog
```
Monitor the output of this as you connect the drive to the computer. Then post the output here.

---

