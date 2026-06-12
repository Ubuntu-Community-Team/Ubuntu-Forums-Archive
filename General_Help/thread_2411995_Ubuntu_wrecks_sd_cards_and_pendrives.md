---
title: "Ubuntu wrecks sd cards and pendrives"
date: 2019-02-06
forum: General Help
---

### Post by boobz on 2019-02-06
I have this issue since i started my journey with Ubuntu (14.04) few years ago. I used a lot of pendrives on Ubuntu, where they worked fine, but then on any other device with Windows they became inaccessible - files couldn't be read or at least write and delete didn't work. Don't know if it's case of not unmounting device before unplugging or what, but tried to repair it with fsck, format, make new partition table and new partition with mkfs but it didn't work. Currently i'm trying to repair sd card, which also has been locked - it worked well for about 2 years, and stopped just after plugging it to the Ubuntu. After first use, I can't write anything on it, but can read without any problem. On the mobile phone it says it's damaged, and even can't read. Tried methods mentioned earlier and i also tried to change the permission with chmod 777 - group get write permission but 'others' didn't. Still can't write also with sudo - it looks like it's copied, but when i mount it again the file is not there.  This issue is quite ridiculous for me, especially when it's in most cases also impossible to unmount the device right for the first time, cause it's auto mounted again in 2 seconds after unmount. I think it's the thing the developers should closer look at, but i hope someone could provide me some tips on how to repair/unlock my sd card or prevent things like this, cause currently i can't plug any usb/sd storage device to the Ubuntu safely. :(

---

### Post by QIII on 2019-02-06
Hello!

First question:  What file system are you using when you format these devices?

Bear in mind that Windows directory and file permissions are immaterial to Linux, and ext file systems and Linux permissions are generally inscrutable to Windows.

If you have the device attached to a Windows machine when it is either shut down or goes into hibernation, Ubuntu will not touch it because it is flagged by Windows as in a hibernated state and messing with it would keep Windows from being able to use it later.

Best to format such devices with a Windows-native file system (Linux can use that) and make sure that the device is ejected from a Windows system prior to shutdown or hibernation and unmounted from a Linux machine after use.

Also remember that such devices have limited read/write durability and will eventually become useless in any case.

What you are describing, as frustrating as it is to you, is not a universal condition of Ubuntu or any other Linux distro.  I have been using Linux since the 90s with no particular problems -- other than eventual wear-out or failure of the device itself.

---

### Post by HermanAB on 2019-02-06
Note that Windows supports only three filesystems: NTFS, ReFS and FAT

Linux, however, supports every file system since Adam created the abakus to count Eve's apples.

It is best to format your SD and USB memory devices on Windows with NTFS.  It is a reliable file system and it works well on Windows, Linux and Mac.

---

### Post by rbmorse on 2019-02-07
One other thing to try...if your USB flash device quits working suddenly and you have been routinely using it with a USB 3.0 or faster port, try plugging it into a genuine USB 2.0 port.  I had a lot problems with SanDisk branded devices for awhile where the USB3 part of the controller on the device would experience a hardware failure.  The USB 2.0 part still worked so I could at least get the data off the device before sending back to SanDisk for replacement.  

Haven't had this for awhile, though. Partly because I beat the purchasing people into submission so they only order Samsung branded devices now and partly because I think recent production SanDisk devices are better.  

I endorse HermanAB's advice to format removable FLASH memory devices with the NTFS file system.

---

### Post by boobz on 2019-02-08
I tried to format it as FAT32 - just like it was before, it's microSD card from android smartphone. When i want to format it with gparted as FAT32 i got error: "Input/output error during write on /dev/mmcblk0" after few retry it prompts that it's successful and the files are still there untouched. I use adapter for this SD card to plug it into my laptop, it has lock button, but i tried both positions and it behaves different when it's locked on read-only position. Anyway it allways behaves like read-only and i can't change the permissions. I tried also some methods from askubuntu.com to resolve it but it didn't help (also as root). :/ I got this problems only with SD cards and pendrives, external drives work well. It drives me insane... Currently don't have access to any Windows machine, but im sure it wouldn't help, cause i tried to format pendrives under the windows as well, as any filesystem. Maybe it's the reason  QIII that it's because the Windows hibernation, those pendrives belonged to my girlfriend that probably didn't unmount it, both on Windows and on Ubuntu. It's just hard to believe it would make them useless and there's nothing i can do about it...

---

### Post by QIII on 2019-02-08
Do you realize that you have introduced a new variable here?

The adapter.

Anyway, they may not be made "useless".  Linux scrupulously avoids making changes to media flagged as hibernated by Windows.  Anything left in that state by Windows that was subsequently changed would appear to Windows as corrupt.  Linux treats all the files (remember that a directory is a "file" to Linux) as read-only.

---

