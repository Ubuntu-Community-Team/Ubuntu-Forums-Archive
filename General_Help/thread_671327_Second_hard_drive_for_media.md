---
title: "Second hard drive for media"
date: 2008-01-18
forum: General Help
---

### Post by fasthands on 2008-01-18
Hi folks, I have now upgraded my PC I ma running Ubuntu 7.10 GG, I have installed Ubuntu on a 80Gig HDD all has gone well after doing my homework. I have also fitted a 320Gig HDD that I want to use for media storage, I have spent hours going through existing threads on this issue, with no avail. The HDD's are both new, I don't want to install Windows at all!!! I have used the entire disk (80Gig) for the install of Ubuntu, as I said everything is spot on!! I even got my graphics card to work:lolflag: XfX Nvidia 8600GT XXX, but I don't know how to partition the second HDD or what format to use, I have read the Ubuntu book by Kier Thomas from front to back but it keeps referring to Windows :mad:. And is not specific enough on just using another HDD for media storage. Can anyone tell me how to do this? PLEASE!! I have had a look at Gparted before and know roughly how to use it, but I am not sure how to use this to install a second HDD. I want my second HDD to have a little icon on my desktop if possible so I can have easy access to it and just drag and drop images etc, from my removable media, digital camera usb stick for example.I have been trying to find the info out for 3 day's solid now and I am at a dead end and don't want to mess it up!! Please put me out of my misery guy's.

---

### Post by jken146 on 2008-01-18
Hi.  Please post the output of ```
sudo fdisk -l
```

---

### Post by Jolly Roger on 2008-01-18
i don't mean to hijack this thread but i have a similar problem and thought it would be better suited to add to this thread instead of starting a new one. 

i too want to add storage for my media files. but in my case i already have the hard drive installed and certain partitions of it are already in use but the last remaining partition that i have saved for my media won't install correctly. i want to format it to fat32 so that i can access it from windows in case i need to. the problem is that after i've formatted it and then i mount it the partition only has write access as the root user. i can read it as my normal user though. when i try to change the permissions of the partition then i get a message saying that i'm not allowed to. i can write data to the partition when i start nautilus with root privileges but i shouldn't have to use root just to write to my hard drive. 

here is my fdisk:

```

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f47d2b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2556    20531038+   7  HPFS/NTFS
/dev/sda2            2557       20023   140303677+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x033fbefa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2626    21093313+  83  Linux
/dev/sdb2            2627        2755     1036192+  82  Linux swap / Solaris
/dev/sdb3            2756       13261    84389445   83  Linux
/dev/sdb4           13262       30401   137677050    b  W95 FAT32
Note: sector size is 4096 (not 512)

Disk /dev/sdc: 79.8 GB, 79824777216 bytes
26 heads, 50 sectors/track, 14991 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14992    77953628    b  W95 FAT32

```

/dev/sdb4 is  the partition that i am trying to set up. 

here is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=32380540-5992-43ba-9f99-176ea28c9ade /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
/dev/sdb3 /home ext3 nodev,nosuid 0 2
# /dev/sda2
UUID=44E9-E224  /storage        vfat    defaults,utf8,umask=007,gid=46 0       2
# /dev/sda1
UUID=D0AC1327AC13079C /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/sdb2 none            swap    sw              0       0
#UUID=2c0d66d0-97d7-4a89-8888-00db640320bd none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0
#storage drive 2 /dev/sdb4
UUID=4790-E6AF /my_media vfat defaults 0       2

```

the last line "storage drive 2 /dev/sdb4" is the drive i'm trying to get up and running. i'm trying to mount it to the folder "my_media"

---

### Post by jken146 on 2008-01-18
Jolly Roger, what happens if you use the same settings as for your storage partition, i.e. **vfat    defaults,utf8,umask=007,gid=46 0       2** ?

---

### Post by fasthands on 2008-01-18
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007567b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c6a45

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 2063 MB, 2063597056 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         251     2015200    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(249, 254, 63) logical=(250, 225, 38)


I have tried to partition it but I couldn't access the HDD, Have I buggered it up?

---

### Post by jken146 on 2008-01-18
Well, the device is there alright, and it's **sdb**.

The easiest way to partition it is probably with gparted. First, install it:  ```
sudo aptitude install gparted
```
Then run it:  ```
gksudo gparted
```

Choose **sdb** in the menu in the upper right corner of the gparted window.  Then create a new partition that takes up the whole of the drive and format it in **ext3**.

---

### Post by fasthands on 2008-01-18
I have Gparted but I am not sure how to use it, I have tried but I don't know what format I need to use for the partition (s)

---

### Post by fasthands on 2008-01-18
I have done that but I can't mount the hdd, to make it show up!

---

### Post by paul.matthijsse on 2008-01-18
type:
$ mkdir /media/drive2
then:
# sudo mount -t ext3 /dev/sdb media/drive2
and you'll be able to browse your new drive

cheers, Paul.

---

### Post by fasthands on 2008-01-18
I get this after I type the first line:- mkdir /media/drive2
mkdir: cannot create directory `/media/drive2': Permission denied

This may sound stupid but I am still learning! should I press enter when I have typed the first line? if not how do I type the command as you have put it.? sorry.

---

### Post by fasthands on 2008-01-18
I have managed to mount the hard drive by reboot, but I now cant change the permissions to read and write, so it wont let me put anything into it.

---

### Post by Sidewinder1 on 2008-01-18
Try this: open your terminal and if your username is fasthands type
sudo chown -R fasthands:fasthands drive2
This should change the owner of drive2 from root to fasthands
HTH

---

### Post by wolfen69 on 2008-01-18
you needed to do sudo mkdir /media/drive2

---

### Post by Sidewinder1 on 2008-01-18
If the above doesn't work, try:
sudo chown -R fasthands:fasthands /media/drive2
I'm a "noob" and trying my best to learn. I just hooked up an external hard drive and  the above changed ownership from root to me :-)

---

### Post by fasthands on 2008-01-19
Right folks I have mounted the hard drive but I can't access it, it is read only and I can't change the permissions now as the owner is root! I have tried,   sudo chown -R username /media/sdb1    But no joy! how can I make it read and write? so I can put my media onto it. Or as attempted make me the user owner. I have managed to get everything working spot on I just have this last step to sort out now.:confused::confused:

---

### Post by fasthands on 2008-01-19
Tried this!! fasthands@fasthands-desktop:~$ sudo chown -R fasthands:fasthands drive2
chown: cannot access `drive2': No such file or directory
fasthands@fasthands-desktop:~$

---

### Post by fasthands on 2008-01-19
When I click on properties of the HDD in the basic tab it say the name of the drive is,   

298.1 GB volume: disk

So I repeated the command line,  sudo chown -R fasthands:fasthands /media/298.1 GB volume: disk

Still no joy!!    AAAAAAAAAAAAARRRRRRRRRRRRRRGGGGGGGGGGGGHHHHHHHHHHH!!!!!!!!

---

### Post by Sidewinder1 on 2008-01-19
Frustrating isn't it; I had the same problem. I think, if I remember correctly there were two issues: the exact name of the drive and weather the chown command was issued when the drive was mounted or ummounted. In your post above, you didn't say weather you tried the command with /media. I believe my first advice was wrong without the /media within the command. At this point all I can recommend is to try the following under both mounted and unmounted conditions:
sudo chown -R fasthands:fasthands /media/drive2

---

### Post by fasthands on 2008-01-19
fasthands@fasthands-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007567b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c6a45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

---

### Post by Jolly Roger on 2008-01-21
it seems i have fixed my own problem. this is how i did it:

1. unmount the drive
2. change the permissions on the folder that you want to mount the drive to so that you have access to read and write in that folder
3. mount the drive in the folder

fasthands that may work for you.

---

