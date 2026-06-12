---
title: "No Permissions to read or write to new WD Hard drive"
date: 2014-06-20
forum: General Help
---

### Post by 777funk on 2014-06-20
What should I do in this case. Never had this before. I just installed and GPT Partitioned/EXT4 formatted a new WD drive in GParted as Root (Xubuntu) and it's not letting me write any data. Any idea what the problem could be?

I tried to chmod the main location of the drive but only the Lost and Found is getting the new 777 permissions.

---

### Post by tgalati4 on 2014-06-20
Open a terminal and post the output of:

```
sudo fdisk -l
```

Sometimes new disks need some break-in.

---

### Post by 777funk on 2014-06-20
Thanks. Here's the output for that disk:

```

Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


```

It's something with permissions because even the "Lost and Found" folder is locked until I chmod by the following:
cd /media/nick/WD3TB/
sudo chmod -R -v 777 

Then what should have been the entire drive (I think anyways) should be writable is not. Only the Lost and Found folder is writable after this operation (but wasn't before).

---

### Post by coffeecat on 2014-06-20
> **777funk said:**
> It's something with permissions because even the "Lost and Found" folder is locked until I chmod by the following:
cd /media/nick/WD3TB/
sudo chmod -R -v 777 

That's not the way to do it. If you use the -R option, you chmod files in the filesystem when you need to chmod the actual ext4 filesystem. And you don't want to change ownership and permissions of lost + found anyway which should be owned by root. Also, it's better to use chown. You need to mount the filesystem and then chown the mountpoint which has the curious effect of chowning the filesystem and not the mountpoint. Assuming you've mounted the partition on /media/nick/WD3TB, don't do any cd-ing, but simply:

```
sudo chown yourusername: /media/nick/WD3TB
```

Substitute your login name for yourusername and don't forget the trailing colon which will chown the filesystem to your default usergroup. That's all you have to do. You'll find you'll be able to write files and create folders once you've done that even if you mount it to a different mountpoint. You can chmod 777 but only if you need other users to be able to write to the partition.

---

### Post by 777funk on 2014-06-20
Thanks! This worked. I'm still very curious as to why this particular drive required ownership? 

All other drives (windows partitions etc) are writable.

---

### Post by coffeecat on 2014-06-20
> **777funk said:**
> Thanks! This worked. I'm still very curious as to why this particular drive required ownership? 

All other drives (windows partitions etc) are writable.

When you created the partition in gparted it was owned by default by root. That's normal for a Linux filesystem, which is why you had to chown the filesystem to make it writeable from your Ubuntu account. If you use Disk Utility or Disks or whatever it is called in Xubuntu, there is a tickbox "own filesystem" when creating or formatting a partition. But I prefer to use gparted and simply chown as necessary any partition/filesystem I create.

With a Windows partition, you are talking about a ntfs filesystem, which is a Microsoft filesystem which doesn't support Unix/Linux ownership and permissions. Permissions and ownership of ntfs files in Ubuntu are determined by the mount options and if you mount from the file manager, the system ensures that you can write to it.

---

