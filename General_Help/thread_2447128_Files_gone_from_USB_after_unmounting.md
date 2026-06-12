---
title: "Files gone from USB after unmounting"
date: 2020-07-13
forum: General Help
---

### Post by robo731 on 2020-07-13
I am trying to copy files to a USB.

I copy the files (seemingly successfully), but once I unmount, they're gone.

It's a FAT32 drive according to fdisk and I mount it with ```
sudo mount -t vfat /dev/sdb1 /tmp/usb -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
```.

I sync and then unmount, but if I remount it, I don't see the files.

I don't believe it makes any difference, but for completeness, this is on an Ubuntu server installation over ssh.

I'm about out of ideas, so if anyone has any, it would be appreciated.

---

### Post by TheFu on 2020-07-13
dmask=027,fmask=137
are wrong. 4 octal characters are required.  Probably want to start with fmask=0002,dmask=0002 on Ubuntu systems, though you can use fmask=0007,dmask=0007 if you like.

---

### Post by robo731 on 2020-07-13
Oh ok, I'll give that a try, thanks.

I found the values I was using on this page: [https://help.ubuntu.com/community/Mount/USB#Using_mount](https://help.ubuntu.com/community/Mount/USB#Using_mount)

---

### Post by robo731 on 2020-07-13
> **TheFu said:**
> Probably want to start with fmask=0002,dmask=0002

I tried with these permissions, but unfortunately the issue persists.

I encounter no errors or permission issues when I copy the files over (and didn't with the previous permissions either).

I see the directory with ls after copying, but once I unmount and remount the drive, I no longer see it.

I don't think it's the case, but could it have something to do with the mount location? Is it because I am mounting it in /tmp?

Or should I mount the drive with sync?

**EDIT:**

Ran fsck both before and after copying, removed dirty bit and corrected cluster summary both times, but no luck

---

### Post by TheFu on 2020-07-14
Vaguely remember a problem when people used **usbmount** first causing some conflicts.
After you mount the storage, check the real mount options used - the mount command will show those for all mounted storage.

Using fsck on Linux to fix broken FAT32 is not likely to actually work. **Connect to Windows** and run **chkdsk** or/and **scandisk** to fix FAT32 or exFAT or NTFS issues.  Don't use Linux to fix Windows file systems.  The most we can hope for from Linux is that once a device stops working, that Linux will allow access to the files to get the data off, maybe.

Similarly, for Linux file systems, don't use Windows tools to try an fix stuff. It won't.

I haven't used vfat in some time - perhaps a year - but my last working **autofs** configuration was this:
```
/etc/auto.misc:/misc/16G  -nodev,nosuid,timeout=2,fstype=vfat,uid=1000,gid=1000 LABEL=16G
```

That would turn into a mount command like this:
```
sudo mount  -t vfat    -o nodev,nosuid,timeout=2,uid=1000,gid=1000     LABEL=16G      /misc/16G
```
My umask is 0002, so that would be picked up by the mount command.  For temporary storage, I prefer to mount using the LABEL option, not UUID or device. As a human, I remember labels better, though with autofs, I actually don't need to know any of that once it is setup.  Just plug the flash drive in, wait 5 seconds for the OS via udev to see the new storage connection, then simply access the storage .... 
cd /misc/16G/ and use as normal.  autofs will automatically remove the mount when all files become unused on it for a few minutes. I use **df -Th** to verify the mount it gone before pulling the usb device out.

But whether we use LABEL, UUID or the device partition with the file system, shouldn't matter at all.

What may matter is which OS release are you running?  My systems with USB ports are all 16.04.6  The problem could be release or kernel specific.

---

### Post by SeijiSensei on 2020-07-14
Unless you need to use this drive on Windows machines, I suggest formatting it to ext4.
```
sudo mkfs -t ext4 /dev/sdb1
```

If you need to convert it back to FAT32 in the future, reformat it again with
```
sudo mkfs -t vfat /dev/sdb1
```

Also, always cleanly unmount the device with 
```
eject /dev/sdb
```
You might or might not need to use "sudo" with that command depending on how the device is mounted.

---

### Post by GhX6GZMB on 2020-07-14
> **robo731 said:**
> 
I don't think it's the case, but could it have something to do with the mount location? Is it because I am mounting it in /tmp?


/tmp is the last place I'd mount storage, it has some unique properties:
 
[https://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/tmp.html](https://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/tmp.html)

Try mounting under /media instead, that would be the obvious place.

---

### Post by TheFu on 2020-07-14
For flash storage, the f2fs file system is pretty awesome. Fast and avoids writes.  Performance comparisions show it is usually faster than ext4. 

As long as the system isn't rebooted while the mount under /tmp/ happens, i wouldn't be too concerned.  
However, */mnt/ is* there specifically to be used as *a temporary work area* for stuff like this.

---

### Post by robo731 on 2020-07-14
The options shown by **mount** all look good, they match what I expect.

I gave the configuration shared by TheFu a try, but no luck.

Also tried mounting to  **/mnt**.

I do not **eject**, but I do **umount**.

Unfortunately I do need to use this drive with Windows, so ext4 is not a good option. I'd like to leave formatting as a last resort.

First I will try to repair the drive on Windows and report back.

---

### Post by vanadium on 2020-07-15
Make sure your file system is healthy and consistent in the first place before copying files to it. Ubuntu works perfectly fine with an error free fat32 file system. The issues you see may have been due to the file system being corrupt.

---

### Post by TheFu on 2020-07-15
I have an NTFS disk (really 1 partition that uses almost all the HDD) that gets corrupted by a video recording device about once every 3-4 weeks. The device splits the files every 2GB, so when the corrupted files begin it is very clear and I know it.  Then I'll pull all the files I can off, there will be a few errors in the output from that attempt, and I'll know to reformat the HDD.  I have a script to handle that and set a LABEL on it.  Once my script formatted the wrong partition - discovered the EFI boot partition by accident and the next reboot was a bad day for me.
Basically, it does this:
```
sudo mkntfs -Q -L 250G $DEV
```
I've had problems with FAT32 storage becoming corrupted too - same video device.  I have flash devices that have never been connected to that video recorder and those seldom, if ever, become corrupted.

Seems really odd to need a Windows file system, but not have a Windows machine?

---

### Post by robo731 on 2020-07-15
So I tried all kinds of things in Windows.

I tried running **chkdsk**, formatting, cleaning the disk with **diskpart** which gave a strange error: "cannot zero sectors on disk."

It seems for some reason it is write protected or the file system is otherwise corrupt. There is no switch to toggle on the device.

I then tried a couple things with Ubuntu.

I tried to format it to exfat with **mkfs**, tried to use **wipefs**, and tried to use **fdisk** to delete the partition on it and replace it with a new one.

All proceeded without error, but to no effect, the existing files on the USB are still there.

---

### Post by TheFu on 2020-07-16
> **robo731 said:**
> The options shown by **mount** all look good, they match what I expect.

ARe they what a group of experts would expect?

> **robo731 said:**
> 
I gave the configuration shared by TheFu a try, but no luck.

Also tried mounting to  **/mnt**.

I do not **eject**, but I do **umount**.

Please always say what "no luck" means, exactly.  Is there an error message? If so, always post it using copy/paste.
umount is better than eject, I usually type "sync" 3 times after, just in case.
Using /mnt/ is better too, but shouldn't matter.

> **robo731 said:**
> 
Unfortunately I do need to use this drive with Windows, so ext4 is not a good option. I'd like to leave formatting as a last resort.

First I will try to repair the drive on Windows and report back.
Seems you are at the Last Resort now. If it must be used with Windows, then I'd use exFAT today, assuming it is a flash drive.  "USB" is vague. If it is an SSD or spinning HDD, then I'd use NTFS.  You've never said what type of storage it is.  Flash storage fails, sometimes much quicker than people expect, especially if used daily.  The underlying technology used will determine if it lasts 4 months or 10 yrs.  Give a hint, please.  How old is this device?

---

### Post by robo731 on 2020-07-16
> **TheFu said:**
> ARe they what a group of experts would expect?

Ask and you shall receive.

```
/dev/sdb1 on /mnt type vfat (rw,nosuid,nodev,realtime,uid=1000,gid=1000,fmask=0002,dmask=0002,allow_utime=20,codepage=437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro)
```

For the record I also tried with **errors=panic**, but it did not panic.

> **TheFu said:**
> Is there an error message? If so, always post it using copy/paste.

> **robo731 said:**
> All proceeded without error

Like I said no error messages are displayed I'm afraid.

> **TheFu said:**
> Seems you are at the Last Resort now. If it must be used with Windows, then I'd use exFAT
Indeed. Yes I am looking to use exFat.

> **TheFu said:**
> How old is this device?
It is maybe 2 to 3 months old and sees little usage, maybe once every two weeks on average, so I've been thinking this issue is not likely due to wear and tear.

I suppose it's possible the hardware is faulty, but I'd like to exhaust all other options before resigning to such a conclusion.

---

### Post by TheFu on 2020-07-16
> **robo731 said:**
> It is maybe 2 to 3 months old and sees little usage, maybe once every two weeks on average, so I've been thinking this issue is not likely due to wear and tear.

I suppose it's possible the hardware is faulty, but I'd like to exhaust all other options before resigning to such a conclusion.

It could just be incompatible between the USB port/controller and the on-device electronics.  I have a few "name brand" flash drives that don't work at all with the USB3 ports on 1 laptop, but work fine with the USB2 controller on that same laptop and every other USB2/3 port in the house.

Is it a flash drive or something else?  I may have missed that answer.  "USB" is ambiguous.

---

### Post by robo731 on 2020-07-16
Yeah, I've been thinking to try with the USB 2 port on the laptop. Have had issues in the past with bootable media on 3.0 ports.

Sorry, I forgot to answer. Yes, it's a flashdrive.

---

### Post by robo731 on 2020-07-20
I don't think it's related to this. I have also tried across different devices.

---

### Post by sudodus on 2020-07-21
It is possible that your USB flash drive is 'gridlocked', which means that the **hardware** is read-only, damaged beyond repair. Maybe you can still return it and get a replacement from the vendor.

The following link may help you analyze the problem, and if you are lucky, solve it (if there is only 'confusion'),

[Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

---

### Post by robo731 on 2020-07-21
Thanks, I had actually bookmarked that while I was searching.

I'm going to give [this]("https://unix.stackexchange.com/a/216338/290481") a try first, if it doesn't work will try to follow that post.

---

### Post by sudodus on 2020-07-21
Interesting, this hdparm method is new to me. Thanks for the link :-)

---

### Post by robo731 on 2020-07-21
No problem, unfortunately it didn't work though.

There is an option to check the whether the protection is set, for me it was not.

I tried some [other things with **hdparm**]("https://askubuntu.com/a/1228996/491784") and [wiping with **dd**]("https://unix.stackexchange.com/a/595416/290481") as well but without success.

Maybe this drive is done for, but if anyone has any other ideas please let me know, I'm certainly willing to give them a try.

---

### Post by sudodus on 2020-07-21
Did you try the 'other alternatives' according to this link (other computer, remove other USB devices, try different USB ports ...)?

[Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

---

### Post by robo731 on 2020-07-22
Yes. Earlier in this thread I tried on Windows, USB 2.0 vs 3.0 ports, and the other items on that list.

---

### Post by sudodus on 2020-07-22
Sorry, but I am afraid that your USB drive is damaged beyond repair.

---

### Post by robo731 on 2020-07-26
Seems that might be case and I'm out of ideas anyways.

Thanks for the assistance though.

---

