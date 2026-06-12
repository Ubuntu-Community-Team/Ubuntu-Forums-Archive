---
title: "Can't deterministically boot into OS"
date: 2020-05-30
forum: General Help
---

### Post by arapollo on 2020-05-30
Two months or so ago I ran out of disk space on my hard drive and cloned Ubuntu to another one in the same box. When doing this I updated the UUIDs. Something strange started happening. Sometimes it would boot into the other older Ubuntu and then sometimes boots into the new one. As a short term fix I changed the desktop background to know what snapshot I am in. I tried deleting the partition and that didn't help. I've tried using bootrepair and that didn't work either. Now I always boot into the old harddrive. It seems like the boot is pointing to two different snapshots and one randomly wins. This is frustrating because sometimes I have to keep rebooting to into the right snapshot and this isn't good because now I may have lost some work. I've tried googling around but I can't really figure out why this is happening. Any help would be appreciated.

---

### Post by VMC on 2020-05-30
snapshot. Does that mean your using BTRFS?
```
lsblk -f
``` would help to see your partitions.

---

### Post by arapollo on 2020-05-30
I don't think I am using BTRFS. I meant snapshot like it seems like the snapshot from the day I cloned the drive. I can still download files and use it from that point onward. The other OS I boot into is also valid. Note I do have a Ubuntu USB drive plugged in too right to help debug this issue.

Here is lsblk -f

NAME  FSTYPE LABEL               UUID                                 MOUNTPOINT
loop0 squash                                                          /snap/data
loop1 squash                                                          /snap/inte
loop2 squash                                                          /snap/core
loop3 squash                                                          /snap/ruby
loop4 squash                                                          /snap/core
loop5 squash                                                          /snap/data
loop6 squash                                                          /snap/ruby
loop7 squash                                                          /snap/inte
sda                                                                   
&#9500;&#9472;sda1
&#9474;     ntfs   Recovery            161602EC1602CCA5                     
&#9500;&#9472;sda2
&#9474;     vfat                       4C02-F1F8                            
&#9500;&#9472;sda3
&#9474;                                                                     
&#9500;&#9472;sda4
&#9474;     ntfs   ubuntu              80168FCD168FC320                     
&#9500;&#9472;sda5
&#9474;     ntfs                       EEBE68DDBE68A037                     
&#9500;&#9472;sda6
&#9474;     ext4                       2d602a1d-3491-4543-8243-58a6e8b51402 /
&#9492;&#9472;sda7
      ext4                       f644834e-2d21-4a2d-8e1e-0033b425610b /home
sdb   iso966 Ubuntu 18.04.4 LTS amd64
&#9474;                                2020-02-03-18-40-13-00               
&#9500;&#9472;sdb1
&#9474;     iso966 Ubuntu 18.04.4 LTS amd64
&#9474;                                2020-02-03-18-40-13-00               /media/ara
&#9492;&#9472;sdb2
      vfat   Ubuntu 18.04.4 LTS amd64
                                 D055-8513                            
nvme0n1
&#9474;                                                                     
&#9500;&#9472;nvme0n1p1
&#9474;     ntfs   Recovery            161602EC1602CCA5                     
&#9500;&#9472;nvme0n1p2
&#9474;     vfat                       4C02-F1F8                            /boot/efi
&#9500;&#9472;nvme0n1p3
&#9474;                                                                     
&#9500;&#9472;nvme0n1p4
&#9474;     ntfs                       EEBE68DDBE68A037                     
&#9492;&#9472;nvme0n1p5
      ntfs                       AA5203DA5203A9E1

---

### Post by VMC on 2020-05-30
Could you copy&paste into CODE tags please. Like this ```
NAME        FSTYPE FSVER LABEL   UUID                                 FSAVAIL FSUSE% MOUNTPOINT
sda                                                                                  
&#9492;&#9472;sda1      ntfs         xSSD    41B523622A4A8924                                    
sdb         vfat   FAT32 safe    E7F7-DA2B                                           
sr0                                                                                  
nvme0n1                                                                              
&#9500;&#9472;nvme0n1p1 vfat   FAT32         06F2-A932                              59.1M    38% /boot/efi
&#9500;&#9472;nvme0n1p2 ntfs         Windows 303E9A203E99DEE2                                    
&#9500;&#9472;nvme0n1p3 swap   1             f4ccc655-f7ba-44b5-b636-88a3cfd42b81                [SWAP]
&#9500;&#9472;nvme0n1p4 ext4   1.0   neon    08f6cbed-48d0-44e7-b182-7ab2752d483d                
&#9500;&#9472;nvme0n1p5 ext4   1.0   xfce    84795b70-6c30-423b-95d7-8eae0f3840f2   32.7G    14% /
&#9492;&#9472;nvme0n1p6 ext4   1.0   lxqt    075d6c52-5b58-40dc-ad35-95af843769c0
```

Why installed into NTFS?

---

### Post by arapollo on 2020-05-31
Hi VMC,

I'm not sure why it is in NTFS.

```

NAME  FSTYPE LABEL               UUID                                 MOUNTPOINT
loop0 squash                                                          /snap/ruby
loop1 squash                                                          /snap/core
loop2 squash                                                          /snap/data
loop3 squash                                                          /snap/ruby
loop4 squash                                                          /snap/core
loop5 squash                                                          /snap/inte
loop6 squash                                                          /snap/data
loop7 squash                                                          /snap/inte
sda                                                                   
&#9500;&#9472;sda1
&#9474;     ntfs   Recovery            161602EC1602CCA5                     
&#9500;&#9472;sda2
&#9474;     vfat                       4C02-F1F8                            
&#9500;&#9472;sda3
&#9474;                                                                     
&#9500;&#9472;sda4
&#9474;     ntfs   ubuntu              80168FCD168FC320                     
&#9500;&#9472;sda5
&#9474;     ntfs                       EEBE68DDBE68A037                     
&#9500;&#9472;sda6
&#9474;     ext4                       2d602a1d-3491-4543-8243-58a6e8b51402 /
&#9492;&#9472;sda7
      ext4                       f644834e-2d21-4a2d-8e1e-0033b425610b /home
sdb   iso966 Ubuntu 18.04.4 LTS amd64
&#9474;                                2020-02-03-18-40-13-00               
&#9500;&#9472;sdb1
&#9474;     iso966 Ubuntu 18.04.4 LTS amd64
&#9474;                                2020-02-03-18-40-13-00               /media/arl
&#9492;&#9472;sdb2
      vfat   Ubuntu 18.04.4 LTS amd64
                                 D055-8513                            
nvme0n1
&#9474;                                                                     
&#9500;&#9472;nvme0n1p1
&#9474;     ntfs   Recovery            161602EC1602CCA5                     
&#9500;&#9472;nvme0n1p2
&#9474;     vfat                       4C02-F1F8                            /boot/efi
&#9500;&#9472;nvme0n1p3
&#9474;                                                                     
&#9500;&#9472;nvme0n1p4
&#9474;     ntfs                       EEBE68DDBE68A037                     
&#9492;&#9472;nvme0n1p5
      ntfs                       AA5203DA5203A9E1                     


```

Another update that is that I used to sometimes boot into the other version, but my last 10 boots I've only booted into the system right before I cloned it. I'm guessing the other newer system I was working on or whatever is forever gone.

---

### Post by oldfred on 2020-05-31
You have duplicate UUID & maybe duplicate GUIDs.
You cannot use clone and keep original drive installed without reformatting or at least resetting all UUIDs & GUIDs.

You may be booting into one install one time and into the other next time & then they can get out of sync. It just depends on what system sees at time you boot.

If you unplug or turn off in UEFI, your sda, it may just work.

---

