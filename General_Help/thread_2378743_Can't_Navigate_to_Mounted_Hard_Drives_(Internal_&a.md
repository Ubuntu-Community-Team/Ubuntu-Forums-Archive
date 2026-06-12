---
title: "Can't Navigate to Mounted Hard Drives (Internal &amp; External)"
date: 2017-11-26
forum: General Help
---

### Post by rwonder on 2017-11-26
Hey everyone,

I have 6 drives: 3 internal and 3 external. My end goal is to copy the media from the external drives to my internal drives.
I have a few questions:
1) I have mounted all drives (as you can see below). I would like my internal drives sda/sdb/sdc to be permanently mounted obviously (similar to C:\ D:\ E:\).  Have I accomplished that based on the simple mount command I used?
2) Follow-up to the above. I used the same mount command for my external drives, would I have to now use an unmount command for the external drives? Seems logical, but again I expect a more strict mount for my internal drives which is what's confusing me.
3) Although I have mounted all the drives (see image below), I cannot navigate to any. Super confused why they are considered mounted but not actually showing up in the file system when I cd to the location. HELP!!!

```

NAME                    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sdf                       8:80   0   1.8T  0 disk  
&#9492;&#9472;sdf1                    8:81   0   1.8T  0 part  /mnt/tmp
sdb                       8:16   0 931.5G  0 disk  
&#9492;&#9472;sdb1                    8:17   0 931.5G  0 part  /media
sdg                       8:96   0   1.8T  0 disk  
&#9500;&#9472;sdg3                    8:99   0   1.6T  0 part  /mnt/tmp
&#9500;&#9472;sdg1                    8:97   0   200M  0 part  
&#9492;&#9472;sdg2                    8:98   0 238.8G  0 part  /mnt/tmp
sde                       8:64   0   2.7T  0 disk  
&#9492;&#9472;sde1                    8:65   0   2.7T  0 part  /mnt/tmp
sdc                       8:32   0   3.7T  0 disk  
&#9492;&#9472;sdc1                    8:33   0   3.7T  0 part  /media
sda                       8:0    0   3.7T  0 disk  
&#9500;&#9472;sda2                    8:2    0   488M  0 part  /boot
&#9500;&#9472;sda3                    8:3    0   3.7T  0 part  
&#9474; &#9492;&#9472;sda3_crypt          253:0    0   3.7T  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--vg-root   253:1    0   3.6T  0 lvm   /
&#9474;   &#9492;&#9472;ubuntu--vg-swap_1 253:2    0  15.9G  0 lvm   [SWAP]
&#9492;&#9472;sda1                    8:1    0     1M  0 part  

```

Thanks in advance!

---

### Post by yancek on 2017-11-26
If you want a filesystem on a partition permanently mounted on boot, you need a proper entry in the /etc/fstab file.  Thousands of tutorials and examples of that online and probably using the search function on these forums.  You will need to know what permissions/parameters you want for the partition(s).  Have you created these entries?

You need a separate mount point for each partition and you have 4 partitions with the same mount point:  /mnt/tmp
Those partitions are sde1, sdf1, sdg2 and sdg3.  Each needs a different mount point.  You can simply create a directory with the name of the partition for the sake of simplicity, /mnt/sde1, /mnt/sdf1, etc... 
or give them any name they want.

What mount command did you use as all you have posted is the output of the lsblk command?  Simply creating a mount point doesn't mean they are mounted so what did you use?
I think part of the problem at least is that you have a single mount point for multiple partitions which is not going to give you what you want.

---

### Post by rwonder on 2017-11-26
Thanks for the reply yancek.

1) Thanks, honestly I didn't know what to search. Even when I search "mount internal drive", "external" comes up
Will this do the trick for permanent mounting? [https://askubuntu.com/questions/154180/how-to-mount-a-new-drive-on-startup](https://askubuntu.com/questions/154180/how-to-mount-a-new-drive-on-startup)

2) The command I used was: "sudo mount /dev/sdb1 /mnt/tmp"
I'll make separate directories for each drive when mounting but please let me know if that command is insufficient to actually mount the drives.

Thanks!

---

### Post by yancek on 2017-11-26
```
sudo mount /dev/sdb1 /mnt/tmp
```

That should work with a known Linux filesystem type.  If you get an error, you may have to indicate a filesystem type but if these are all standard Linux it should not be a problem.

> sudo mount -t ext4 /dev/sdb1 /mnt/tmp

The -t in the above command is for the type filesystem and the filesystem is ext4, the rest you know.

If you set the same mount point for different drive partitions you will likely get a message "already mounted" when you try to manually mount a second partition on the same mount point:  /mnt/tmp
The method for mounting internal or external drives is the same.  You just need to indicate the specific drive/partition.

I would suggest you use the official Ubuntu Documentation on fstab.  It's at the link below and gives you a detailed explanation of the various options/parameters and there are also example entries which you can modify and use.  It's best to use the examples with the UUID rather than the device, i.e.: /dev/sdb1

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by rwonder on 2017-11-26
Looks like I made some progress...
A few tips for future readers...
 - I used Gparted to convert one of my drives from MBR to GPT
 - gnome-disks makes it easy to configure partitions
 - Here is what I had to do to permanently mount the two extra internal hard drives I had:
> rwonder@superduper:/Med2$ sudo mkdir /Med3
rwonder@superduper:/Med2$ blkid | grep sdb1 > ~/UUID_data
rwonder@superduper:/Med2$ cp /etc/fstab ~/fstab_bkup
rwonder@superduper:/Med2$ cat ~/UUID_data 
rwonder@superduper:/Med2$ vi /etc/fstab

Note: In this file, you'll do something like this "UUID=0AED64F912A2GB1E /Med3 ntfs defaults 0 2". Replace the UUID, mount location, and type according to the results above.


Here's what I still don't know and need help with:
From what I understand (based on my digging around), there is no difference between a usb stick and an internal hard drive other than (1) what's inside /etc/fstab and that there is a dedicated mount location associated. Then I used gnome-disks so that my internal drives won't show up in the Ubuntu Launcher. Am I right? Would love to learn more.

P.s. for future readers' reference: [https://askubuntu.com/questions/769974/how-to-automatically-mount-2nd-internal-hard-drive](https://askubuntu.com/questions/769974/how-to-automatically-mount-2nd-internal-hard-drive)

---

### Post by yancek on 2017-11-27
The entries for external usb/flash drives would be similar to the entries for an internal drive with the obvious change for the device or UUID and mount point.  I also notice in your last post that you are using a windows filesystem so the standard Linux permissions will not apply.  A problem you may run into is that with an external drive/flash drive, if you have an entry in fstab for it and it is not plugged in on boot you will get a message on boot indicating it can't be found which will delay boot.  Usually you can just hit the S key to skip waiting an continue booting.

---

