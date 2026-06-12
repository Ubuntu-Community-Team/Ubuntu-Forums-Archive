---
title: "usb as read only"
date: 2015-08-31
forum: General Help
---

### Post by atux on 2015-08-31
hello everyone.
    
    i have a usb stick that it gets recognised as read only.
    how do i fix that issue, so i could format it and have a usable usb    stick?
    i have tried with dosfsck -a without success
    
                  Disk /dev/sdb: 31.4 GB, 31449415680 bytes
        19 heads, 19 sectors/track, 170151 cylinders, total          61424640 sectors
        Units = sectors of 1 * 512 = 512 bytes
        Sector size (logical/physical): 512 bytes / 512 bytes
        I/O size (minimum/optimal): 512 bytes / 512 bytes
        Disk identifier: 0x10635f1f
        
        
           Device Boot      Start         End      Blocks   Id           System
        /dev/sdb1   *        8064    61424639    30708288    7           HPFS/NTFS/exFAT
        **root@netbook:~#** dosfsck -a /dev/sdb1
        dosfsck 3.0.13, 30 Jun 2012, FAT32, LFN
        open: Read-only file system
        **root@netbook:~#** 
        
        
      
    
    even gparted has it recognised as read only

---

### Post by Bucky Ball on 2015-08-31
Install Gparted if it is not already installed. Insert the stick. Launch Gparted and right click the USB stick partition(s) and unmount them. Right click again and delete them. Any luck?

---

### Post by sudodus on 2015-08-31
If the device is read-only also after unmounting (unmount as suggested by Bucky Ball), there may be severe problems.

As a last resort you can try to [wipe the first megabyte with mkusb](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device). If that works you can try with gparted again, first create a partition table, then create one or more partitions.

If that does not work, I'm afraid that the pendrive is 'gridlocked'. See the following link for more details.

[Pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

