---
title: "How to remove grub"
date: 2016-02-09
forum: General Help
---

### Post by tom171 on 2016-02-09
Checking to see if there's a way to remove grub?  I don't want to remove Ubuntu.  I used a CD to completely erase hard disk and install Ubuntu.  It also installed grub so I get options of booting to Ubuntu or running some memory tests.  I don't need any of that and just want it to boot into Ubuntu.  Sometimes it will lock at the grub screen and I have to hard shut down.  Is there a way to remove grub and just boot directly to Ubuntu.  Everything I search for shows how to remove it and keep Windows, but I don't have Windows.

---

### Post by ajgreeny on 2016-02-09
If you have only ubuntu installed you should not see the grub menu at all, so either something is wrong or you do have another OS installed on the computer.  You can not remove grub; if you did so you would not be able to boot to Ubuntu.  However you can stop grub showing in a variety of ways, so let's explore what is going on here.

Can you show us the output of terminal command ```
sudo parted -l
``` in code tags please (see my signature below for a "how-to") which will show us the partitions on disk.

It will also help if you run Boot-Repair from my signature and just run the Boot-info script, then post back here the pastebin link it gives you.

---

### Post by grahammechanical on 2016-02-09
The default setting of Grub is to load the default OS after about 10 seconds unless we press a key. In that situation the count down will stop. Is that the freezing at the Grub screen that you mention?

Even with only Ubuntu on the machine the Grub menu will display if the shift key is pressed. Sticky keys, anyone?

Regards.

---

### Post by tom171 on 2016-02-10
```

[sudo] password for test: 
Model: ATA Hitachi HTS72323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  316GB  316GB   primary   ext4            boot
 2      316GB   320GB  4149MB  extended
 5      316GB   320GB  4149MB  logical   linux-swap(v1)

```

[http://paste.ubuntu.com/15010678/](http://paste.ubuntu.com/15010678/)

---

