---
title: "Problem mounting ext3 hard drive"
date: 2006-07-25
forum: General Help
---

### Post by chipsdeluxe on 2006-07-25
I recently reformatted a hard drive in my system as ext3 (previously NTFS) and installed ext2ifs in Windows so I can use that drive as storage in both Windows and Ubuntu. I copied a bunch of data onto the partition while in Windows, and now I'd like to access that data in Ubuntu. The problem I have is that when I try to open the drive in Ubuntu File Browser, I get an error message that reads:

```
Unable to mount selected volume
mount: only root can mount /dev/sdb1 on /media/sdb1
```

I think the problem is that my /etc/fstab is incorrectly configured. Can someone point me in the right direction so I can access the drive?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by taurus on 2006-07-25
Open a terminal (Applications -> Accessories -> Terminal) and do

```

sudo umount /media/sdb1 <-- to unmount the drive first
(enter your own password, the one that you use to log in...)
sudo gedit /etc/fstab <-- to modify your /etc/fstab for new change

```
Make a change for /dev/sdb1 so now it would looke something like this!

```

/dev/sdb1   /media/sdb1   ext3   defaults   0   1

```
Save the change and from the prompt, type

```

sudo mount -a <-- to mount /dev/sdb1
df -h <-- you now should see /dev/sdb1 in /media/sdb1!!!

```

---

### Post by chipsdeluxe on 2006-07-25
Thanks for the help. I followed your instructions and it seemed to mount the drive properly, but I ran into a couple of problems. First I'll post my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1      /media/sdb1   ext3   defaults   0   1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Problem 1. Now I see my Windows NTFS partition in nautilus, and I cannot browse it. It is the first partition on the first hard drive: sda1. I don't think it appears in the fstab file, so I'm not sure why it's showing up in nautilus. I don't need access to this partition in Ubuntu, so I'd like to not even see it when I boot to Ubuntu.

Problem 2. When I boot to Ubuntu, I get the following errors regarding the drive I was having trouble mounting in the earlier post (sdb1). It is labled DATA:
```
DATA contains a file system with errors, check forced.
DATA: Inode 47874071 has illegal blocks.
```
The computer procedes to run a fsck (I think) which takes a couple of minutes. When it finishes I get the following messages:
```
DATA: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY, I.E. WITHOUT -a OR -p OPTIONS
File system check failed. Please repair manually.
Control-D will exit from this shell and continue startup.
```

When I press Control-D, the computer finishes starting up, and I can log in normally, and browse the drive labled DATA (sdb1).

Is it possible to repair the drive without losing any data?

---

