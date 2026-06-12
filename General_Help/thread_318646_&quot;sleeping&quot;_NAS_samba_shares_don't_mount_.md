---
title: "&quot;sleeping&quot; NAS samba shares don't mount properly"
date: 2006-12-14
forum: General Help
---

### Post by barney_1 on 2006-12-14
Hi all,

I have a problem with mounting my NAS samba shares.  The first time I boot in the morning it takes a very long time for my gnome-panel to become active and the two NAS drives I have bookmarked in "places" through smb shares to not mount.

If I try to mount them manually at this point I get:
```
could not find mount point /Milhouse
```

To get them to work, I have to unmount the two directories (which takes a mysteriously long time, ~25 seconds each), then run "sudo mount -a" and everything mounts properly immediately.

My theory:  I have my NAS server (freeNAS) set up to go to sleep when not in use.  When I boot my computer first thing in the morning those drives are asleep and when fstab tries to mount them the file system isn't available in time for Edgy to mount them properly.

Does anyone have an idea of what I can do to fix this?  I'll include my fstab below.  The two that don't mount properly are /Milhouse and /Skinner:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6 -- converted during upgrade to edgy
UUID=76b79d37-e36c-4ec6-908f-4cca4beca257 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda7 -- converted during upgrade to edgy
UUID=a35ab384-9b49-4736-9882-4eac9790103a none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=F2C085EDC085B7FD /mnt/Cdrive ntfs umask=0222 0 0
# /dev/sda2 -- converted during upgrade to edgy
UUID=F4C4882FC487F262 /mnt/Ddrive ntfs umask=0222 0 0
# /dev/sda3 -- converted during upgrade to edgy
UUID=07ac799d-9626-45af-9b4d-aafafe25ce5f /Flanders ext3 defaults 0 0
/dev/sda5 /Lenny xfs defaults 0 0
//192.168.1.100/NAS1		/Milhouse smbfs	credentials=/root/.smbcredentials,dmask=777,fmask=777	0	0
//192.168.1.100/NAS2		/Skinner smbfs	credentials=/root/.smbcredentials,dmask=777,fmask=777	0	0
```

---

### Post by bernied on 2006-12-14
hmmmm, I didn't realise it until now, but I have the same problem. I have a couple of NSLU2 devices and they don't always mount at startup. I don't have to do everything you did, just a 
```
sudo mount -a
```does it for me. Sorry, can't show you my fstab just now.

---

### Post by bernied on 2006-12-14
a workaround might be to mount these problem devices in a script, instead of through fstab. You'd need a way of waking them up first though.
But this is messy.

There doesn't seem to be anything on this in the mount or fstab man pages.

---

