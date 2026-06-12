---
title: "Need help with partitions- GParted not showing any free space"
date: 2015-07-31
forum: General Help
---

### Post by todd16 on 2015-07-31
Hi, I'm using Ubuntu Studio which I installed from a live dvd, and I used Linux Lite before that. Right now I'm trying out KXStudio
to try and fix my partition problem. I know I have approx. 30 gigabytes or more of free space on my HD but gparted is not showing it.
I'd like to create another partition. please help. Here is a screen shot of gparted:

[IMG][[IMG]http://i153.photobucket.com/albums/s208/todddean/mmmmmmmmmmmmmm/snapshot1_zpsvcbeebj0.png[/IMG]]("http://s153.photobucket.com/user/todddean/media/mmmmmmmmmmmmmm/snapshot1_zpsvcbeebj0.png.html")[/IMG]

---

### Post by nerdtron on 2015-07-31
Where is the screenshot?

Also the output of the following commands will be helpful:
```
 sudo parted -l
sudo fdisk -l
lsblk
df -Th

```

---

### Post by ajgreeny on 2015-07-31
Your screenshot is not showing. Try it again please by using the edit post button, 
Go Advanced, click on the paperclip icon and follow the instructions to browse to the image and then upload it. That will add a thumbnail in your post that points to the uploaded image.

---

### Post by todd16 on 2015-07-31
here is the output for those commands:

```
kxstudio@kxstudio:~$ sudo parted -l
Model: ATA FUJITSU MHV2080A (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   80.0GB  79.8GB  extended
 5      257MB   80.0GB  79.8GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--studio--vg-swap_1: 2147MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  2147MB  2147MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--studio--vg-root: 77.6GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  77.6GB  77.6GB  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
``` 
```

kxstudio@kxstudio:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b9c21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   156301311    77899777    5  Extended
/dev/sda5          501760   156301311    77899776   8e  Linux LVM

Disk /dev/mapper/ubuntu--studio--vg-root: 77.6 GB, 77619789824 bytes
255 heads, 63 sectors/track, 9436 cylinders, total 151601152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--studio--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--studio--vg-swap_1: 2147 MB, 2147483648 bytes
255 heads, 63 sectors/track, 261 cylinders, total 4194304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--studio--vg-swap_1 doesn't contain a valid partition table
``````

kxstudio@kxstudio:~$ lsblk
NAME                                 MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                                    8:0    0  74.5G  0 disk 
&#9500;&#9472;sda1                                 8:1    0   243M  0 part 
&#9500;&#9472;sda2                                 8:2    0     1K  0 part 
&#9492;&#9472;sda5                                 8:5    0  74.3G  0 part 
  &#9500;&#9472;ubuntu--studio--vg-root (dm-0)   252:0    0  72.3G  0 lvm  
  &#9492;&#9472;ubuntu--studio--vg-swap_1 (dm-1) 252:1    0     2G  0 lvm  
sr0                                   11:0    1   1.5G  0 rom  /cdrom
loop0                                  7:0    0   1.4G  1 loop /rofs
kxstudio@kxstudio:~$ df -Th
Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs 1008M  578M  431M  58% /
udev           devtmpfs   998M  8.0K  998M   1% /dev
tmpfs          tmpfs      202M  1.1M  201M   1% /run
/dev/sr0       iso9660    1.5G  1.5G     0 100% /cdrom
/dev/loop0     squashfs   1.5G  1.5G     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     1008M  1.3M 1007M   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs     1008M  152K 1008M   1% /run/shm
none           tmpfs      100M  4.0K  100M   1% /run/user
kxstudio@kxstudio:~$
```

---

### Post by Bucky Ball on 2015-07-31
You appear to have installed UStudio on sda5 as an encrypted partition. That can cause Gparted issues. You also have no /swap.

Personally, I'd go back to square one and do a standard install, no encryped partition. Easier. Also, is there any particular reason you went for Ubuntu Studio? No problem with it, it's great, but it has a LOT of stuff you definitely don't need if you are not intending audio/video/multimedia editing on a serious to pro level. You can always install the bits of it you need later if and as required.

Good luck. ;)

---

### Post by coffeecat on 2015-07-31
You have an LVM volume which gparted cannot manage. My guess is your 30GB free space is within the LVM. Was there a reason you chose LVM when you installed Ubuntu Studio? Please be aware that along with LVM you have an undersized /boot partition which will quickly fill up with kernels unless you clean the old ones out. That's not your mistake, but an inadequacy of the installer which creates an approximately 250 MB sized boot partition - too small - when you choose LVM or whole disc encrypted installation, which requires LVM.

LVM probably adds a degree of complexity which you don't need, but in order to be able to manage it, you may find this article useful:

[http://www.howtogeek.com/211937/how-to-use-lvm-on-ubuntu-for-easy-partition-resizing-and-snapshots/](http://www.howtogeek.com/211937/how-to-use-lvm-on-ubuntu-for-easy-partition-resizing-and-snapshots/)

If you wish to use the Ubuntu Disks utility, you will need to use the Ubuntu live CD rather than KXStudio which few, if any, members here will know much about. You may be able to manage your LVM from within Ubuntu Studio if you install the correct tools, but you will need someone with more experience of LVM to guide you.

By the way, I've added BBCode code tags to your post in order to restore readability and formatting of the terminal output. Please use the # icon in the message toolbar to add code tags when posting terminal output.

---

### Post by nerdtron on 2015-07-31
This is an LVM partition and  you'll see if you have free space using the following commands.
```
sudo vgdisplay
sudo lvdisplay
```

And if you do have free space, you may need to shrink the current filessystem which does not support online reduction of filessystem. Either you boot into the LIVE mode and you perform the LVM tasks from the command line or you start from scratch again and carefully declare your final partitioning on reinstallation.

---

### Post by todd16 on 2015-07-31
Thanks for the help you guys. I'm going to start from square one. Btw, Im using ubuntu studio because I am a musician ready to record songs ive written....
I'm just very green when it comes to linux and to partitioning period! But I'm so glad I'm using linux now. It has changed my world. Thanks again!

---

### Post by Bucky Ball on 2015-07-31
All good. Mark this thread as solved if your original question is answered and post a new one with a descriptive title if you hit any brickwalls during/after install. See the first link in my signature (this will not close the thread for further discussion).

---

