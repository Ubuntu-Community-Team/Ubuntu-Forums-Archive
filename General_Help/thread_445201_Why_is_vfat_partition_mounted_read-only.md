---
title: "Why is vfat partition mounted read-only?"
date: 2007-05-15
forum: General Help
---

### Post by vav on 2007-05-15
I have the following in my fstab:

```

# /dev/sda3 -- converted during upgrade to edgy
UUID=42CF-B82B /media/sda3 vfat defaults,rw,umask=000 0 0
# /dev/sda6 -- converted during upgrade to edgy
UUID=0C8A-0FA4 /media/sda6 vfat defaults,rw,umask=000 0 0

```

If I try to write to the mounted sda3, I get an error saying read only file system. However, if I write to the mounted sda6, I can do that without problems... why could this be? Where else would the permissions change?

---

### Post by taurus on 2007-05-15
Can you post the output of these two commands from a terminal?

```
sudo fdisk -l
ls -la /media
```

---

### Post by vav on 2007-05-15
Here it is:

```

 sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15358108+  83  Linux
/dev/sda2   *        1913        3824    15358140    c  W95 FAT32 (LBA)
/dev/sda3            3825        6374    20482875    b  W95 FAT32
/dev/sda4            6375        7296     7405965    5  Extended
/dev/sda5            6375        6505     1052226   82  Linux swap / Solaris
/dev/sda6            6506        7296     6353676    b  W95 FAT32

 ls -la /media
total 56
drwxr-xr-x 10 root root  4096 2007-05-15 12:44 .
drwxr-xr-x 25 root root  4096 2007-04-29 17:41 ..
lrwxrwxrwx  1 root root     6 2005-10-28 06:35 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2006-01-16 13:04 cdrom0
-rw-r--r--  1 root root     0 2007-05-15 12:44 .hal-mtab
---Sr-x---  1 root root     0 2007-03-24 10:23 .hal-mtab-lock
drwxr-xr-x  2 root root  4096 2006-01-16 13:03 iso
drwxrwxrwx 13 root root  8192 1969-12-31 16:00 sda2
drwxrwxrwx 17 root root 16384 1969-12-31 16:00 sda3
drwxrwxrwx 19 root root  4096 2007-05-15 14:47 sda6
drwxr-xr-x  2 root root  4096 2005-11-20 18:54 usbdisk1
drwxr-xr-x  2 root root  4096 2006-11-26 15:05 VV USB250 1
drwxr-xr-x  2 root root  4096 2006-11-26 15:05 VV USB250 2

```

---

### Post by taurus on 2007-05-15
Looks like you still have Windows on your machine.  Why don't you boot into Windows and run defrag and scandisk on /dev/sda3.

See if that fixes the problem in Ubuntu.  And in case you want to know, Windows can read/write to ext3 just fine with [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by vav on 2007-05-17
Huh... running Scandisk seems to have fixed the issue...

I was waiting to run defrag when I had time, but it works after scandisk (scandisk found 1 bad file). I'm pretty sure I had run fsck.vfat on it... does this not work as well as scandisk?

Unfortunately I found out about the IFS driver only a little while back, but after this issue I guess I'll transfer data out, reformat as ext3 and transfer data in.
But then if there is a similar problem in future, is fsck as good for ext3 as scandisk is for fat32 in fixing problems?

Thanks for your help.

---

### Post by merike on 2008-05-01
I have the same problem here. In fstab it is rw and it worked fine for months, haven't made any changes recently. But quite regularly it appears read-only. When I do umount followed by mount it seems to correct this. I noticed that before umount the number that follows file permissions in ls -la is different than after mount. What does this number stand for?
The owner, group and permissions are all the same before umount and after mount, but size differs.

---

