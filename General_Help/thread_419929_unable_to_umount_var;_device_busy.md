---
title: "unable to umount /var; device busy"
date: 2007-04-23
forum: General Help
---

### Post by goslar on 2007-04-23
Ladies and gentlemen,
I would like to upgrade to from 6.10 to 7.04, but my /var filesystem is too small for the operation.
Thus, I thought of booting into single user mode, lvextend the logical volume, unmount /var, and resize2fs the filesystem.
Worked before on /usr (but see later), but for /var, I get a "device busy" error. (lsof | grep var) and (fuser -v /var /var/*) report no open files.
Absent the ability to resize MOUNTED ext3 filessystems, it would be highly desirable to be able to unmount most if not all of the filesystems. I am not alone, it seems, in expecting this.
I was dismayed to find in 7.04 single user mode that even /usr could only be dismounted in SINGLE USER MODE once certain processes were manually killed. But that is another story. The bigger problem still remains that in 6.10, I do not know how to overcome the "device busy" problem for /var.
I would like to here from anyone who knows how to dismount /var in single user mode. Any comments from the developers regarding this issue?

---

### Post by zvacet on 2007-04-23
You can not umount partition when your OS is runing.You have to boot up your live Cd or Gparted live CD,and then resize partition.I don´t understand why you put var as separate partition,but you customize your comp as you wish.
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by goslar on 2007-04-23
> **zvacet said:**
> You can not umount partition when your OS is runing.You have to boot up your live Cd or Gparted live CD,and then resize partition.I don´t understand why you put var as separate partition,but you customize your comp as you wish.
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

Putting /var on a separate filesystem is common practice. For one thing, separate filesystems for / (root), /var, /tmp, /opt, /home, /usr may reduce system downtime caused by certain denial of service attacks.

---

