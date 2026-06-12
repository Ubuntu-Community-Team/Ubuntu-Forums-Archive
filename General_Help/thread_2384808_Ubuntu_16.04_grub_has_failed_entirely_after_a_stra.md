---
title: "Ubuntu 16.04 grub has failed entirely after a strange update1"
date: 2018-02-12
forum: General Help
---

### Post by lightice1 on 2018-02-12
Hello! 

A couple of days I started a normal Ubuntu system update on my laptop, which seemed to go as normal, when it suddenly rebooted without warning. Then, rather than starting up the grub again, the computer instead started updating the Windows 10 that I also have installed on the disk, but haven't used for several months, but that update failed and was rolled back. Finally, I was given a some kind of emergency grub screen that I've currently been stuck with for two days, that looks like this: 

```

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

```

Tab does indeed give me a list of commands and "ls" shows the system partitions on the device, looking as follows: 

```

(hd0), (hd0,gtp8) (hd0,gpt7) (hd0,gpt6) (hd0,gpt5) (hd0,gpt4) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1) (hd1) (hd1,gpt2) (hd1,gpt1)

```

I tried installing a boot repair disk on a USB stick (using Rufus), but the machine does not seem to recognise it. Now, what can I do to get my system running, or failing that, format the hard drive and reinstall everything? I'm ready for the latter, if necessary, I have everything backed up on an external disk, in any case.

---

### Post by oldfred on 2018-02-12
Since you have gpt and Windows, system must be UEFI.
Windows only boots from gpt partitioned drives with UEFI.

 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

Also:

 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 


 Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by lightice1 on 2018-02-12
None of the USB drive versions worked. But since I finally happened to have time for more extensive googling, I managed to learn a manual command line solution: 

```

ls
set root=(hd0,[x])
set prefix=(hd0,[x]/boot/grub
insmod normal 
normal

```

With [x] standing for my boot partition that I figured out through trial and error. And finally "update-grub" in bash after getting Ubuntu properly started to get the grub running properly, again. With only five lines of code, I feel that this should be the go to solution over downloading gigabytes of boot disks...

---

