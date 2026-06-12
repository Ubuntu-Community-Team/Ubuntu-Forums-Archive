---
title: "Cannot resume from hibernate using swapfile and uswsusp"
date: 2014-03-23
forum: General Help
---

### Post by ad2476 on 2014-03-23
Hi guys,

I'm trying to set up hibernate using a swapfile and uswsusp on my laptop. I've followed the following tutorials for this:
[Debian Wiki: Hibernation Without Swap Partition]("https://wiki.debian.org/Hibernation/Hibernate_Without_Swap_Partition")
[Ubuntu Forums thread]("http://ubuntuforums.org/showthread.php?t=1042946")

What I did differently from these threads is that instead of creating the swap file on my root partition, I created on my /home partition. The reason for this is that I don't have enough space on /.

**What happens when I try to hibernate:**
I run the following command: ```
sudo pm-hibernate
```
The system appears to successfully hibernate and shutdown. However, when I try to resume, it tells me: "The system snapshot image could not be read".

**System configuration:**
Here are the contents of the relevant files/configuration details:

```

~$ swapon -s
Filename             Type         Size           Used    Priority
/home/swap      file        3071996           0        -1

# swap-offset /home/swap
resume offset = 75776

~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic.efi.signed root=UUID=3b43438c-de6e-4b39-a1e3-d68685ca3b27 ro resume=/dev/disk/by-uuid/63d59054-3c70-403d-850f-fc249693481e resume_offset=75776 quiet splash acpi_backlight=vendor vt.handoff=7

~$ cat /etc/initramfs-tools/conf.d/resume
resume=/dev/disk/by-uuid/63d59054-3c70-403d-850f-fc249693481e resume_offset=75776

```

My /etc/uswsusp.conf file:
```

# /etc/uswsusp.conf(5) -- Configuration file for s2disk/s2both 
resume device = /dev/sda2
compress = y
early writeout = y
image size = 0
RSA key file = /etc/uswsusp.key
shutdown method = platform
resume offset = 75776
compute checksum = y

```

My /etc/fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / is on /dev/sda3
UUID=3b43438c-de6e-4b39-a1e3-d68685ca3b27 /               ext4    errors=remount-ro,noatime,discard 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=63B6-8198  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
# UUID=bb82baa8-4fed-4082-a869-1d403f122864 none            swap    sw              0       0


# /home is on /dev/sda2
UUID=63d59054-3c70-403d-850f-fc249693481e /home ext4 defaults,noatime,errors=remount-ro,discard 0 2
UUID=63B6-8198    /boot/efi    vfat    defaults,discard    0    1


# Mount the swap file as swap
/home/swap swap swap sw,discard 0 0

```

Relevant part of my /etc/default/grub:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="resume=/dev/disk/by-uuid/63d59054-3c70-403d-850f-fc249693481e resume_offset=75776"

```

[B]Debugging dmesg output:
[/B](I didn't post the entire output of the command, only what appeared relevant.)
```

~$ dmesg | grep "PM:"
[    1.454504] **PM:** Checking hibernation image partition /dev/disk/by-uuid/63d59054-3c70-403d-850f-fc249693481e
[    1.466032] **PM:** Hibernation image not present or could not be loaded.

```

I should note that when I first set up uswsusp and hibernate using swap file, it worked. However, after the third time hibernating, it began showing that error of "The system snapshot image could not be read". Only then did I add in the grub cmdline args and modify /etc/initramfs-tools/conf.d/resume. I believe my original resume file only contained "resume=/dev/sda2" and it worked for some reason... until it didn't.

Any ideas? This has been really bugging me, because I can't see what's wrong with my setup.

Thanks!

---

