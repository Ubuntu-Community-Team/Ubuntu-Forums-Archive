---
title: "[SOLVED] FAT: codepage cp437 not found"
date: 2008-03-23
forum: General Help
---

### Post by MountainX on 2008-03-23
I followed this guide:
[http://wejn.org/how-to-make-passwordless-cryptsetup.html](http://wejn.org/how-to-make-passwordless-cryptsetup.html)
How to setup passwordless disk encryption in Debian Etch

After rebooting I get this error:

Trying to get the key from the USB keychain..
trying device: ssd
[ 51.827168] **FAT: codepage cp437 not found**
FAILED to find suitable USB keychain

Can anyone tell me how to deal with FAT: codepage cp437 not found?

The guide says, 
we need to add couple of modules to be loaded to the ramdisk:
# echo -e "vfat\nfat\nnls_cp437\nnls_iso8859_1" >> /etc/initramfs-tools/modules

I'm guessing this is related to my issue, but I'm not sure in what way.

Here is some more info:

sudo fdisk -l

[snip]

Disk /dev/sdd: 259 MB, 259522560 bytes
17 heads, 32 sectors/track, 931 cylinders
Units = cylinders of 544 * 512 = 278528 bytes
Disk identifier: 0x4e192479

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         932      253424    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(990, 16, 32) logical=(931, 12, 32)

```

$ sudo mount -t vfat /dev/sdd1 /mnt

```

FYI, the above command succeeds.

---

### Post by MountainX on 2008-03-24
Solution described here:

[http://www.linuxquestions.org/questions/linux-server-73/how-do-i-mount-a-usb-drive-at-boot-time-630115/](http://www.linuxquestions.org/questions/linux-server-73/how-do-i-mount-a-usb-drive-at-boot-time-630115/)

and, the same thing here:

[http://ubuntuforums.org/showthread.php?t=733457](http://ubuntuforums.org/showthread.php?t=733457)

---

