---
title: "ext3 corrupted filesystem (Raid5)"
date: 2008-04-11
forum: General Help
---

### Post by soapee01 on 2008-04-11
Hi,

I managed to corrupt my raid5 array and the ext3 partition that sits atop it with massive power cycling in my neighborhood due to the tornadoes here in north Texas, and in spite of my use of a UPS.

I'll concede, already that I'm dumb and lazy, since I didn't bother to back anything up in spite of numerous articles I've read that explicitely state that RAID is not a backup.

I did manage to get the Raid array (root partition) to sync.  After that, I tried to mount the ext3 filesystem, to no avail, so I ran fsck.  After many, many errors, I let it do it's thing and was able to mount the filesystem.  It appears that I've been very lucky, and I haven't lost any data that I really care about.

I'm now backing everything up to a Western Digital NAS (My Book World Edition), via knoppix and smb (tar).

I'm unable to boot Kubuntu due to many missing OS files, libraries and init scripts (many of which are in lost+found).  It just stalls at Busybox in initramfs.

What I'd REALLY like to be able to do is to chroot into this directory and somehow repair the OS install.   It was fairly customized and I'd rather not have to go through the weeks of tweaking ubuntu again to get it just right (I know... that's why I should have backed it up in the first place).

Is there any way this can be accomplished?  Somehow, I'm thinking that apt/dpkg probably can't handle something this screwy, but I'm guessing that it might.

Also, I've tried the Ubuntu Feisty install CD in rescue mode, but it doesn't appear that it can handle Software Raid, and it acts like it wants to wipe my drives.

Thanks for considering.

Sincerley,

James

---

### Post by dcstar on 2008-04-12
> **soapee01 said:**
> Hi,

I managed to corrupt my raid5 array and the ext3 partition that sits atop it with massive power cycling in my neighborhood due to the tornadoes here in north Texas, and in spite of my use of a UPS.
............
Also, I've tried the Ubuntu Feisty install CD in rescue mode, but it doesn't appear that it can handle Software Raid, and it acts like it wants to wipe my drives.

Thanks for considering.

Sincerley,

James

I would suggest doing an install of your current O/S on a USB drive, and then mounting your array with that and manually copying the missing files from the USB to it.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

