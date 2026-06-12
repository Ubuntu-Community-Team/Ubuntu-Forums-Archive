---
title: "Mounting Windows Drive on Gusty"
date: 2008-01-12
forum: General Help
---

### Post by HoodRabbit on 2008-01-12
Hey everyone, I'm a little new to Linux and just installed Gusty Gibbon but my problem is difficult. I have this hdd that was a slave from my old windows machine. Every time I try to mount it this appears "hal-storage-fixed-mount-all-options refused uid 1000". I want to mount it an access the files but I seem to have some trouble. If anyone could help i'd appreciate it.


-Thanks

---

### Post by taurus on 2008-01-12
See if you can mount it by hand from a terminal?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by HoodRabbit on 2008-01-12
fdisk (util-linux-ng 2.13)
zero@Knine:~$ sudo fdisk -l
[sudo] password for zero:

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000050a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4661    37439451   83  Linux
/dev/sda2            4662        4866     1646662+   5  Extended
/dev/sda5            4662        4866     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00e2c74f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    7  HPFS/NTFS

---

### Post by taurus on 2008-01-12
Try something like

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```

---

### Post by HoodRabbit on 2008-01-12
Eh...

zero@Knine:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0

---

### Post by rivalarrival on 2008-01-12
Hood, 

Fairly common problem. These two links should help you out:

[http://ubuntuforums.org/showthread.php?t=647024](http://ubuntuforums.org/showthread.php?t=647024)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Windows](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Windows)

---

### Post by taurus on 2008-01-12
Use the force option to mount it then.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
ls -la /media/sdb1
```

---

### Post by HoodRabbit on 2008-01-12
Haha silly me. Thank you for your help my friend.

---

