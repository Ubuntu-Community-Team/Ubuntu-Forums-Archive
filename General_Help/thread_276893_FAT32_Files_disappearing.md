---
title: "FAT32: Files disappearing?"
date: 2006-10-13
forum: General Help
---

### Post by ikkejw on 2006-10-13
I have a few FAT32 partitions, the most important ones being 200 and 20 GB in size. Now, I have been using Kubuntu exlusively for the past few weeks, and I must say I really love it. But when I booted to Windows this morning, most (if not all) files I changed/added on the FAT32 disk in Kubuntu had disappeared! Then I went back to Kubuntu, only to find out they were really gone. The 20GB disk is not affected, only the 200GB one.

Anyone knows why this happened? Is there some limit on FAT32 partition size in Linux (in Windows it's 200GB)?

---

### Post by kidders on 2006-10-13
Hi there,

Afaik, the maximum size of a FAT32 partition (limited by the structure of the filesystem itself) is around 8TB, so that shouldn't be a problem.

If changes you made weren't persisted, the usual explanation is that they never actually made it onto the disk in the first place. My first suspicion is that you may not have dismounted the filesystem correctly, or that you didn't in fact save your changes where you thought you were saving them. Is either of these possible?

Hope that helps.

**Edit:** I should probably add that Microsoft actively discourages the use of FAT32 partitions larger than 32GB ... just in case.

---

### Post by ikkejw on 2006-10-14
I'm pretty sure the files got saved onto the disk... In Kubuntu, even after a reboot, the files persisted. After one reboot into Windows, they were gone!

I have been using these disks for a few years in Windows, and I never lost any files.

And about the 32GB limit, that's probably because MS wants us to use NTFS instead.

---

### Post by tturrisi on 2006-10-14
post your /etc/fstab.

---

### Post by ikkejw on 2006-10-14
```
# <file system> <mount point>   <type>  <options>                           <dump>  <pass>
proc            /proc           proc    defaults                            0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro          0       1
/dev/hda1       /media/win_c    ntfs    defaults,nls=utf8,umask=007,gid=46  0       1
/dev/hda5       /media/win_d    ntfs    defaults,nls=utf8,umask=007,gid=46  0       1
/dev/hdb5       /media/win_o    vfat    defaults,utf8,umask=007,gid=46      0       1
/dev/hdb6       /media/win_p    vfat    defaults,utf8,umask=007,gid=46      0       1
/dev/hda6       /media/win_s    vfat    defaults,utf8,umask=007,gid=46      0       1
/dev/hdb7       none            swap    sw                                  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto                     0       0
```

---

### Post by kidders on 2006-10-16
> **ikkejw said:**
> I'm pretty sure the files got saved onto the disk... In Kubuntu, even after a reboot, the files persisted. After one reboot into Windows, they were gone!Looks like some sort of silly limitation with Windoze in that case :-( How irritating ](*,)

---

### Post by deeptingler on 2006-10-16
I must say that thats a new one on me - I was using an external 320gb hard drive formatted with fat32 (yes the whole lot as one partition) as a temporary measure when I first came over to linux so I could still duel boot to windows when needed.  I am using Kubuntu myself too and never had any probs at all?  All my files are still there.

Now, though, my drive is formatted to ext3 and I use a 1gb partition on the external drive with the drivers on it for windows to see the ext3 partition.  It means I am using a superior file system but I am still able to take the drive to my windows using mates (until they see the light)..  hopefully, this has just been a one off thing that has happened to you!:(

---

### Post by kidders on 2006-10-16
Yeah :mad: it's so weird! Please let us know if this happens to you again.

---

### Post by div on 2006-10-16
I have exactly the same problem. If I save the files on a FAT32 partition (20GB in size) the next time I get into Windows, the files are lost (they are marked as lost clusters).

---

### Post by kidders on 2006-10-16
You know, I wonder if this has to do with character encoding. I wonder if ikkejw and div could check whether Linux and Windoze are on the same page.

What language does each of your copies of Windows speak?

---

### Post by div on 2006-10-16
English for both Linux and Windows. I've seen multiple threads here on ubuntuforums speaking of the same problem, but no fix yet. The thing is that if I unmount the FAT32 partition, restart, go to linux again, mount the partition, everything is fine (the files are saved). As soon as I get into Windows, the files are missing (they are marked as lost clusters as I've said above). Without trying to fix them in windows, if I go back to linux, I can't see them anymore.
I've managed at some point to save the files from linux and they were visible on Windows, but I can't remember what I did any different than nowadays.

---

### Post by tturrisi on 2006-10-16
> **ikkejw said:**
> ```
# <file system> <mount point>   <type>  <options>                           <dump>  <pass>
proc            /proc           proc    defaults                            0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro          0       1
/dev/hda1       /media/win_c    ntfs    defaults,nls=utf8,umask=007,gid=46  0       1
/dev/hda5       /media/win_d    ntfs    defaults,nls=utf8,umask=007,gid=46  0       1
/dev/hdb5       /media/win_o    vfat    defaults,utf8,umask=007,gid=46      0       1
/dev/hdb6       /media/win_p    vfat    defaults,utf8,umask=007,gid=46      0       1
/dev/hda6       /media/win_s    vfat    defaults,utf8,umask=007,gid=46      0       1
/dev/hdb7       none            swap    sw                                  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto                     0       0
```

vfat should look like this (for read-write): 
(I use /mnt instead of /media)

```
/dev/hda5    /mnt/FILES	vfat 	iocharset=utf8,umask=000	0
```

See these sections:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

