---
title: "External drive is read-only, can't change"
date: 2008-06-07
forum: General Help
---

### Post by nunix on 2008-06-07
This is for 7.04.

I have an external USB drive that is being seen as read-only; I can't even change the file permission as root (by using gksudo nautilus and right-clicking on the icon). Doing some searching on my own I found a few directions for modifying fstab but this drive doesn't even appear to show up there. I don't use it that often, it's for backups.. and.. I actually need to do a backup. -.- So this is pretty frustrating..

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=143c3cff-3c24-48d9-a989-e3e513ed4fb8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=37f844bb-46fd-4965-8ec8-5c1d893d3275 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


But if I look under mount, the drive shows up as
/dev/sdb5 on /media/MEMORY LANE type ntfs (rw,nosuid,nodev,umask=222,utf8)

What the heck do I do so I can use my drive?

---

### Post by rampageoberon on 2008-06-07
This is what my mtab file says about ntfs usb drives

/dev/sda2 /media/disk fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0

Not sure if that will help you in any way, but I'm not sure, mine work similar to plug and play fortunately

---

### Post by Pjotr123 on 2008-06-07
It's probably this: you didn't "safely remove" (unmount) the external USB disk in Windows. You always have to do that: Windows writes a stop code then, which Linux needs.

Solution: let Windows "safely remove" the disk as yet. Then boot Linux again.

---

### Post by nunix on 2008-06-07
Pjotr: No go. Plugged it into an XP box, let it Safely Remove, rebooted linux (these are two seperate machines, not a dual boot), plugged drive back in, same deal.

---

### Post by kordite on 2008-06-07
I am running into the same problem with a USB external drive of mine. I think it all started when I was working with a friends Ubuntu machine that was having problems and used it to try to backup his drive. 

I have Folder access but not File access. I can save new files but cannot edit any existing files. 

My Win98 machine can read and write just fine. Normal disconnect doesn't resolve issue. Haven't had a chance to try that with an XP or Vista machine to see if there is anything to do with the so-called Windows stop code. And, like nunix, it does not appear in the fstab. It worked previously so it's not an issue with the formatting of the drive, as suggested in other threads. It's vfat.

I have the same issue with my desktop and laptop so issue is with the drive.

I tried a chmod command but it returned "Read-only file system"

---

### Post by sisco311 on 2008-06-07
Make sure you have ntfs-3g and ntfs-config installed.

```
sudo aptitude update
sudo aptitude install ntfs-3g ntfs-config
``````
gksu ntfs-config
```and check the *Enable write support for external device *box*. *

---

### Post by nunix on 2008-06-07
Did that. Still read-only.

EDIT: I tell a lie! I did the ntsf-config, but neglected to unmount/mount the drive.. did that, and it seems to work now. I also switched it to a different USB port which.. probably did nothing, but you never know.

---

### Post by sisco311 on 2008-06-07
> **nunix said:**
> Did that. Still read-only.
Did you remount the partition?

If yes post the output from:
```
mount
```
and
```
sudo fdisk -l
```

---

### Post by kordite on 2008-06-07
Actually, my problem seems to be associated with Rhythmbox. Booting up and mounting the drive, I have been able to change file names, edit files, and all that stuff but if I go into Rhythmbox, it locks the drive. I'm going to investigate further and if I can't figure it out I'll create a new thread.

---

