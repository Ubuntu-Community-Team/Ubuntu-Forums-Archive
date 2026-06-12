---
title: "mount error at boot"
date: 2018-03-18
forum: General Help
---

### Post by dryan775 on 2018-03-18
HELP please!

I was running along just fine.  Tried to start Steam to log into a network game I am playing when system became totally unresponsive.

Had to power it off.
When I turned it back on it wouldn't boot to grub, got some kind of I/O error from the /dev

Booted into a Live session from USB stick. 
When I try to mount my 991GB volume I get this:

Error mounting /dev/sda2 at /media/ubuntu-gnome/786f0791-581c-40ff-9233-9d85f6503c49: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda2" "/media/ubuntu-gnome/786f0791-581c-40ff-9233-9d85f6503c49"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

ANY help would be appreciated.  

Even if I can't fix it (I'm fine with replacing the drive) there are a few files that I was working on whose current versions have not been backed up.  I'd hate to lose the past week or so worth of work.

Thanks in advance for any help

DwR

---

### Post by wildmanne39 on 2018-03-18
*Thread moved to **General Help, a more appropriate forum**.*

---

### Post by SeijiSensei on 2018-03-19
Things don't look good.  Have you tried running
```
sudo fsck -t ext4 /dev/sda2
```

Otherwise you might need something like [photorec]("https://www.cgsecurity.org/wiki/PhotoRec") to try and restore your files.

---

### Post by dryan775 on 2018-03-19
That fsck code worked!  I was able to mount the drive and copy the files I wanted to save off to a USB.

                  ******       THANK YOU SO much!      *******

I don't think I'll trust this drive again - i'll be ordering a replacement tomorrow!

DwR

---

