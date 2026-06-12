---
title: "DVD Packet Writing Read-only error"
date: 2008-06-05
forum: General Help
---

### Post by ordealbyfire83 on 2008-06-05
Hello,
I am having trouble getting packet writing working in Feisty. I'm trying to write to DVD+RW disks. I have formatted the disk using

```
dvd+rw-format -force /dev/scd0
```
```
mkudffs --media-type=dvd --udfrev=0x0150 /dev/pktcdvd/0
```

Then I mount the disk manually using something like
```
mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/cdrom0
```

Then I try to change the permissions of /media/cdrom0 and it tells me the disk has a read-only file system (this still happens if I use -o rw,utf8,noatime). Alternatively, Ubuntu will automount the disk and an icon LinuxUDF appears on the desktop. Still the disk is read only.

I have tried to write to the disk on another computer running Fedora, and the same thing happens. Is it because the disk isn't formatted properly? Or a permissions error?

I have seen other (older) tutorials that use cdrwtool instead of dvd+rw-format/mkudffs instead but this doesn't work.

Any ideas? Thanks

---

### Post by ordealbyfire83 on 2008-06-06
Solved.

When invoking mkudffs, use --media-type=dvdrw instead of ...=dvd.

---

