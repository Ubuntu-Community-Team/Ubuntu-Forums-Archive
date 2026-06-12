---
title: "[ubuntu] How to expand Ubuntu partition?"
date: 2014-05-15
forum: General Help
---

### Post by FDRmz4Y on 2014-05-15
I just installed 14.04 on my system using Wubi. I selected 30GB as the size of my partition in the Wubi GUI before my install. Here is what my HDD looks like:

NAME   FSTYPE   SIZE MOUNTPOINT LABEL
sda           465.8G            
&#9500;&#9472;sda1 ntfs     1.5G            SYSTEM_DRV
&#9500;&#9472;sda2 ntfs   449.6G /host      Windows7_OS
&#9492;&#9472;sda3 ntfs    14.7G            Lenovo_Recovery
sr0            1024M            
loop0  ext4      29G /          


So I'm confused as to where Ubuntu was being installed using Wubi. I think it was actually installed as part of the sda2 drive and as a part of Windows, so I'm not exactly sure how to expand this partition now since it's part of Windows.

---

### Post by Impavidus on 2014-05-15
Wubi, which is no longer supported, installs Ubuntu on a virtual partition, which is a big file called root.disk located somewhere on a Windows partition. The maximum size of it is 30GB. If you want more, you'll have to create a real dual boot system. As you only have three primary partitions, that shouldn't be too complicated.

You can migrate wubi ([https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)) or start again. In both cases you have to do some preparations. Shrink the Windows7_OS partition using Windows tools. If you want a fresh install, uninstall Wubi using the uninstaller in Windows. If you want to migrate, use gparted to create new partitions (/ and swap). If you want a fresh install, you can just boot the live disk, install and select "install alongside Windows 7". It will create the partitions for you.

---

