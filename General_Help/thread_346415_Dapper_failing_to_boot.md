---
title: "Dapper failing to boot"
date: 2007-01-25
forum: General Help
---

### Post by bcp01cui on 2007-01-25
I'm having trouble getting Dapper to boot.  It was working fine until I tried to boot today and all of a sudden I get a black screen of death with the following:

mount: Mounting /dev/hdc3 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /rootproc failed: No such file or directory
Target filesystem doesn't have /sbin/init
...
/bin/sh: can't access tty; job control turned off


I've tried running the rescue mode from the Live CD as suggested in the help menu on the CD but get "Could not find kernel image: rescue".  Is there any way to get Ubuntu to actually work short of reinstalling it and hoping this doesn't happen again?

---

### Post by dcstar on 2007-01-25
> **bcp01cui said:**
> I'm having trouble getting Dapper to boot.  It was working fine until I tried to boot today and all of a sudden I get a black screen of death with the following:

mount: Mounting /dev/hdc3 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /rootproc failed: No such file or directory
Target filesystem doesn't have /sbin/init
...
/bin/sh: can't access tty; job control turned off


I've tried running the rescue mode from the Live CD as suggested in the help menu on the CD but get "Could not find kernel image: rescue".  Is there any way to get Ubuntu to actually work short of reinstalling it and hoping this doesn't happen again?

Use the Live CD to run **fsck** on your hard drive (a forum search should provide detailed instructions).

---

