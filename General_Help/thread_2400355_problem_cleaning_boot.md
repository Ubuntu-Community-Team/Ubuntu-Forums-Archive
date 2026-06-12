---
title: "problem cleaning /boot"
date: 2018-09-05
forum: General Help
---

### Post by thom35 on 2018-09-05
Hello,
I've been using Ubuntu already some years but I still have not much 'technical' knowledge, so to speak.
While trying to install updates or to upgrade from Ubuntu 16.04 to 18.04 I get a message saying there is not enough free space on my /boot.
I tried removing old kernels both using apt autoremove and manually using
```

sudo dpkg -P linux-image-x-generic

```
as suggested here: [https://ubuntuforums.org/showthread.php?t=2357793](https://ubuntuforums.org/showthread.php?t=2357793)


Unfortunately, this has no result so far.
Some output of commands that may be useful:

```

$ uname -r
4.4.0-131-generic

```

```

$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         1,7G     0  1,7G   0% /dev
tmpfs                        342M  5,9M  337M   2% /run
/dev/mapper/ubuntu--vg-root   55G   43G   11G  81% /
tmpfs                        1,7G   26M  1,7G   2% /dev/shm
tmpfs                        5,0M  4,0K  5,0M   1% /run/lock
tmpfs                        1,7G     0  1,7G   0% /sys/fs/cgroup
/dev/sda1                    228M  156M   61M  72% /boot
/dev/sdb2                    437G  165G  250G  40% /media/mynewdrive2
/dev/sdb1                    481G  316G  141G  70% /media/mynewdrive1
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        342M  112K  342M   1% /run/user/1000

```


```

$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
udev                          431338    504   430834    1% /dev
tmpfs                         437536    773   436763    1% /run
/dev/mapper/ubuntu--vg-root  3670016 674292  2995724   19% /
tmpfs                         437536     45   437491    1% /dev/shm
tmpfs                         437536      7   437529    1% /run/lock
tmpfs                         437536     18   437518    1% /sys/fs/cgroup
/dev/sda1                     124496    334   124162    1% /boot
/dev/sdb2                   29048832   3981 29044851    1% /media/mynewdrive2
/dev/sdb1                   32006144 175074 31831070    1% /media/mynewdrive1
cgmfs                         437536     14   437522    1% /run/cgmanager/fs
tmpfs                         437536     44   437492    1% /run/user/1000

```



```

$ dpkg -l | grep linux
ii  console-setup-linux                           1.108ubuntu15.4                              all          Linux specific part of console-setup
ii  extlinux                                      3:6.03+dfsg-11ubuntu1                        amd64        collection of bootloaders (Linux ext2/ext3/ext4, btrfs, and xfs bootloader)
ii  libselinux1:amd64                             2.4-3build2                                  amd64        SELinux runtime shared libraries
ii  libselinux1:i386                              2.4-3build2                                  i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                1.10.0-1                                     amd64        Collection of video4linux support libraries
ii  libv4l-0:i386                                 1.10.0-1                                     i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                          1.10.0-1                                     amd64        Video4linux frame format conversion library
ii  libv4lconvert0:i386                           1.10.0-1                                     i386         Video4linux frame format conversion library
ii  linux-base                                    4.5ubuntu1~16.04.1                           all          Linux image base package
ii  linux-firmware                                1.157.20                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                 4.4.0.131.137                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-130                       4.4.0-130.156                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-130-generic               4.4.0-130.156                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-131                       4.4.0-131.157                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-131-generic               4.4.0-131.157                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.4.0.131.137                                amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-130-generic                 4.4.0-130.156                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-131-generic                 4.4.0-131.157                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-130-generic           4.4.0-130.156                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-131-generic           4.4.0-131.157                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.4.0.131.137                                amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          4.4.0-134.160                                amd64        Linux Kernel Headers for development
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
rc  playonlinux                                   4.2.1                                        all          This program is a front-end for wine.
ii  pptp-linux                                    1.8.0-1                                      amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                      3:6.03+dfsg-11ubuntu1                        amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                               3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies
rc  syslinux-themes-debian                        12-4                                         all          collection of boot loaders (theme metapackage)
rc  syslinux-themes-debian-wheezy                 12-4                                         all          collection of boot loaders (debian-wheezy theme)
ii  util-linux                                    2.27.1-6ubuntu3.6                            amd64        miscellaneous system utilities

```

```

$ sudo parted -l
[sudo] password for thom: 
Model: ATA ADATA SX900 (scsi)
Disk /dev/sda: 64,0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   64,0GB  63,8GB  extended
 5      257MB   64,0GB  63,8GB  logical                lvm


Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size   Type     File system  Flags
 1      1049kB  524GB   524GB  primary  ext4
 2      524GB   1000GB  476GB  primary  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 3729MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0,00B  3729MB  3729MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 60,0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0,00B  60,0GB  60,0GB  ext4

```

---

### Post by Dennis N on 2018-09-05
You can use Synaptic Package Manager to easily remove unwanted kernels. See attached image using 4.4 kernel.
1) To remove 4.4 kernel packages, search in Synaptic for 4.4.0 
2) Further group the results by kernel number by clicking on "Installed Version" column heading. 
3) Select all items with same installed version. See screenshot with all 4.4.0.130 kernel packages selected. There are five such packages on the system, but could be fewer.
4) Right-click on these selected items, and mark for complete removal.
5) Click Apply in tool bar.

You can remove more than one kernel at a time if you want by selecting additional packages in step 3.

---

### Post by Impavidus on 2018-09-05
When you autoremove old kernels, two kernels are kept: the most recent one and one older kernel, just in case there's a problem with the latest. As you're running 4.4.0-131, you could use apt-get or synaptic or whatever you prefer to remove kernel 4.4.0-130, wich may free just enough space. You may have to repeat that trick on 18.04 before every kernel upgrade.

Your /boot partition is a bit too small. It's best to make it about half a gigabyte, so it can hold a number of kernels. Maybe a bit more, to be futureproof. You're not going to notice half a gigabyte of wasted disk space on a 64GB disk. But changing it won't be easy, as you'll have to shrink your lvm partition.

---

### Post by thom35 on 2018-09-06
Thanks for your reply! I removed the 4.4.0.130 kernel using Synaptic Package Manager. Then after upgrading to 4.4.134 I removed the 4.4.131 kernel as well.
I previously removed the older kernels by hand using the dpkg -P command since autoremove didn't do the job. I didn't dare to remove the 4.4.0.130 but apparently it's not a big problem to remove that kernel as well. 
I might consider a reinstall sometime to solve the space problem of my /boot partition.
Anyway, thank you very much for your help!

---

