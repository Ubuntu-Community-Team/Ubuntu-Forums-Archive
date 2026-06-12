---
title: "External HD's and Ubuntu?"
date: 2007-04-12
forum: General Help
---

### Post by bg1256 on 2007-04-12
I'm in the market for an external HD, namely this one:

[link]("http://www.compusa.com/products/product_info.asp?product_code=340471&pfp=apr8#ts")

Will this work with Linux?

Thanks!

---

### Post by NICU on 2007-04-12
I can't say with 100% certainty, but most external hard drives will show up similar to a huge USB thumb drive.  It says it will work with the Mac OSX which makes me almost positive it will work in Linux.  Your only problem may be the file system, if for some strange reason its NTFS instead of FAT32 which most are.  I have a Western Digital MyBook which works great on all of my PCs running XP and Ubuntu.

---

### Post by thebigandroid on 2007-04-15
I have a Western Digital MyBook which doesn't work so great on my PC that dual-boots XP and Ubuntu. Specifically, ubuntu dapper 6.01 doesn't mount it unless I unplug it & replug it  while Ubuntu's running. I can't mount it as non-root, and when I mount it with sudo, I have no permissions on it; just to do ls, I would have to do sudo ls? That's not right, there must be a way to fix that. Also, it's formatted NTFS (I did that because of the FAT32 4G file size limit). Will that mean I can't write to it from Ubuntu?

What I really seek is a convenient way to be able to download &/or create a file in Ubuntu, and then access it when I boot into XP. Any suggestions?

---

### Post by NICU on 2007-04-15
I use a MyBook 320GB hard drive which works great with my dual boot system.  In Ubuntu Edgy 6.10 and Feisty 7.04, I haven't had any problems.  It mounts similar to a USB flash drive.  I haven't had a problem using FAT32 on a very large hard drive. 

To fix your read/write permissions on your MyBook you may want to add that to your /etc/fstab file.  The problem with doing that is (at least my USB drive) doesn't always show up as the same drive every time.  The first USB drive plugged in receives /dev/sda1 and the second receives /dev/sda2 and so on.  You can also install NTFS drivers to read/write if you don't want to reformat your large drive.

---

### Post by dfm21 on 2007-04-15
Format you drive with FAT!

If want to see an internal ext3-formatted drive in windows, you can get the Ext2 IFS from [http://www.fs-driver.org/](http://www.fs-driver.org/).

The mount thing (example):
```

sudo mkdir /media/external
sudo chown me /media/external
sudo mount -t vfat /dev/hdb1 /media/external

```
With these steps you
[LIST=1]
[*]create a mountpoint
[*]change owner of mountpoint to self
[*]mount a FAT partition from /dev/hdb1 to mountpoint
[/LIST]

---

### Post by bg1256 on 2007-04-16
[www.ntfs3g.org](www.ntfs3g.org)

---

