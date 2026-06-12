---
title: "CD Automounting Stopped working :("
date: 2007-02-11
forum: General Help
---

### Post by BIGtrouble77 on 2007-02-11
I haven't testing other devices (like my flash drives) but my CDs/DVDs won't auto-mount.  I can do it manually.  I assume it's an issue with dbus and possibly the kernel.

I just ran one of the new kernel updates which brought me to 2.6.15-28-amd64-generic.  Problem occured after I did the update... the system defaulted to a Fiesty Kernel I had previously installed.  I changed grub back to the (updated) standard Dapper kernel, reinstalled my video drivers and auto-mounting ceased to work.

Any ideas?
TIA,
-bt

---

### Post by BIGtrouble77 on 2007-02-12
bump

---

### Post by seppo on 2007-02-12
could you post the contents of your /etc/fstab file?

---

### Post by BIGtrouble77 on 2007-02-12
The meda drive (hda1) mounts just fine.  cdrom0, not so fine.  I haven't changed myfstab since I installed Dapper.  I think the problem has something to do with dbus/hal.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro,noatime,data=writeback 0 1 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/media              ext3    defaults,errors=remount-ro 0       1
```

---

### Post by seppo on 2007-02-12
fstab looks ok. Indeed it is most likely the problem can be pinned down to your new kernel.

---

### Post by BIGtrouble77 on 2007-02-12
> **seppo said:**
> fstab looks ok. Indeed it is most likely the problem can be pinned down to your new kernel.

I agree.  I appreciate looking into it.  I'll reboot with 2.6.15-27 and report my findings.  I just have to wait for a few things to finish first.

---

### Post by BIGtrouble77 on 2007-02-12
I can confirm that it is a kernel issue.  I fired up 2.6.15-27 and my auto-mounting seems to be working fine once again.  I curious if others running the Dapper 2.6.15-28 kernel are having the same problem as me.  I'm using the amd64 build so it would be interesting to know if it's limited to that build.

---

### Post by seppo on 2007-02-13
any weird things in dmesg, /var/log/messages, lshal?

---

