---
title: "Ubuntu Permissions Problem"
date: 2018-03-29
forum: General Help
---

### Post by kristin3l on 2018-03-29
Hello!

I've just installed Ubuntu on one of my PC's and i want to use it as a localhost PC for my work.

I have 2 HDD's installed in the PC that's using Ubuntu. One SSD with the Ubuntu OS installed on it (ext4 format) and 1 normal HDD formatted as FAT32 (because i have to access this HDD from another PC over the network that's using Windows). Everything works just fine, I can access the shared HDD from Windows through the network but the only issue is that the folders and files that I Copy/Create on the FAT32 partition have 755 permissions and I need to change them to 777 but I don't know how...

Can anyone help me?

Thanks!

---

### Post by bryantj247 on 2018-03-29
FAT32 doesn't support permissions, so Linux uses the permissions specified when the drive is mounted. If your drive is auto-mounted, you'll find the settings you need to change in /etc/fstab, or you can edit them with gnome-disks or a similar GUI program. 

If you add umask=000 to the options for your FAT32 drive, and remove the fmask or dmask options if present, it should work. These options are permission masks, which means they specify the permission bits you *don't* want to set. The default is 022, which results in 755 permissions. By changing it to 000, you get 777 permissions, just be aware that this is for all users.

---

