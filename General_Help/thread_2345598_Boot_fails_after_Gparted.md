---
title: "Boot fails after Gparted"
date: 2016-12-06
forum: General Help
---

### Post by Shaktijar on 2016-12-06
Hi, everybody!

When I have resized a NTFS partition on a HDD by means gparted 0.28 my Ubuntu (placed at the same HDD) stoped boot.

I have tried Boot-Repair-64bit live CD.  The result was a failure. 
It is here [URL="http://paste.ubuntu.com/23581387/"]http://paste.ubuntu.com/23581387/

[/URL]Also I've done a check with new e2fsck v.1.43 from a System Rescue CD```

sudo e2fsck -V /dev/xxx
```
And the result was "Clean".

A command```
sudo grub-install --root-directory=/mnt/ /dev/xxx
```
returns a stage1 grub error.

---

### Post by yancek on 2016-12-06
You are always better off using windows tools to modify windows partitions/filesystem, Linux tools to modify Linux partitions/filesystems.  I don't think xp has any tools built in.  On the other hand, GParted usually works.  You don't indicate what change you made and to what partition.  Did you increase or decrease you ntfs partition and which one?  I don't see any Grub files on the Ubuntu partition or the boot repair output.  Your xp boot.ini file only shows windows entries so that doesn't help.

Your output does not show any grub.cfg file either so it looks like Grub is gone/overwritten.  I'm surprised at the 'stage1 is missing' error as that file was only used in Grub Legacy which Ubuntu hasn't used for seven years.  Did you increase the size of sda6 (D partition) and shrink the Ubuntu.  More details on exactly what you changed.

---

