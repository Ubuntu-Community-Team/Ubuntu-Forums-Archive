---
title: "Partitions resize"
date: 2014-05-20
forum: General Help
---

### Post by srikanth3 on 2014-05-20
I want to increase the size of my '/' partition size, which indicates that i have low memory and should delete some things before going through with some process. any ideas?

---

### Post by deadflowr on 2014-05-20
Two things.
1) In terms of partitioning, you should do so in a live session, so the partition you want to resize is unmounted.
It's hard to unmount a running partition.

2)Please post 
```
sudo parted -l
```
to see the partition table as is exist now.

And 
```
df -h
```
to see how much space is in use now.

---

### Post by srikanth3 on 2014-05-22
hi, here is the response for the sudo parted -l command:

```
Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  274MB   273MB   fat32           EFI system partition          hidden
 2      274MB   1819MB  1546MB  ntfs            Basic data partition          hidden, diag
 3      1819MB  2092MB  273MB   fat32           EFI system partition          boot
 4      2092MB  2226MB  134MB                   Microsoft reserved partition  msftres
 5      2226MB  88.1GB  85.9GB  ntfs            Basic data partition          msftdata
 6      88.1GB  88.1GB  1049kB                                                bios_grub
12      88.1GB  88.4GB  300MB   ext4
13      88.4GB  95.4GB  7000MB  ext4
14      95.4GB  138GB   42.9GB  ext4
15      138GB   143GB   5000MB  linux-swap(v1)
 7      143GB   144GB   367MB   ntfs                                          hidden, diag
 8      144GB   252GB   108GB   ntfs            Basic data partition          msftdata
 9      252GB   360GB   108GB   ntfs            Basic data partition          msftdata
10      360GB   468GB   108GB   ntfs            Basic data partition          msftdata
11      468GB   500GB   32.4GB  ntfs            Basic data partition          msftdata
```





and the response for ~$ df -h
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda13      6.3G  4.8G  1.2G  81% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           384M  1.4M  382M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  328K  1.9G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sda14       40G  1.5G   36G   4% /home
/dev/sda12      269M   49M  202M  20% /boot
/dev/sda3       252M   50M  203M  20% /boot/efi
```

sorry i couldn't do it earlier, thank you....

---

### Post by oldfred on 2014-05-23
You have to use live installer and load gparted from that. You may also have to right click on swap and unmount that.

While UEFI spec may allow two efi partitions, we have not seen an UEFI that will work with two efi partitions. You show both sda1 & sda3 as efi. And it looks like fstab is mounting sda3 as its efi partition. Does sda1 have Windows efi files, or is it really just a recovery partition? Recovery partitions my have efi files, but are not flagged as efi.

I normally suggest no /boot partition, a / of 20 or 25GB so you have lots of room, but I actually only use 11GB in my / so it does not have to be quite that large. Then rest of space for /home and/or data partition(s).

You do not show much data yet in /home - sda14, so you should be able to shrink it, and move it right. Then you should be able to expand / (root) - sda13.

Do not reinstall Ubuntu without using Something Else or manual install where you create/select manually. Any auto-install option may erase entire drive.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by srikanth3 on 2014-05-25
response to sudo parted -l

```
Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  274MB   273MB   fat32           EFI system partition          hidden
 2      274MB   1819MB  1546MB  ntfs            Basic data partition          hidden, diag
 3      1819MB  2092MB  273MB   fat32           EFI system partition          boot
 4      2092MB  2226MB  134MB                   Microsoft reserved partition  msftres
 5      2226MB  88.1GB  85.9GB  ntfs            Basic data partition          msftdata
 6      88.1GB  88.1GB  1049kB                                                bios_grub
12      88.1GB  88.4GB  300MB   ext4
13      88.4GB  117GB   28.1GB  ext4
14      117GB   133GB   16.9GB  ext4
15      133GB   143GB   9923MB  linux-swap(v1)
 7      143GB   144GB   367MB   ntfs                                          hidden, diag
 8      144GB   252GB   108GB   ntfs            Basic data partition          msftdata
 9      252GB   360GB   108GB   ntfs            Basic data partition          msftdata
10      360GB   468GB   108GB   ntfs            Basic data partition          msftdata
11      468GB   500GB   32.4GB  ntfs            Basic data partition          msftdata
```


response to 
```

~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda13       26G  5.1G   20G  21% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           384M  1.4M  382M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  328K  1.9G   1% /run/shm
none            100M   64K  100M   1% /run/user
/dev/sda12      269M   49M  202M  20% /boot
/dev/sda14       16G  1.1G   14G   8% /home
/dev/sda3       252M   50M  203M  20% /boot/efi
/dev/sda10      101G   74G   27G  74% /media/scofield/EDU
/dev/sda9       101G   87G   14G  87% /media/scofield/ALLOY
/dev/sda8       101G   38G   63G  38% /media/scofield/WISDOM
/dev/sda5        81G   39G   42G  48% /media/scofield/OS
```







do you guys think it's done properly?
i don't seem to have any problem with booting and all but not very sure this is the right way to have it.
thanks for your help...

---

### Post by oldfred on 2014-05-25
Should be ok, It just is your /home where most data will be saved is smaller than your /home. But if you save all your data into the NTFS data partitions you should be ok.

---

### Post by srikanth3 on 2014-05-25
I plan to save most of my data in ntfs drives, so i guess it won't be a problem. Regarding the EFI partitions, does it look ok now?
thanks.

---

### Post by oldfred on 2014-05-25
Did not notice the hidden parameter on your sda1 efi partition. I think that is what some vendors use for recovery or repair boot.

Looks like you should be ok. 

Even my own "optimal" partitioning in a couple of years needs changes, so as you use systems you may find something else is preferred.

---

### Post by srikanth3 on 2014-05-26
Thanks.

---

