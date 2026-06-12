---
title: "Using AIr: no space left on device"
date: 2024-04-03
forum: General Help
---

### Post by PigFox on 2024-04-03
My Ubuntu version is 22.04.4 LTS and I have not noticed any other issues with my machine,

I have been using AIr hot reload for my Go development but now I am getting an  error:
$ air *.go
  __    _   ___  
 / /\  | | | |_) 
/_/--\ |_| |_| \_ 1.51.0, built with Go 1.22.0

failed to watch /home/user/Documents/project1, error: **no space left on device**


$ df -i
Filesystem                    Inodes   IUsed      IFree IUse% Mounted on
tmpfs                        4078939    1902    4077037    1% /run
/dev/mapper/vgubuntu-root   60858368 2014874   58843494    4% /
tmpfs                        4078939    1481    4077458    1% /dev/shm
tmpfs                        4078939       7    4078932    1% /run/lock
efivarfs                           0       0          0     - /sys/firmware/efi/efivars
/dev/nvme0n1p2                 93888     322      93566    1% /boot
/dev/nvme0n1p1                     0       0          0     - /boot/efi
tmpfs                         815787     230     815557    1% /run/user/1000
/dev/sdb1                 8228485964  706000 8227779964    1% /media/peter/Elements
/dev/sda1                          0       0          0     - /media/peter/Seagate Backup Plus Drive

$ sudo apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

$ df -i
Filesystem                    Inodes   IUsed      IFree IUse% Mounted on
tmpfs                        4078939    1902    4077037    1% /run
/dev/mapper/vgubuntu-root   60858368 2014917   58843451    4% /
tmpfs                        4078939    1428    4077511    1% /dev/shm
tmpfs                        4078939       7    4078932    1% /run/lock
efivarfs                           0       0          0     - /sys/firmware/efi/efivars
/dev/nvme0n1p2                 93888     322      93566    1% /boot
/dev/nvme0n1p1                     0       0          0     - /boot/efi
tmpfs                         815787     230     815557    1% /run/user/1000
/dev/sdb1                 8228485964  706000 8227779964    1% /media/peter/Elements
/dev/sda1                          0       0          0     - /media/peter/Seagate Backup Plus Drive

Any ideas how to fix this?

---

### Post by Impavidus on 2024-04-04
Could you show the output of ```
df -h
```too? df -i only shows the inodes. You haven't reached the limit on the number of files, but may have reached the limit on total file size.

---

