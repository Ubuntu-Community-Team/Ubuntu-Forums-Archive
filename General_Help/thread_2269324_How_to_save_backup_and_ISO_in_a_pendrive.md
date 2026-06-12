---
title: "How to save backup and ISO in a pendrive?"
date: 2015-03-14
forum: General Help
---

### Post by flaymond on 2015-03-14
Hello, I know this possible, I just don't know if I can save/install them separately in different partition. I got only one USB, I always use that USB (just have one partition) for Ubuntu backup installation. Now, I found that I need to save my files and works too, but not with cloud backup since my connection pretty slow. So I need to backup Ubuntu installation and my files in one pendrive. Is this possible?

* How can I choose which partition to use that contain 2 partition with ubuntu installation and my files when try to boot with it? (whenever my PC crash or need to rescue boot)

---

### Post by sudodus on 2015-03-14
It is possible, but maybe not the best way, because USB pendrives can fail without a warning. All devices can fail, but ***hard disk drives are much more reliable***, so better for backup. Unmount and disconnect the backup drive, when it is not used.

***Maybe you can get an old hard disk drive and you can connect it via an adapter***, that is often called 'USB to IDE & SATA cable' or with a box (that does the same job plus protects the HDD, but some boxes are not cooling the HDD enough, so it can get overheated and damaged). That way you can even use an old PATA hard disk drive (often called IDE drive). You can also connect an old CD or DVD drive with that kind of parallel connection.

-o-

But if you want to use a big enough pendrive for storage and installing, you can have ***one partition with FAT32*** and use the Ubuntu Startup Disk Creator or Unetbootin to flash the installer into it. You can have ***another partition with ext4*** so that you can preserve file permissions if you backup system directories or your home directory with the hidden configuration files with ***rsync*** or some other tool.

---

### Post by flaymond on 2015-03-14
I got a 32gb pendrive, is it enough? I'm using it to install Xubuntu. For the first partition(Xubuntu partition), how much should I provide the space, minimum?

---

### Post by sudodus on 2015-03-14
The current xubuntu iso files are around 1 GB, but I would make the first and FAT32 partition at least 2 GB to have some margin for future and bigger iso files. (If you want to try really big 'DVD sized' iso files, you need 5 GB.) The extra size can also be used for a casper-rw file to make a persistent live system. The rest of the pendrive can be used for an ext4 partition.

---

### Post by flaymond on 2015-03-15
Thank you! :)

---

