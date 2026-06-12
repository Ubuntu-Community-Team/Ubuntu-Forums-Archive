---
title: "Label Disk"
date: 2007-02-28
forum: General Help
---

### Post by erugalatha on 2007-02-28
Hello,

I like the ability to label my disks in windows but since reformatting my disk drive it's mounting as ieee1394disk. There are a few issues with this - one it looks c**p second it takes longer to type (and remember how many "e's" there are).

I've tried gparted to label it but I'm gonna lose all data (vicious circle) so is there another way to label the disk the way I want?

I realised linux doesn't work like windows in labeling disks and I can mount it as a different name and that would be fine but it only mounts once as the name I choose and doesn't appear after reboot.

Ideally I'd like to re-label it without losing data.

Thanks for any help.

---

### Post by yabbadabbadont on 2007-02-28
Which type of filesystem is on the *partition* that you wish to label?

Please post the contents of your /etc/fstab file and the output of "sudo fdisk -l" when run in a terminal window.

---

### Post by vincentvee on 2007-02-28
> **erugalatha said:**
> Hello,

I like the ability to label my disks in windows but since reformatting my disk drive it's mounting as ieee1394disk. There are a few issues with this - one it looks c**p second it takes longer to type (and remember how many "e's" there are).

I've tried gparted to label it but I'm gonna lose all data (vicious circle) so is there another way to label the disk the way I want?

I realised linux doesn't work like windows in labeling disks and I can mount it as a different name and that would be fine but it only mounts once as the name I choose and doesn't appear after reboot.

Ideally I'd like to re-label it without losing data.

Thanks for any help.
is it really necessary??

---

### Post by erugalatha on 2007-02-28
Outputs should be below and I would like to be able to re-label the 500 GB disk if possible:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

```

> 
is it really necessary??

vincentvee - it's not necessary but I would still like to be able to do it. :)

---

### Post by punx45 on 2007-02-28
looks like the /dev/sdb1 is the drive in question?  (if you need to identify it by size try 'df -h' in a terminal.) (do note that due to fuzzy marketing math, the GB value on the box and the actual GB value will differ some.) (looks like its ~240GB?)

just add it to /etc/fstab to preserve its mount after reboot.

im foggy on the details so you will have to wait for someone else, or investigate on your own ;)

---

### Post by yabbadabbadont on 2007-02-28
It appears the you want to change the label of the /dev/sdb1 partition.  It is marked as a Linux partition type (83), but it appears that it is automounted since it is not listed in your /etc/fstab file.  **If** that partition has been formatted with either an **ext2** or **ext3** filesystem, then you can use the tune2fs command to change the label.  You will have to do this with the drive plugged in (of course ;)) but not mounted.  So, plug in the drive and let it be mounted.  I assume that an icon appears on your desktop when this happens.  Right-click the icon and choose eject or umount, whichever is listed.  Then open a terminal window and run:
```
sudo tune2fs -L NewLabelName /dev/sdb1
```  From then on, it should show up with NewLabelName.

---

### Post by vincentvee on 2007-03-01
> **yabbadabbadont said:**
> It appears the you want to change the label of the /dev/sdb1 partition.  It is marked as a Linux partition type (83), but it appears that it is automounted since it is not listed in your /etc/fstab file.  **If** that partition has been formatted with either an **ext2** or **ext3** filesystem, then you can use the tune2fs command to change the label.  You will have to do this with the drive plugged in (of course ;)) but not mounted.  So, plug in the drive and let it be mounted.  I assume that an icon appears on your desktop when this happens.  Right-click the icon and choose eject or umount, whichever is listed.  Then open a terminal window and run:
```
sudo tune2fs -L NewLabelName /dev/sdb1
```  From then on, it should show up with NewLabelName.
thats cool
i couldn't find any information on doing it at all

---

### Post by vincentvee on 2007-03-01
dude...didn't wanna upset you....sorry
anyway, i couldn't find anything for you
let me know if the solution below works out for you
good luck
> **erugalatha said:**
> Outputs should be below and I would like to be able to re-label the 500 GB disk if possible:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

``````

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

```

vincentvee - it's not necessary but I would still like to be able to do it. :)

---

### Post by erugalatha on 2007-03-01
Thanks for the reply but I couldn't get this to work ... I tried it a number of times rebooting each time but the drive remounted as ieee1394disk.  I then tried editing my fstab file but the drive would not mount at all then.

I dunno - maybe it cannot be done - it would just be a nice thing to be able to do as I usually give my disks strange names to amuse myself. :) Yup I'm easily amused! :p

---

### Post by vincentvee on 2007-03-20
> **erugalatha said:**
> Thanks for the reply but I couldn't get this to work ... I tried it a number of times rebooting each time but the drive remounted as ieee1394disk.  I then tried editing my fstab file but the drive would not mount at all then.

I dunno - maybe it cannot be done - it would just be a nice thing to be able to do as I usually give my disks strange names to amuse myself. :) Yup I'm easily amused! :p
i'm quite sure it can be done....i remember having a conversation with someone some time ago who had done something similar with fedora 5
but if it came to running fedora again, i would rather /dev/hda/blah/blah/blah
lol
i hate fedora

---

### Post by jw5801 on 2008-05-04
> **yabbadabbadont said:**
> It appears the you want to change the label of the /dev/sdb1 partition.  It is marked as a Linux partition type (83), but it appears that it is automounted since it is not listed in your /etc/fstab file.  **If** that partition has been formatted with either an **ext2** or **ext3** filesystem, then you can use the tune2fs command to change the label.  You will have to do this with the drive plugged in (of course ;)) but not mounted.  So, plug in the drive and let it be mounted.  I assume that an icon appears on your desktop when this happens.  Right-click the icon and choose eject or umount, whichever is listed.  Then open a terminal window and run:
```
sudo tune2fs -L NewLabelName /dev/sdb1
```  From then on, it should show up with NewLabelName.

Are there equivalent tools for FAT32, NTFS and ReiserFS? I have all my EXT2/3 partitions labeled nicely, but I can't for the life of me find anything to do it for other filesystems.

---

### Post by jw5801 on 2008-05-04
No matter, solved it myself. ReiserFS can be labelled with reiserfstune, FAT32 can be labelled with mlabel (part of the mtools package) and NTFS can be labelled with ntfslabel (part of the ntfsprogs package).

Hopefully that helps anyone else who stumbles to this thread!

---

