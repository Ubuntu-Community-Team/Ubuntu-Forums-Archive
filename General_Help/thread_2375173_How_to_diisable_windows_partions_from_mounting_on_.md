---
title: "How to diisable windows partions from mounting on Lubuntu?"
date: 2017-10-22
forum: General Help
---

### Post by ezpkzmo on 2017-10-22
I have done it in the past but forgot the terminal commands to do it,       I don't want my Windows partitions  to mount or show everytime I am using Lubuntu OS, what is the terminal command to disable partitions from mounting?  Please, try not to ask for any screenshot, just assume my partition list and try responding.

---

### Post by oldfred on 2017-10-22
You actually mount it using fstab and set noauto, no permissions 777.

Examples, but you have to still create a mount point and use your UUID.
       ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list 
      
 sudo mkdir /mnt/SysRes 
         # Hide mount template examples with noauto,  you have to make the mount points yourself first
sudo mkdir /mnt/SysRes
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0

Hide windows mount with noauto: 777 is no permissions at all, UUID is better than this example with device mount
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
#hide windows 7 second hard drive
sudo mkdir /mnt/reserved
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
sudo mkdir /mnt/win7
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0
[http://askubuntu.com/questions/858029/how-to-disable-access-to-win7-disk-partitiondual-boot/858105#858105](http://askubuntu.com/questions/858029/how-to-disable-access-to-win7-disk-partitiondual-boot/858105#858105)

---

