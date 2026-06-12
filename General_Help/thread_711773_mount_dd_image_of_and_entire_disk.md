---
title: "mount dd image of and entire disk"
date: 2008-03-01
forum: General Help
---

### Post by TheCowGod on 2008-03-01
My grandmas computer crashed and I offered to fix it. It ended up being a borked disk drive, she wants me to see if I can get the files off of it. I used ddrescue if=/dev/sda of=/mnt/storage/diskimage to image the entire drive. Now I need to figure out how to mount the image so I can retrieve the files.
When I try to mount the image I get this error
```

[cowgod@ubuntu /mnt/storage]$ sudo mount -o loop -t ntfs ./disk_image2 /home/cowgod/Desktop/drive_image/
./disk_image2: No such file or directory

```

the output from fdisk -l shows that there are two partitions in the image, but I cannot figure out how to mount the one i need.
```

[cowgod@ubuntu /mnt/storage]$ fdisk -l disk_image 
You must set cylinders.
You can do this from the extra functions menu.

Disk disk_image: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41172ba5

     Device Boot      Start         End      Blocks   Id  System
disk_image1               1           4       32098+  de  Dell Utility
disk_image2   *           5        4862    39021885    7  HPFS/NTFS
Partition 2 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(4861, 254, 63)

```

Any help is appreciated.
Thanks, John

---

### Post by TheCowGod on 2008-03-01
Ok i figured it out. You need to do a fdisk -u -l ./disk_image
.
```
[cowgod@ubuntu ~]$ fdisk -u -l /mnt/storage/disk_image 
You must set cylinders.
You can do this from the extra functions menu.

Disk /mnt/storage/disk_image: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41172ba5

                  Device Boot      Start         End      Blocks   Id  System
/mnt/storage/disk_image1              63       64259       32098+  de  Dell Utility
/mnt/storage/disk_image2   *       64260    78108029    39021885    7  HPFS/NTFS
Partition 2 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(4861, 254, 63)

```

then take the start of the partition that you want to edit 64260 in this case and multiply it by 512 ie 512*64260=32901120

then mount like this:
```
[cowgod@ubuntu ~]$ sudo mount -o loop,offset=32901120 -t auto /mnt/storage/disk_image /home/cowgod/Desktop/drive_image

```

Hope this helps someone!

---

