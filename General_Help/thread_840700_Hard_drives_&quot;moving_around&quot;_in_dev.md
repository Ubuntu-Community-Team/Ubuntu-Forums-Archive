---
title: "Hard drives &quot;moving around&quot; in /dev"
date: 2008-06-25
forum: General Help
---

### Post by bbbaldie on 2008-06-25
Bizarre issue.

Upgraded from Gutsy to hardy two months ago. Now, every time I get a kernel upgrade, my hard drives "move around" in /dev!

Here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=5a28df74-acee-43d2-a311-1c8b6b5f7d7a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=91fff306-f181-4cd1-b540-e432bb2e74be none            swap    sw              0       0
/dev/cdrom1        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1 	/media/250g/	ext3 	defaults,errors=remount-ro	0	0
usbfs 	/proc/bus/usb 	usbfs 	auto 	0 0
/dev/sda2	/home	ext3	nodev,nosuid	0 2
```

After a kernel update, typically the boot will halt at a root CLI. I have to do a ls /dev to see the hard drives' location. Then, I have to edit fstab to make them show up. 

sda1 and sda2 typically become hda1 and hda2. With the most recent kernel update (released a week or two ago), hda and hdb trade places, so I can't boot at all. I'm not geeky enough to edit the entries for hdb put in when the filesystem was originally written.

Any ideas, friends?

---

### Post by bodhi.zazen on 2008-06-25
Mount them by UUID rather then /dev (like your other partitions)

To list your partitions by uuid 

```
sudo blkid
```

---

### Post by bbbaldie on 2008-06-25
I'll gve it a try, bodhi.zazen. Thanks.

---

