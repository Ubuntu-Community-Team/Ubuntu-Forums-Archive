---
title: "Problem mounting exfat sd card"
date: 2019-04-07
forum: General Help
---

### Post by saurian2 on 2019-04-07
Hello everyone,

I bought a 64GB card from Kingstone and I have issues with mounting it on Ubuntu 16.04. So when I put the card in my laptop I got the error from here [https://itsfoss.com/mount-exfat/](https://itsfoss.com/mount-exfat/) and tried to follow the steps there. Nothing happened so I was thinking to check if Ubuntu can see my card and I got:
```
sorin@sorin-K54C:~$ lsusb
Bus 002 Device 003: ID 09da:90a0 A4Tech Co., Ltd. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 003: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sorin@sorin-K54C:~$ 
sorin@sorin-K54C:~$ sudo parted -ls
Model: ATA WDC WD3200BPVT-8 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  85.9GB  85.9GB  primary   ntfs            boot
 2      85.9GB  172GB   85.9GB  primary   ntfs
 4      172GB   235GB   63.1GB  extended
 6      172GB   224GB   52.4GB  logical   ext4
 5      224GB   235GB   10.6GB  logical   linux-swap(v1)
 3      235GB   320GB   85.2GB  primary   ntfs


Model: Multiple Card Reader (scsi)
Disk /dev/sdb: 62.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      16.8MB  62.2GB  62.2GB  primary


sorin@sorin-K54C:~$ 
sorin@sorin-K54C:~$ sudo lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE
MODEL            NAME   FSTYPE LABEL      MOUNTPOINT                SIZE
WDC WD3200BPVT-8 sda                                              298.1G
                 &#9500;&#9472;sda1 ntfs   Religioase /media/sorin/Religioase    80G
                 &#9500;&#9472;sda2 ntfs   Studiu     /media/sorin/Studiu        80G
                 &#9500;&#9472;sda3 ntfs   Sorin      /media/sorin/Sorin       79.4G
                 &#9500;&#9472;sda4                                               1K
                 &#9500;&#9472;sda5 swap              [SWAP]                    9.9G
                 &#9492;&#9472;sda6 ext4   Boot       /                        48.8G
Card  Reader     sdb                                                 58G
                 &#9492;&#9472;sdb1                                            57.9G
CDDVDW TS-L633A  sr0                                               1024M
```
So I tried to mount my sd card manually:
```
sorin@sorin-K54C:~$ sudo mount -t exfat /dev/sdb1 /media/sorin/sdcard
FUSE exfat 1.2.3
ERROR: exFAT file system is not found.
```
I found a link somewhere about some kind of issue as mine at that it was fixed on exfat 1.2.8 so I installed *exfat-fuse* and *exfat-utils* for that version but I got the same error.

Any ideas what else can I try? Thanks in advance.

---

### Post by sudodus on 2019-04-08
Have you tried, if your SD card works

- in another computer,
- with an[other] USB adapter,
- with another operating system?

The following links may help analyzing the problem, and if you are lucky, solve it,

[Analysis of the problem - and tips how to solve the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

[(Scroll down to) More about exFAT](https://askubuntu.com/questions/952673/how-do-i-copy-a-file-larger-than-4gb-to-a-usb-flash-drive/952706#952706)

---

### Post by saurian2 on 2019-04-08
Hey,

Thanks for your reply. I actually tried on an Windows  machine and, sadly, I formatted the card as NTFS. I sad "sadly" because  now I'll probably never find out why I had that issue on Ubuntu. :razz:

---

### Post by sudodus on 2019-04-08
Does you card work with Ubuntu now?

In that case fine, you need not worry about the reason for your problem with exfat :-)

[hr][/hr]
If you want to investigate it anyway, you can create an exfat file system (using Windows or Ubuntu) and check if it will work both in Windows and Ubuntu.

---

