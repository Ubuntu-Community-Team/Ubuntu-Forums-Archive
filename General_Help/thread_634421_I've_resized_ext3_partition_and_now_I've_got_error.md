---
title: "I've resized ext3 partition and now I've got errors..."
date: 2007-12-07
forum: General Help
---

### Post by darck on 2007-12-07
I've got exact problem like person here:
[http://www.linuxquestions.org/questions/linux-hardware-18/corrupt-ext3-partition-need-to-recover-376366/]("http://www.linuxquestions.org/questions/linux-hardware-18/corrupt-ext3-partition-need-to-recover-376366/")

I resized partitions ext3 partition with Ubuntu by Pargon Partition Manager. It has done job right with windows NTFS, but wrong with ext3

I can access files on this partition, but while booting Ubuntu it says partition has got errors and advices me to run fcsk. After running fcsk it makes something like that:

```
Error allocating 1022 contiguous block(s) in block group 1 for inode table: Could not allocate block in ext2 filesystem
Error allocating 1022 contiguous block(s) in block group 25 for inode table: Could not allocate block in ext2 filesystem
Error allocating 1022 contiguous block(s) in block group 49 for inode table: Could not allocate block in ext2 filesystem
Restarting e2fsck from the beginning...
/ contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
```

and the whole process repeats itself


How can I repair that?

---

### Post by p_quarles on 2007-12-07
I'm not familiar with this Pargon application, but I would recommend using Gparted instead. It looks like Pargon attempted to expand the ext3 partition as an ext2 partition. This filesystems are compatible with each other, so it probably didn't completely destroy the partition, but that will definitely cause some problems with fsck. 

Anyway, I hope you backed everything up before doing this. If you haven't do what you can in that department before proceeding. Then, get the Gparted live CD  and use that to fix the partition. You may need to format it entirely. 

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by darck on 2007-12-07
I've just tried to resize partition in Gparted, but it "hungs" on checking disk. If I remember correctly it run e2fsck. When I run e2fcsk in console it makes this checks in infinite loop...

Anyway how to repair it, or maybe if i can read disk data how to backup them in order to restore after disk format and Ubuntu reinstallation? (I'm not sure weather i can read all, but it seems so)

---

### Post by p_quarles on 2007-12-07
> **darck said:**
> I've just tried to resize partition in Gparted, but it "hungs" on checking disk. If I remember correctly it run e2fsck. When I run e2fcsk in console it makes this checks in infinite loop...

Anyway how to repair it, or maybe if i can read disk data how to backup them in order to restore after disk format and Ubuntu reinstallation? (I'm not sure weather i can read all, but it seems so)
Yep. Sounds like the partition is hosed. 

To back up, you'll need to copy your files to another medium. An external hard drive if possible; otherwise you'll need to burn it onto CDs/DVDs or copy to a flash drive.

Your number one priority is to backup any data in your home folder. This is where all your settings and personal files are, i.e., the stuff you don't want to lose. Once you've done that, you'll need to format the partition and reinstall Ubuntu.

---

### Post by darck on 2007-12-08
I created backup like is written here : [http://www.arsgeek.com/?p=637](http://www.arsgeek.com/?p=637)

```

    sudo tar cvpzf arsgeek.backup.tgz –exclude=”/proc/*” \

    –exclude=”/lost+found/*” –exclude=”/dev/*” \

    –exclude=”/mnt/*” –exclude=”/media/*” –exclude=”/sys/*” \
    –exclude=”/tmp/*” –exclude “/var/cache/apt/*” /

```

formated partition, installed ubuntu once again
and restored backup by:  sudo tar xvpfz backup.tgz -C /

And now have problem, because when i choose normal Ubuntu boting in Grub it hungs on loading
And when i choose in Grub failsave start it hungs somewhere during detecting hdds - it says something about DMA, then hungs for few minutes and leaves me with wired bash:
(initramfs)

---

### Post by p_quarles on 2007-12-08
So, I take it that Windows boots up okay? 

DMA is the protocol used for reading and writing an IDE hard disk, so it looks like there's still a problem with the filesystem. My advice would be to boot up the Gparted live cd again and run fsck.

---

### Post by darck on 2007-12-09
Yes windows boots correctly.

No it's not problem with disk, because after error I formatted partition, installed Ubuntu - it was working. Then I extracted backed up files of old Ubuntu (which i archived when fsck was showing many errors on partition) and Ubuntu stopped working.

Conclusion is that files i extracted are corrupted or method i used to back up system and recreate is bad.

Question is, which of backed up files i can extract to working Ubuntu system to be pretty sure I won't destroy crucial for booting files. In other words:** having working fresh Ubuntu and my backup - how to restore old settings?**

---

### Post by p_quarles on 2007-12-09
Problems with the disk and problems with the filesystem are not the same thing. My advice is still to run fsck on the Ubuntu partition, which may help diagnose the problem that was caused by restoring your backup files.

---

### Post by darck on 2007-12-09
> **p_quarles said:**
> Problems with the disk and problems with the filesystem are not the same thing. My advice is still to run fsck on the Ubuntu partition, which may help diagnose the problem that was caused by restoring your backup files.

i'll do that, but as far as i know **tar** can't destroy fileststem. Because seriously - how ? :)

---

### Post by p_quarles on 2007-12-09
No, tar can't destroy the filesystem. What I'm thinking is that the files you tarballed were themselves part of a corrupted filesystem, and that by untarring them this corruption was introduced to the newly formatted partition.

---

### Post by darck on 2007-12-12
problem solved:

It wasn't file system error ( fsck hasn't returned any error ) but /boot/grub/menu.lst  error. Restored backup replaced this file with previous version. Between previous and actual there was difference in UUID=cccacfba-5179-42de-a063-7cd46e784c0c

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cccacfba-5179-42de-a063-7cd46e784c0c ro quiet splash locale=pl_PL
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

after another reinstallation of ubuntu and restoring all backup expect of /boot directory Ubuntu works like before !!! :)

---

