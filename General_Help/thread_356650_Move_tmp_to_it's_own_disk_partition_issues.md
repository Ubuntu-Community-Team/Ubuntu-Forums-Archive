---
title: "Move /tmp to it's own disk partition issues"
date: 2007-02-08
forum: General Help
---

### Post by landrand on 2007-02-08
I thought I'd give Ubuntu Edgy a try.  I primarily use Gentoo and Archlinux.  I'm trying to move the /tmp directory to it's own partition.  Something that is very easy to do in Gentoo or archlinux, I'm finding it difficult with Ubuntu.  Any idea's what I'm doing wrong.  

Existing configuration.
/dev/hda3    /
/dev/hda2  /boot
/dev/hdc1   swap

For performance reasons, I'd like to move the /tmp directory to it's own partition (hdc2) on the second harddrive.

Here's what I tried to do:
fdisk /dev/hdc   and create a 1 G partition (hdc2).
mkreiserfs /dev/hdc2

vol_id -u  /dev/hdc2  to find out the volume label for hdc2
daf568ca-c622-493b-bfec-726376081b0f

Change /etc/fstab with the following info.

#/dev/hdc2
UUID=daf568ca-c622-493b-bfec-726376081b0f   /tmp  reiserfs  noatime,notail   0 0

reboot the system.

No matter what I've done, this won't work.  The system doesn't like it and give me an error when I start up.  Any idea's what I'm doing wrong???

---

### Post by po0f on 2007-02-09
landrand,

First, the error it is spitting at you would be nice.  Second, have you tried just specifying just the device name instead of its UUID?  And thirdly, why are you using reiserfs as a /tmp filesystem?  ext2 would probably be a better choice.

I also fail to see how having /tmp on a separate partition increases *performance*.  I do it myself, but to increase *security*.

---

### Post by chrisccoulson on 2007-02-09
> **po0f said:**
> I also fail to see how having /tmp on a separate partition increases *performance*.  I do it myself, but to increase *security*.

Doesn't having /tmp on its own partition reduce fragmentation of the root fs?

---

