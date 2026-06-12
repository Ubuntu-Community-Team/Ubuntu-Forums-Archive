---
title: "BTFS vs EXT4"
date: 2016-07-09
forum: General Help
---

### Post by uwe-bungto on 2016-07-09
Is there any advantage to the normal user in using BTFS instead of EXT4? 
I am using Ubuntu studio mainly for video editing.

---

### Post by grahammechanical on 2016-07-09
BTFS allows the user to create snapshots of the file system which can then be rollback to. But it is all done through the command line. So, a person would need to be a little bit more than a normal user. The absence of a GUI snapshot management utility is due to the fact the BTFS is developed mainly for server systems.

There is one Linux distribution that has BTFS by default. I think it is OpenSuse and there is a GUI snapshot management utility. But the other year when I was experimenting with BTFS I failed to get the OpenSuse snapshot utility working. It is called Snapper. by the way. Things might have improved since I experimented.

[https://en.opensuse.org/Portal:Snapper](https://en.opensuse.org/Portal:Snapper)

[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

> When installing Ubuntu in one large btrfs-Partition without an extra  boot-partition, take care to keep about 1 Mib space free at the  beginning of the disk. This is possible using the partition manager in  the Ubuntu installer. When there is not this space, the installer fails  at the end when trying to install Grub!

I do not know if that is still applicable. I think that you will find that you will soon become someone who is more than a normal user. 

Regards.

---

