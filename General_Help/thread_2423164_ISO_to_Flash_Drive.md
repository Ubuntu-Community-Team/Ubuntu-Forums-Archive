---
title: "ISO to Flash Drive"
date: 2019-07-18
forum: General Help
---

### Post by hatewindows on 2019-07-18
Hello  I wanted to know if there is a simple way burn ISO image to usb flash drive.. I ve used Unetbootin over the years but for some reason it wont install in the latest 18 of Ubuntu.. Just wondering if there are others out there for Linux.. Thanks

---

### Post by uRock on 2019-07-18
What OS are you trying this with? I usually use the DD command to put ISOs on USB.

```
dd if=image.iso of=/dev/sdb bs=4M
```

---

### Post by wildmanne39 on 2019-07-18
I use startup disk creator and it come installed by default in Ubuntu, I have never had a problem using it, very simple.

---

### Post by oldfred on 2019-07-18
I only need UEFI, but this does not work for BIOS boot.

       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash drive partition & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)


New Windows ISO are now over 4GB, so you cannot directly extract to one FAT32 partition, but have to put boot files in FAT32 and rest in NTFS. Have not done it, so do not know details.

       
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) or 
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
           
 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

---

### Post by C.S.Cameron on 2019-07-18
Do you want to use the USB to install ubuntu? Try a Live or Persistent install using mkusb: [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
You can also do a Full install to USB the same as to Internal drive, just unplug the internal drive first.

---

### Post by VMC on 2019-07-18
I'm with @uRock.
I do it so often I created an '*alias*' for it:
 alias hyb='echo "sudo dd if=utopic-desktop-amd64.iso of=/dev/sdc bs=8M"&&lsblk'

*lsblk* points to which usb to use.

---

### Post by hatewindows on 2019-07-18
Thank you Everyone!!

---

### Post by TheFu on 2019-07-18
I use **dd** or **ddrescue** too. Something like this:

```
sudo ddrescue /path/to/ubuntu......iso /dev/sdZ  /tmp/log
```
ddrescue is handy for other uses where dd fails. It keeps trying to read blocks that stop dd cold. This shouldn't matter with creating a flash drive to boot, but if trying to move data from a failing disk to a new disk, it is invaluable.

But I don't know if creating an ISO works on anything after 16.04.x.  Can't think of a reason it wouldn't, but who knows?

---

### Post by uRock on 2019-07-18
> **TheFu said:**
> I use **dd** or **ddrescue** too. Something like this:

```
sudo ddrescue /path/to/ubuntu......iso /dev/sdZ  /tmp/log
```
ddrescue is handy for other uses where dd fails. It keeps trying to read blocks that stop dd cold.

But I don't know if it works on anything after 16.04.x.  Can't think of a reason it wouldn't, but who knows?

I will give that a try the next time I go to create a bootable USB and let you know if it worked. I'm going to be testing Debian 10 LXDE on my production system in the next day or two, so we'll see.

---

