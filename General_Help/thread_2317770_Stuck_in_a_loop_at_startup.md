---
title: "Stuck in a loop at startup"
date: 2016-03-19
forum: General Help
---

### Post by Xavier_Bechard-Doy on 2016-03-19
**Update:
OK, so it seems it was the boot order in the legacy boot options that was set to Network before USB storage device. 

But now on to the next problem... 

I'm stuck in a loop. 

I try to run Ubuntu Studio without installation and it just keeps restarting my computer and coming back to the same screen (boot options for Linux OS) 




**Original Post:

"Hi everyone, 

I used to test linux distros all the time back on an old desktop tower... 
Now times have changed (a lot, even in a year..) and I have a windows 10 Dell Inspiron 5-something. 

After a while of frustrations with windows (just name any problem, I have it, grhhh windows), I remembered about Linux, and so I went ahead, downloaded the OS (ubuntu studio, since I am making Audio Prod.), installed it on a partition(100GB) of my USB-HDD (Seagate 1TB).

So now I have a boot-able Ubuntu Studio USB-HDD.

The problem is when I try to run it, after getting past the BIOS/UEFI, Secure Boot options, I was able to boot from the drive but then I got this error:

"Realtek PCIe FE family controller series v1.34 (10/17/13) 
PXE-E61: Media Test Failure, Check Cable" *Image of a screenshot is attached.

After a little reasearch it seems to be that it is trying to boot from network instead of the USB-HDD. 
At least that's what I got online, but I have a feeling this might not be it because when I am using Windows 10, the Realtek driver ALWAYS ****s up. The sound starts to crackle and clip. 

Could this be as simple as a boot order? Is it a bad cable connection? Is it because of Realtek? 

Any help would be appreciated, meanwhile, I will check the bad boot order possibility.

---

### Post by oldfred on 2016-03-19
Removed email. 
Forum is regularly scanned and you will get spammed.
Plus we are a forum where many users volunteer to help and then other users can search for answers.

If you have UEFI and Windows installed in UEFI boot mode, you want to have Ubuntu installed in UEFI boot mode not the Legacy/CSM/BIOS boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

If you have secure UEFI boot off, but UEFI boot on, you should get 2 boot entries for flash drive. One UEFI:flashdrive and one flashdrive which is the BIOS boot.

You generally want UEFI boot first in boot order and if never using network boot have it last in boot order.

Flash drive must be correctly configured. And a few installers or a few flash drives or some combination, do not always work. Sometimes reinstalling ISO to flash drive with a different flash drive creator works.
      
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by Xavier_Bechard-Doy on 2016-03-19
thanks for the info I will check this right away, sorry for spamming and stuff.

---

### Post by Xavier_Bechard-Doy on 2016-03-19
That did the trick! 

wrong iso file and usb installer. 

linuxliveusb.com was the way to go.

I really learned a lot on this one, thanks.

---

