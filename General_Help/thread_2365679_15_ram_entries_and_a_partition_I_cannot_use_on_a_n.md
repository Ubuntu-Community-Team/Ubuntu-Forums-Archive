---
title: "15 ram entries and a partition I cannot use on a new Xubuntu only install"
date: 2017-07-09
forum: General Help
---

### Post by makem2 on 2017-07-09
When I installed a fressh Xubuntu I wanted to make a small partition available to Windows. I appear to have mistakenly mounted it at /windows and it does not appear when I view the partitions in File Manager.

How can I gain access? I tried using gparted to change the filetype to ntfs but that messed up everything and it was easier to install Xubuntu again. I thout I was able to make primary partitions which would be available in File Manager.

Is it better/easier to make an extended partition to contain other partitions?

I have never seen so many ran entries when making an install in the past.

```

makem@teclast:~$ sudo fdisk -l
[sudo] password for makem: 
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 05D77963-795A-4483-9D7F-CEF7586BD9F8


Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624  98707455  97656832  46.6G Linux filesystem
/dev/sda3   98707456 390739967 292032512 139.3G Linux filesystem
/dev/sda4  390739968 488396799  97656832  46.6G Microsoft basic data
makem@teclast:~$ 

```

```

makem@teclast:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           387M  6.4M  381M   2% /run
/dev/sda2        46G  4.6G   39G  11% /
tmpfs           1.9G  102M  1.8G   6% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1       511M  4.8M  507M   1% /boot/efi
/dev/sda3       137G   21G  110G  16% /home
/dev/sda4        47G   32K   47G   1% /windows
tmpfs           387M   36K  387M   1% /run/user/1000
makem@teclast:~$ 

```

---

### Post by efflandt on 2017-07-09
Did you try looking in File Manager under **+ Other Locations**? It is probably mounted by its UUID or partition label if it has one, below /media/your_username/

Permissions of directories or files in DOS or Windows formatted partitions are determined by mount options (typically in /etc/fstab if mounted during boot) because Windows file systems have no concept of *nix like file permissions. Note that FAT32 (vfat) is limited to 4 GB maximum file size, but ntfs can handle larger files.

---

### Post by yancek on 2017-07-09
You have GPT partitioning so all partitions are primary and you can't use Extended.  The df -h output you posted shows a 47GB (/dev/sda4) mounted in the root of the filesystem at the mount point /windows so if you use your file manager and navigate to the / of the system where you see the /boot /etc /home directories, windows should be there.  That's based on the info originally posted so if you've made changes, it won't apply.  If you don't see anything in /windows mount point you can try manually mounting it:

```
sudo mount /dev/sda4 /windows
```

---

