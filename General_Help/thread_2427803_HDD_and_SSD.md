---
title: "HDD and SSD"
date: 2019-09-26
forum: General Help
---

### Post by ordak on 2019-09-26
Hi,

If I install Ubuntu on a laptop with both HDD and SSD , can I access the both drives easily using a file manager like Files(Nautilus) ?

Where would be "Home" , "Desktop" , ... , be located and can I change the location ?

---

### Post by yancek on 2019-09-26
When you open Nautilus as a user, you should be in that users /home directory and the Desktop directory should be there.  What do you mean by change the location and why would you want to do that?  
External drives should be available under the /media/username directory.  In Nautilus in the left panel, select other locations and Computer to see the drive.

---

### Post by ordak on 2019-09-26
> **yancek said:**
> When you open Nautilus as a user, you should be in that users /home directory and the Desktop directory should be there.  What do you mean by change the location and why would you want to do that?  


I want to know on which drive these directories are placed , HDD or SSD ? Is it possible to select the default drive during installation ?

> 
External drives should be available under the /media/username directory.  In Nautilus in the left panel, select other locations and Computer to see the drive.

Suppose I want to place some music/various files on SSD and the rest on HDD. Is that easy to do ?

---

### Post by mastablasta on 2019-09-26
> **ordak said:**
> I want to know on which drive these directories are placed , HDD or SSD ? Is it possible to select the default drive during installation ?

by default the /home goes where the os is installed. you can specify a different location during OS install by using the manual install option. you can also set a different file system there etc.

If you used windows before, home is kind of similar to "My Documents".

> 
 Suppose I want to place some music/various files on SSD and the rest on HDD. Is that easy to do ?

you can either just put it on another drive (the HDD  will show up in nautilus under it's volume name and you can easily access it).

or you can create symlink in home folder:
[http://manpages.ubuntu.com/manpages/bionic/man7/symlink.7.html](http://manpages.ubuntu.com/manpages/bionic/man7/symlink.7.html)
how to:
[https://askubuntu.com/questions/56339/how-to-create-a-soft-or-symbolic-link](https://askubuntu.com/questions/56339/how-to-create-a-soft-or-symbolic-link)

on my wife PC i have 2 disk drives. one is WD green for data and has one partition (sdb1), the other one is system drive separated into sda1 and sda2 partitions. OS is on sda1, data is on sdb. some backup files are on sda2 (i used them on upgrade) but mostly it is empty.

my PC has 3 disks, one has windows XP with OS partition (C), data & games partition (D) and 3rd partition for virtualbox images (E). it also has an empty unformatted partition. then i have a WD green drive with 2 NTFS parittions (H and I). one has photos and static data, the other has OS images and games images -GOG). then i have a 3 disk which has one partition (i maybe made a misitake here with only 1  partition). it has Kubuntu installed, Steam games and some photos&videos. mostly i work in Kubuntu now. i can access all partitions with no issues using the dolphin file manager. i bet it would be the same if i had Ubuntu installed using Nautilus or Nemo or whatever.

---

