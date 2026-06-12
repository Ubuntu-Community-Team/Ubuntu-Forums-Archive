---
title: "Accdessing Windows"
date: 2007-03-01
forum: General Help
---

### Post by vybz on 2007-03-01
Hey,

Here is my situation.  I have a laptop which was running windows.  Windows somehow got corrupted and wont load anymore.  I booted the computer from Ubuntu 6.10 Live CD.  I then mounted the hd containing Windows on /mnt/win.  I am able to view all the Windows files and directories, but when I open each directory it is empty.

Basically I can see my windows partition, but all my directories are empty.

Anyone know why?

---

### Post by booe on 2007-03-02
I *think* this might be because you have mounted your drive with the incorrect permissions. For example, if you mount it with root-like permissions - then only root will have access to list directories and read files on your Windows partition.

Have you tried using this approach:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

Or if you have installed Ubuntu on a computer, you can automatically mount a Windows NTFS drive by using this method:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

Please note: both of the above methods only work for **read only** access. The same pages linked to above also contain information on how to write to NTFS drives, if you need to do this.

---

