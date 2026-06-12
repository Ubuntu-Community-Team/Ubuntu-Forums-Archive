---
title: "Installing Grub to USB to Dual-Boot"
date: 2007-03-31
forum: General Help
---

### Post by antex on 2007-03-31
I was trying to follow a guide for getting Ubuntu dual-booting with Windows without affecting the MBR of the drive -- which is something I have to do, but I won't get into it.

[http://ubuntuforums.org/showthread.php?t=56723]("http://ubuntuforums.org/showthread.php?t=56723")

However, since I don't have a floppy drive, I thought I'd try to do it using a USB pen.

My set up before I tried installing Ubuntu was three partitions on hda, with hda1 hidden (Packard Bell, grr), hda2 holding Windows, and hda3 holding Documents and Settings and my data. I shrank hda3 so that the free space on it was 30 GB instead of 60 GB, and then I left the remaining space unallocated. In the installation, I chose to install on the largest continuous free space. At the GRUB step at the end, I changed it from "(hd0)" to "(sd1)", since my USB was at sdb. However, at the end of the installation, it gave me an error executing grub-install (sd1), so I tried again with "/dev/sdb" as the place to install GRUB and it worked fine.

Then, I did

```
dd if="/dev/sdb" of="/media/My Book/ubuntu.lnx" count=1 bs=512
```

Since I have a Western Digital external hard drive on sda, and I couldn't get it to work using of="/dev/sda1/ubuntu.lnx". It worked and the ubuntu.lnx file was created. Just to be sure, I also repeated the step with

```
dd if="/dev/sdb" of="/media/My Book/ubuntu2.lnx" count=1 bs=446
```

Since I know that the first 446 bytes is the bootloader, and 512 includes the partition table.

I rebooted into Windows with no problems, took the files from the external hard drive and added them into C:\, and then edited my bootloader, adding the lines

```
C:\ubuntu.lnx="Ubuntu Edgy Eft (6.10)"
C:\ubuntu2.lnx="Ubuntu Edgy Eft (6.10) 2"
```

I rebooted, and at the prompt, tried the second one first, and it gave me an error saying something like, "This is not a valid boot floppy." The first one also doesn't work, and gives me "GRUB Hard Disk Error". After trying some stuff out, I tried leaving the USB in the computer, and chose the first option again, and it just gave me GRUB on the screen.

One thing I did try to do was download "dd for Windows" and use the dd command from within the command prompt on the USB drive. However, the exact same thing happened.

If I leave the USB in the computer and restart, I'll be given GRUB GRUB GRUB GRUB, or just a blinking cursor, and nothing will happen.

I think the issue might be that I can't actually boot into Ubuntu and *then* dd the USB, as the guide says.

I really want to get using Ubuntu, so it'd be great if someone could fix this for me.

---

### Post by antex on 2007-03-31
*bump*

---

