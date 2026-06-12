---
title: "Cannot unmount partition on USB drive"
date: 2016-03-26
forum: General Help
---

### Post by rdh61 on 2016-03-26
Hi,

I have purchased a Sandisk USB drive, which I want to partition. However, to do this I have to unmount the file system. But I cannot unmount it either with GParted or the "Disks" utility. If I umount with a terminal, no errors are shown, but the drive still appears mounted in both the Disks utility and GParted.

How can I resolve this?

Many thanks.

---

### Post by TheFu on 2016-03-26
Update:  I just bought a 64G SDXC micro card.  Linux wouldn't recognize it.  Windows7 wouldn't see more than 32G of the storage.  Put it into a chromebook, formatted it to 64G - FAT32 (needed for a specific device here with only NTFS/FAT32 support). xFat doesn't work.  Microsoft added a 32G limit to FAT32 formats years and years ago - not because there was any requirement, but mainly so they could patent xfat and earn royalties off all the video camera makers who use it. Then they pushed "critical patches" out to all versions of Windows to prevent FAT32 over 32G formatting. It still works fine, just cannot be formatted that way on Windows.  I won't use xfat, ever.  Sorta like BluRay - which I will never use.  My little protest, useless, but ... I feel better doing it.  BTW, SanDisk flash storage isn't the most compatible like it was in the old days.  There are lots of USB controllers that don't like SanDisk Ultra - Raspberry Pi's have issues with it. There are others. Google "sandisk issues" to see more - there's even an WSJ article from last year.

Original:
The sort answer - try right-clicking on the mount in the files app, there should be an **eject** or **unmount** option.

There is also the** fusermount -u** tool.

The rest of this post is full of facts AND my opinions about mounting.

There are different sorts of "mounting" in Linux now.  
a) There are _real_ mounts, which happen by manually editing the /etc/fstab file. That would be too much hassle for a portable device like temporary USB storage.  
b) There are autofs mount, which are _real_ in that the entire OS sees these. It is a little more involved to setup using the automounter tools.
c) There are manual mounts - sudo mount ....  I mount flash storage using unique labels on those devices. 
```
$ more ~/bin/mnt-usb-320.sh 
#!/bin/bash
UID=1000
GID=1000
LABEL1=PortMedia
LABEL2=Videos
LABEL3=32G
LABEL4=16G
LABEL5=64G

sudo mkdir -p /mnt/$LABEL1 /mnt/$LABEL2 /mnt/$LABEL3 /mnt/$LABEL4 /mnt/$LABEL5
sudo mount -o uid=$UID,gid=$GID LABEL=$LABEL1 /mnt/$LABEL1
sudo mount -o uid=$UID,gid=$GID LABEL=$LABEL2 /mnt/$LABEL2
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL3 /mnt/$LABEL3
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL4 /mnt/$LABEL4
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL5 /mnt/$LABEL5
```
Is how I do it for lots of different USB devices (I'm lazy, so have all the devices in 1 script).  To umount, just use **sudo umount** in the normal way.  This will let every userid on the box see the storage, which is important to me.
d) Then there is the gfvs way. gfvs mounts aren't real mounts in that the entire OS doesn't see them, the /etc/mtab doesn't get updated and only the userid running the GUI tool with the libgvfs addon knows about the mount(s).  It sorta sucks, because in the last 4 yrs, they've moved the mounted location 3 times.  gvfs can be really slow too - like 3x slower than a _real_ mount.  But they are convenient, so people put up with the bad performance and other less-than-Unixy parts.

Your choice on how you elect to mount things. Completely up to you.

I should say that since I don't use GUI file managers (too slow, too limiting), gvfs really isn't a viable option for me.  Plus every year when they come up with a new reason to move the default gvfs mount locations due to security issues, I would need to change all my scripts, but only on the systems running the new code, not the 15 systems running older versions. I don't like to be confused over something which has been working for 30+ yrs.

I don't understand why they bother with gfvs for locally attached storage at all. I completely understand having a GUI to connect mounts, but a whole new subsystem? Really?  NIH issues, much?
</opinion>
[https://wiki.gnome.org/Projects/gvfs/doc](https://wiki.gnome.org/Projects/gvfs/doc) is the documentation for it, which I haven't read.

---

### Post by rdh61 on 2016-03-26
Thanks for the short answer and the long one, and sorry to have bothered people with this. Problem solved with reboot. Maybe one day I'll learn.

---

### Post by TheFu on 2016-03-26
reboot is NOT a solution. It is a bad workaround, IMHO.  Unix systems should not need to be rebooted except for a kernel update and even that will be ending soon - the 4.x kernel has while-running kernel updates. [https://www.linuxjournal.com/content/no-reboot-kernel-patching-and-why-you-should-care](https://www.linuxjournal.com/content/no-reboot-kernel-patching-and-why-you-should-care) .   Ksplice has been doing this for selected kernels for over a decade.

Rebooting should never be a viable solution, IMHO.  But I'm crazy that way.  Heck, I don't even like to logout/login to reset session environment variables.  Been running for 5 days where I have to start thunderbird from a special terminal just to avoid logout. ;)

Of course, you aren't me and my obsessions don't apply to many people. ;)

---

