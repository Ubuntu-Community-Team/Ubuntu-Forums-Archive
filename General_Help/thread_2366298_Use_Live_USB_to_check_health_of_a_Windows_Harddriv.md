---
title: "Use Live USB to check health of a Windows Harddrive?"
date: 2017-07-16
forum: General Help
---

### Post by shmish on 2017-07-16
Hello,
My Windows laptop won't boot and I think it could be the harddrive. I thought I might be able to boot Ubuntu from a USB disk and then use Ubuntu to check the health of the laptop's drive. However, when I run the Drive app, it only gives me access to the usb disk.
```

sudo fdisk -l
```

only lists my usb drive.  Should I expect my main HDD to show as well?

---

### Post by johndough2 on 2017-07-16
Hi

I suggest Gparted to show available drives.

If it does show a hard disk you will want to note the partitions names and numbers in case there is a possibility to mount and repair/copy/clone or whatever.

/dev/sda1   efi boot
/dev/sda2   reserved
/dev/sda3     windows

read man fdisk

 fdisk [options] device

       fdisk -l [device...]

sudo fdisk -l  /dev/sda

If in doubt please ask.

---

### Post by mrgnome on 2017-07-16
Yes. Normally, Ubuntu isn't permitted to access the main disk, but because GParted runs with root permission, it can see it. GParted also make a Linux distro specifically for running off a USB and diagnosing the main disk. You can pick it up [(http://gparted.org/download.php)]here]([http://gparted.org/download.php)

---

### Post by yancek on 2017-07-16
Since you only have windows installed, have you tried using the Repair option on your windows installation DVD or recovery CD?  Which version of windows are you using?  What output do you get from fdisk and if you run GParted, you might post an image here of the output.  Do you get any error messages?

---

### Post by HermanAB on 2017-07-16
Howdy,

You cannot use Linux to repair NTFS disks.

Google for BartPE instead.

---

### Post by mrgnome on 2017-07-16
> **HermanAB said:**
> Howdy,

You cannot use Linux to repair NTFS disks.

Google for BartPE instead.

I beg to differ; NTFS drivers are available and some distros support them out of the box.

---

### Post by HermanAB on 2017-07-16
Yes, there are NTFS drivers on all Linux and BSD distributions, but you cannot use it to *repair* a NTFS disk.

Get BartPE.

(BartPE is a CD or USB bootable version of Windows.  You can also a PE version from MS, but that costs money.)

---

### Post by yancek on 2017-07-16
> I beg to differ; NTFS drivers are available and some distros support them out of the box. 		

Drivers to read/write to ntfs partitions are not the same as software to repair damaged filesystems.  ntfsfix can do some very minor repairs on an ntfs filesystem and that's about it.  There would be no reason for any Linux developer to spend their time writing software to repair the proprietary/commercial windows systems.

---

### Post by shmish on 2017-07-16
I booted the live USB for GParted and the only device that it is seeing is the USB drive.  In terminal:
fdisk -l 

only listed the usb flash drive. I then got my hands on an external drive enclosure and cable connected the questionable harddrive to another windows computer.  Nothing appears in windows explorer.

In windows Disk Manager I get the following:
[ATTACH=CONFIG]276022[/ATTACH]

So either it's not reading because it has an OS on it, or the drive is (likely) shot.

---

