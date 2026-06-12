---
title: "How to install Windows 7 on a computer with Ubuntu 13.10 already installed"
date: 2014-01-28
forum: General Help
---

### Post by nem01 on 2014-01-28
The title pretty much says it all. I would like to dual boot windows 7 and Ubuntu. I already have gparted installed but I don't know how to use it. My computer is a Toshiba Satilite with a 1TB HDD, core i7 and 6gb ram.

Thanks in advance.

---

### Post by nothingspecial on 2014-01-28
You would need to create a partition for Windows to install on first, ntfs will be fine. You wont be able to do this using gparted while Ubuntu is running if Ubuntu is installed in one partition over the entire disk, you need to use gparted from the live cd to shrink Ubuntu then make a new partition. Then you can install windows to the empty partition.

Once it has installed you will need to go back to live cd and run boot repair  [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") so you can choose between them at boot.

It goes without saying that you need to back everything up first in case something goes wrong

---

### Post by justleen on 2014-01-28
in very condensed form:
- resize your partitions to make room for windows,create new partition  for  windows. ( probably best done from a live usb/cdrom enviroment since this will leave your disk unmounted and free to resize)
- install windows
- reinstall grub (since windows install will overwrite MBR) 

let me know if you need details for any of those steps

---

### Post by justleen on 2014-01-28
double posted

---

### Post by nem01 on 2014-01-28
How do I create another partition for windows within the live cd? For that you're gonna  have to speak to me as if I'm slow.  Thanks.

---

### Post by justleen on 2014-01-28
start gparted (through the ubuntu search menu ) select the disk you want, select resize and after that apply.

A more detailed step by step is here: [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

