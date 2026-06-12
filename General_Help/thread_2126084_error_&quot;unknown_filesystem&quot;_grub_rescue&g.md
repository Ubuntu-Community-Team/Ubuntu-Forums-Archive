---
title: "error: &quot;unknown filesystem&quot; grub rescue&gt;  after deleted partition"
date: 2013-03-15
forum: General Help
---

### Post by michk on 2013-03-15
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]I had dual boot with windows 7 and ubuntu 10.04 running, and working. After deleting the partitions of ubuntu in windows for removal of ubuntu from my laptp, i got this error..please help me how could i load my windows operating systm..[/COLOR]:confused::confused:

---

### Post by mickon on 2013-05-31
- Make or find Ubuntu LiveCD.
- Boot into your Ubuntu LiveCD
- Go to System - Administration - Software Sources and enable the
  Universal repository.
- Open a terminal.
- Type sudo apt-get install ms-sys
-  (If can not find package, download from  [http://sourceforge.net/projects/ms-sys/files/ms-sys%20development/2.3.0/ms-sys-2.3.0.tar.gz/download?use_mirror=switch&download=](http://sourceforge.net/projects/ms-sys/files/ms-sys%20development/2.3.0/ms-sys-2.3.0.tar.gz/download?use_mirror=switch&download=)   and install)
- Type sudo fdisk -l You are looking for a partition  like /dev/sda1-- NTFS, (or maybe your windows install on sdb or  hda?).  If partition(s) exists...
- Type sudo ms-sys -m /dev/sda (or sdb or hda)
- Reboot. Remove LiveCD.
- :)

---

