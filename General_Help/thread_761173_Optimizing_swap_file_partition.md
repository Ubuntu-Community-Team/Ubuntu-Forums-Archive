---
title: "Optimizing swap file partition"
date: 2008-04-20
forum: General Help
---

### Post by nihilion on 2008-04-20
Dear Ubuntu community,
I'm new to the Linux community, so please forgive my complete noobiness if my question shows no understanding of how linux works.

My objective is to optimize my swap partition. In windows, I keep my pagefile on a second physical harddrive. Can I do this with linux? 

Currently, I have a dual boot setup with Windows XP and Ubuntu. 

* Windows is on hard drive 0, swapfile is on harddrive 1
* Linux is on harddrive 1, system and swap are on harddrive 1

Thinking i could optimize my linux swap the same way i optimized my windows, I created a small 2 gig partition on HD0 using partition magic (formated as linux swap). 

Would it improve performance if i made that partition my linux swap? If so, how do I do it? If not, is there something else i could do?

Thank you so much for your time.

Nick

---

### Post by erginemr on 2008-04-20
> **nihilion said:**
> Dear Ubuntu community,
I'm new to the Linux community, so please forgive my complete noobiness if my question shows no understanding of how linux works.

My objective is to optimize my swap partition. In windows, I keep my pagefile on a second physical harddrive. Can I do this with linux? 

Currently, I have a dual boot setup with Windows XP and Ubuntu. 

* Windows is on hard drive 0, swapfile is on harddrive 1
* Linux is on harddrive 1, system and swap are on harddrive 1

Thinking i could optimize my linux swap the same way i optimized my windows, I created a small 2 gig partition on HD0 using partition magic (formated as linux swap). 

Would it improve performance if i made that partition my linux swap? If so, how do I do it? If not, is there something else i could do?

Thank you so much for your time.

Nick

Hi Nick,

It will have no effect performance-wise, if you have 1 GB or more RAM, yet you can try it anyway. You need to check the input data for your partitions:
```
sudo fdisk -l
```
take note of where your new swap partition is and edit your /etc/fstab file:
```
sudo cp /etc/fstab /etc/fstab.working
gksudo gedit /etc/fstab
```
and have the line for swap point to your new swap partition. 

If you need more details, please don't hesitate to post the outcome of the first command and the contents of your /etc/fstab file.

---

### Post by nihilion on 2008-04-21
Hi, thank you so much for your response. I tried what you suggested. Results are as follows:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d6f2d6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/sda5            2551        9461    55512576    7  HPFS/NTFS
/dev/sda6            9462        9723     2104483+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x785b71a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        4318    34676302+   f  W95 Ext'd (LBA)
/dev/sdb2   *        4319        9729    43463857+  83  Linux
/dev/sdb5               2        1531    12289693+   7  HPFS/NTFS
/dev/sdb6            1532        4081    20482843+   7  HPFS/NTFS
/dev/sdb7            4082        4318     1903671   82  Linux swap / Solaris

AND...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=6f592ca0-d521-4ed7-8343-dcb4de97d426 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb7
UUID=6af97bc7-faa8-4619-a8bf-1057d5c16c63 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
 

I can recognize my current and desired swap partitions on my disks, but I'm unsure about the addressing and how, exactly, I can make the suggested changes. 

Can you please be more specific in what I need to do? Also, I would really appreciate it if you could take a moment and briefly explain how the linux swap file works, as it appears to be quite different from windows.

Thank you again.

Nick

---

### Post by erginemr on 2008-04-22
Hi Nick,

As you have also guessed correctly, the line to change in /etc/fstab is:
```
# /dev/sdb7
UUID=6af97bc7-faa8-4619-a8bf-1057d5c16c63 none swap sw 0 0
```
which points to /dev/sdb7. We shall have it point to /dev/sda6, which is fairly easy.

**1. **You need to edit /etc/fstab with root permissions. First, let us back up the old file. From a terminal:
```
sudo cp /etc/fstab /etc/fstab.old
```
And then:
```
gksudo gedit /etc/fstab
```
**2.** You need to replace the above two lines with:
```
/dev/sda6 none swap sw 0 0
```
**3.** Alternatively, you can learn the UUID code for your swap partition with:
```
blkid   
#or with:
sudo vol_id -u /dev/sda6
```
and write this code in:
```
# /dev/sda6
UUID=............................... none swap sw 0 0
```

**4. **Once you make sure that your new swap is ready to roll, you can erase the older one(/dev/sdb7), reformat it to NTFS and add it to (dev/sdb6) by either installing GParted under Ubuntu and using it or by downloading and burning the GParted Live CD:
***[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)***

---

### Post by erginemr on 2008-04-22
**[This part is optional...]**

**5. **For your information, UUID is a new way to represent partitions. Yet, since it has created problems in my previous system restore attempts, I have decided to revert to the old way of mounting partitions, which in your case, would be:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sdb2  / ext3 defaults,errors=remount-ro 0 1
/dev/sda6  none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
```

For more information on UUID's:
[I][B][http://wolfger.wordpress.com/2007/08/31/ubuntu-and-uuid/](http://wolfger.wordpress.com/2007/08/31/ubuntu-and-uuid/)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=512623](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=512623)
[/B][/I]

**6. **Regarding what swap is and the optimum swap size, it is a harddrive area used by the system to dump part of the memory temporarily, when your physical RAM space is filled by running programs and background services. Having to use the swap area is not something desirable, as the time to access the hard drive is considerably longer than the time to access RAM. 

So, Ubunteros with more than enough RAM are always on the look out to minimize swap. If you have equal to or more than 1 GB RAM, unless you are running a server or many simultaneous memory intensive applications, then the system hardly ever uses your swap. If you have 512 MB RAM, swap is rarely used. On the other hand, if you have 256 MB or less RAM, you will begin to notice some hard drive activity. In this context, depending on your RAM size you may have little to no gain by transferring the swap partition of another of your hard drives this way.

There is a system setting called swappiness that regulates how much the system should depend on the swap. If you have more than enough physical RAM (say 1 GB), you may consider decreasing this value to limit the redundant use of swap. To change this value (whose default is 60 on a scale of 100) on the fly:
```
sysctl vm.swappiness  # to view the current percentage
sudo sysctl vm.swappiness=10
```
and to make it permanent, edit /etc/sysctl.conf with:
```
gksudo gedit /etc/sysctl.conf
```
and add the line to the end of the file to set it automatically at boot time:
```
vm.swappiness=10
```

For more information on swap and swappiness:
[I][B][http://ubuntuforums.org/showthread.php?t=727667](http://ubuntuforums.org/showthread.php?t=727667)
[http://ubuntuforums.org/showpost.php?p=4537237&postcount=8](http://ubuntuforums.org/showpost.php?p=4537237&postcount=8)
[http://ubuntuforums.org/showpost.php?p=4537260&postcount=9](http://ubuntuforums.org/showpost.php?p=4537260&postcount=9)
[/B][/I]

**7.** Finally, there is a terminal application "top" that lets you view the system resources (cpu usage, memory consumption per application, free and used memory, swap usage, etc.), which is the console counterpart of Gnome System Monitor. I suggest you to install a similar console process viewer "htop" instead, which has more features and exhibits more compatible output with gnome-system-monitor:
***[http://ubuntuforums.org/showpost.php?p=4539416&postcount=13](http://ubuntuforums.org/showpost.php?p=4539416&postcount=13)***

---

