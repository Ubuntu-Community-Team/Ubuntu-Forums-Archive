---
title: "Cloned drive and permissions issues"
date: 2014-03-23
forum: General Help
---

### Post by Brandon_MacEachern on 2014-03-23
I recently cloned my drive via dd (because I'm going to a bigger drive in my laptop)  and once it was done i expanded the drive in gparted. 

Took old drive out and installed new one into the laptop. Booted up just fine, but it had a problem.  I got a permission error that a reboot resolved it seemed. But other things remained. 

For example, when launching Google Chrome from the unity launcher, it opens up another icon.  Second part of this is that chrome loads without my settings, cookies, etc. 

Almost like there is still a permissions issue somewhere.  Being that it was a direct copy basically i don't know how permissions got messed up.

---

### Post by TheFu on 2014-03-23
I think it is something else.
Please run **sudo parted -l** and **sudo blkid** and post the /etc/fstab.

Cloning a HDD via dd, ddrescue, gparted, fsarchive, ... works.

---

### Post by Brandon_MacEachern on 2014-03-23
```
 brandon@brandon-MacBookPro:~$ sudo parted -l
[sudo] password for brandon: 
Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End    Size    File system     Name                  Flags
 1      20.5kB  210MB  210MB   fat32           EFI System Partition  boot
 2      210MB   136GB  136GB   hfs+            Macintosh HD
 3      136GB   136GB  650MB   hfs+            Recovery HD
 4      136GB   136GB  1049kB                                        bios_grub
 5      136GB   746GB  609GB   ext4
 6      746GB   750GB  4200MB  linux-swap(v1)




brandon@brandon-MacBookPro:~$ sudo blkid
/dev/sda1: LABEL="EFI" UUID="70D6-1701" TYPE="vfat" 
/dev/sda2: UUID="2a97f693-433b-3075-b3ad-b871c6d4a279" LABEL="Macintosh HD" TYPE="hfsplus" 
/dev/sda3: UUID="42320ca6-833a-3699-aac3-64080dd45ff8" LABEL="Recovery HD" TYPE="hfsplus" 
/dev/sda5: UUID="38cf8bed-e1d6-4b8e-9e41-f3a7e158f78c" TYPE="ext4" 
/dev/sda6: UUID="1b988e3f-4fbc-4f6a-b0b4-2adea9fd7bc6" TYPE="swap" 
brandon@brandon-MacBookPro:~$
```

---

### Post by TheFu on 2014-03-23
Please edit the last post and add "code" tags.  Makes this stuff much, much easier to read.
Also -** /etc/fstab** - code tag that too please.

---

### Post by Brandon_MacEachern on 2014-03-23
Done

---

### Post by Brandon_MacEachern on 2014-03-23
```
[COLOR=#000000]# /etc/fstab: static file system information.[/COLOR]#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=38cf8bed-e1d6-4b8e-9e41-f3a7e158f78c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1b988e3f-4fbc-4f6a-b0b4-2adea9fd7bc6 none            swap    sw              0       0
```

---

### Post by Brandon_MacEachern on 2014-03-23
I ran the clone again but this time from a USB boot disk, now it works fine, not a single issue.

Lesson learned, done clone an HD from a live boot partition.  On OS X this works fine, but not so much for linux.

---

### Post by TheFu on 2014-03-23
You can clone a HDD in linux
either by booting from another install (gparted ISO is good for this)
OR
dropping into single-user mode for the last copy of the clone.

I run rsync to clone files between running systems all the time, but for that last sync (about 20-50 seconds), I drop to single-user-mode to avoid file corruption.  The kind of programs running matter. The more programs that use databases and have them open, but not sync'd to disk, the more likely corruption is.

BTW, I think you have just been lucky on OSX.  But the lack of Gnome and those ever-more-complicated settings files might be it.

The issue I though would be seen in the blkid/fstab/parted output isn't there. Sorry - it was an idea that wasn't going to help. Just thought you should know.

---

### Post by monkeybrain20122 on 2014-03-23
> **Brandon_MacEachern said:**
> I ran the clone again but this time from a USB boot disk, now it works fine, not a single issue.

Lesson learned, done clone an HD from a live boot partition.  On OS X this works fine, but not so much for linux.

fsarchiver supports live cloning.I do it all the time.[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)
Just don't install or remove stuffs when you are running it to clone the same partition you are on to avoid inconsistencies.

---

