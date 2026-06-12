---
title: "ddrescue-image from failing failing hdd is not working ("
date: 2015-07-01
forum: General Help
---

### Post by sibu4 on 2015-07-01
Hey people,
When I try to mount the image from the failing hdd made with ddrescue, I get the following message:


```
 Error mounting /dev/loop0 at  /media/xy/2e50c2b4-0fe9-4a44-9dbd-28325a39da4a: Command-line `mount -t  "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/loop0"  "/media/xy/2e50c2b4-0fe9-4a44-9dbd-28325a39da4a"' exited with non-zero  exit status 32: mount: /dev/loop0 is write-protected, mounting read-only
 mount: wrong fs type, bad option, bad superblock on /dev/loop0,
     missing codepage or helper program, or other error
    In some cases useful info is found in syslog - try
     dmesg | tail or so.
```

```


Rechnerxy:~$        dmesg | tail 
[83297.472971] blk_update_request: critical medium error, dev sdc, sector 69141760
[83297.472977] Buffer I/O error on dev sdc3, logical block 834720, async page read
[83389.076895] sd 7:0:0:0: [sdc] Synchronizing SCSI cache
[83389.100017] usb 4-1.1: USB disconnect, device number 6
[87607.695839] EXT4-fs (loop0): bad geometry: block count 25600000 exceeds size of device (25599985 blocks)

```

Fsck din't work as well
```

 Rechnerxy:~$ sudo fsck -y /dev/sdb2/image.img
fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
fsck.ext2: Not a directory beim Versuch, /dev/sdb2/image.img zu öffnen
Der Superblock ist unlesbar bzw. beschreibt kein gültiges ext2/ext3/ext4-
Dateisystem. Wenn das Gerät gültig ist und ein ext2/ext3/ext4-
 Dateisystem (kein swap oder ufs usw.) enthält, dann ist der Superblock
beschädigt, und Sie könnten versuchen, e2fsck mit einem anderen Superblock
 zu starten:
     e2fsck -b 8193 <Gerät>
 oder
  e2fsck -b 32768 <Gerät>

```


Here I attached the results from ddrescue - I interrupted at this point, because the hdd was making weird noises all the time, and there haven't been progress for 5 hours (but I think I could resume it, because of log file):

> rescued:    78986 MB,  errsize:    963 MB,  current rate:        0 B/s
>    ipos:     3419 MB,   errors:   11254,    average rate:     995 kB/s
>    opos:     3419 MB, run time:   22.04 h,  successful read:    5.12 h ago
> Copying non-tried blocks... Pass 3 (forwards)
> Interrupted by user[B]


If anybody has an advise, about how to proceed, I would be glad.[/B]

---

### Post by tgalati4 on 2015-07-01
Welcome to the forums.  Can you describe the noise that the disk is making?  You can do a web search on "failing hard disk noises" to get samples of the noise and see what it is similar to.  What are the SMART parameters of the disk drive?

It's possible that ddrescue failed to create a working image.  There are a few versions of ddrescue:  [http://askubuntu.com/questions/211578/whats-the-difference-between-ddrescue-gddrescue-and-dd-rescue](http://askubuntu.com/questions/211578/whats-the-difference-between-ddrescue-gddrescue-and-dd-rescue)

Were there any log files created by ddrescue that can help you determine what failed?

Have you tried *photorec* on the original drive?  Sometimes creating the image can cause the drive to heat up and fail, but simply reading small files will allow some data recovery.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by sibu4 on 2015-07-01
Thanks for replying.
- I think it's the noise of a dying harddrive - really dying.
- The drive passed smart test and the short test, but faild at the extendend test (gsmartcontrol) -> like 248 pending sectors / bad blocks
- I used gddrescue; I cancelled the recovery of the data, when ddrescue tried to scan over the hdd for a third time (at the point where no file could be recovered anymore after 5 hours), I have no clue about imagestructures from broken harddrives, I hope I can get the image to work.
- there should be a logfile, but I don't know where it is saved
- I don't really want to go over the hdd with photorec, before I haven't tried possible solutions to get the image work - but thanks for the tip

---

