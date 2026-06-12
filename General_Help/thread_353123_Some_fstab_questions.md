---
title: "Some fstab questions?"
date: 2007-02-04
forum: General Help
---

### Post by poohbear1616 on 2007-02-04
So I'm reading about the fstab settings and about what various settings in each row mean and so I pull up my fstab to take a look, which looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I'm using dapper btw.
Since there is not a mount point given for my swap partition but seems active when I use "top" in terminal, I assume this is ok and is normal for ubuntu???

Also I noticed there is no entry at all for my dvd player which should be /dev/hdd, so does that mean it would not mount? Or does it just mount with pre-determined defaults? I haven't used it yet in ubuntu since I rarely use it anyways.

My floppy mounts when I put one in and open the file browser but I see no entries for it either.:confused:

---

### Post by bom28 on 2007-02-04
Mount point are for filesystems, swap have no filesystems (it's just one big file) so they don't use a mount point. Run "sudo swapon -s" to check which swap partitions are used.

---

