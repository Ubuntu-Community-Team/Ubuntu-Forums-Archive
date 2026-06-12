---
title: "not mount partition?"
date: 2012-10-21
forum: General Help
---

### Post by alirezamax on 2012-10-21
hi, I'm use ubuntu 12.4 But not mount on partition  help me :(

[http://ubuntuforums.org/attachment.php?attachmentid=225872&stc=1&d=1350853702](http://ubuntuforums.org/attachment.php?attachmentid=225872&stc=1&d=1350853702)

---

### Post by ajgreeny on 2012-10-21
Please open a terminal and show the output of ```
sudo fdisk -l
```Use the code tags after copying the text in your reply by selecting the text and using the # icon in toolbar.  

Whilst dealing with the reply toolbar please add an image next time with the attchment icon (paperclip) and follow the self explanatory dialogs that appear.  In-line images are a problem occasionally if too large.

---

### Post by wildmanne39 on 2012-10-21
Please do not post duplicates, it dilutes community effort.

---

### Post by papibe on 2012-10-21
This is a duplicate of:  [http://ubuntuforums.org/showthread.php?p=12309806#post12309806](http://ubuntuforums.org/showthread.php?p=12309806#post12309806)

Threads has been Merged.

---

### Post by alirezamax on 2012-10-22
excuse me duplicate post:(

 sudo fdisk -l === >


```

Disk /dev/sda: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2cb72cb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    19533821     9766879+   7  HPFS/NTFS/exFAT
/dev/sda2        19535101   488392064   234428482    f  W95 Ext'd (LBA)
/dev/sda5        19535103   122881184    51673041    7  HPFS/NTFS/exFAT
/dev/sda6       122884096   190167039    33641472   83  Linux
/dev/sda7       190169088   231127039    20478976   83  Linux
/dev/sda8       231143283   488392064   128624391   83  Linux

Disk /dev/sdb: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders, total 3944448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x564102bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8192     3944447     1968128    7  HPFS/NTFS/exFAT
```

---

### Post by alirezamax on 2012-10-22
help me :(

---

### Post by ajgreeny on 2012-10-22
OK, I am assuming this error pops up at boot time, so now let's see the output of ```
sudo blkid
``` and ```
cat /etc/fstab
```
Paste the output in a New Reply, then highlight entire file and click on # in toolbar (code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ CODE] paste here [ /CODE] tags.

---

### Post by alirezamax on 2012-10-22
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=54552f66-2313-44ae-8e5e-fa747ffaefd7 /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```



sudo blkid 

```

/dev/sda1: UUID="01CDAC4FC4565B00" TYPE="ntfs" 
/dev/sda5: UUID="F45E66795E663510" TYPE="ntfs" 
/dev/sda6: UUID="acea4b28-e31d-4282-91e1-17b98b79a584" TYPE="ext4" 
/dev/sda7: UUID="54552f66-2313-44ae-8e5e-fa747ffaefd7" TYPE="ext4" 
/dev/sda8: UUID="e54f8698-d222-48f1-a847-5373c72c6e69" TYPE="ext4" 

```

---

### Post by ajgreeny on 2012-10-22
You can add sda8 to your automounted partitions by editing fstab.

Use terminal command ```
sudo cp /etc/fstab /etc/fstabbak
``` first to make a backup then ```
gksudo gedit /etc/fstab
``` and add two lines to the bottom of the file
```
# Data partition on sda8
UUID=e54f8698-d222-48f1-a847-5373c72c6e69 /media/data ext4 defaults,relatime 0 2
``` save it, and finally make the mountpoint folder with ```
sudo mkdir /media/data
```
You can now check that all is well with ```
sudo mount -a
```which should not show any error.

You may also wish to give yourself ownership of the new folder with ```
sudo chown username:username /media/data
```use your own username, of course.  This should give you read/write permissions on the partition.

---

