---
title: "qbittorrent and external drive problem"
date: 2017-04-20
forum: General Help
---

### Post by makem2 on 2017-04-20
I have attached a USB SSD drive and set qbittorrent downloads to a directory 'Torrents' on that drive. The drive mount point is /media/usb1

When I start qbittorrent it immediately crashes and the only way to recover is to restart the computer.

qbittorrent works correctly if the downloads are set to a directory on an internal drive partition.

These are the settings which cause the program to crash. I would appreciate assistance as I have spent so long trying to rectify this that I think I can no longer see the wood for the trees and am probably missing something obvious.

UUID:
```

/dev/sdc1: UUID="a251d4c3-7ede-415f-a17b-4524a2b4a87e" TYPE="ext4" PARTUUID="0005b28a-01"

```
fstab entry:
```

UUID=a251d4c3-7ede-415f-a17b-4524a2b4a87e /media/usb1 ext4 noatime 0 2

```
Permissions:
```

makem@ssdTOSH:/media$ ls -la
total 16
drwxr-xr-x  5 root  root  4096 Apr 20 23:23 .
drwxr-xr-x 27 root  root  4096 Apr  7 10:41 ..
drwxrwxrwx  1 root  root  4096 Apr 20 23:01 makem
drwxrwxrwt  3 root  root    80 Apr 21 00:31 ramdisk
drwxr-xr-x  5 makem makem 4096 Apr 21 00:18 usb1

makem@ssdTOSH:~$ cd /media/usb1
makem@ssdTOSH:/media/usb1$ ls -la

total 32
drwxr-xr-x 5 makem makem  4096 Apr 21 00:18 .
drwxr-xr-x 5 root  root   4096 Apr 20 23:23 ..
drwx------ 2 root  root  16384 Apr 20 13:27 lost+found
drwxrwxr-x 6 makem makem  4096 Apr 20 16:09 Torrents
drwx------ 4 makem makem  4096 Apr 20 15:37 .Trash-1000
makem@ssdTOSH:/media/usb1$


```

---

