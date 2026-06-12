---
title: "Help recovering previous partition"
date: 2015-07-12
forum: General Help
---

### Post by Duncan_Bristow on 2015-07-12
Hello,

I had a ext4 partition taking up the entirety of my 4 TB disk. I was attempting to format an external hard drive as exfat, however I accidentally selected the internal 4 TB drive rather than the external one.

I have attempted to follow [these instructions]("http://ubuntuforums.org/showthread.php?t=1376383"), however parted doesn't seem to detect any partitions, and testdisk sees the exfat drive, as well as some ext4 superblocks but is unable to find the partition itself. Is there anything else I can do, or is my data lost forever?

---

### Post by Bucky Ball on 2015-07-12
STOP what you are doing. Do not use that drive for anything except trying to retrieve data. Boot from USB or disk to access it and not from the drive. 

See these links. Testdisk and/or Photorec are your friends.

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

Testdisk description:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Photorec description:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

You can create a SystemRescue disk/usb and use that. Always handy to have a copy of that around and available in any case. Good luck and let us know. ;)

(Little note, which you may be aware of. When you delete files, they remain. Where they are is marked as 'writeable'. Until that part of the drive is written on, your data is there. If you start using the drive, data starts to get written ... over your remaining data on sections of the drive that are now marked as 'writeable' possibly. So don't boot from that drive.)

---

### Post by oldfred on 2015-07-12
When you did the exfat format, did it also convert from gpt(GUID) to MBR(msdos)?
Then entire drive would not be formatted as MBR has a max of 2TiB. And that may make recovery more difficult.

If still one large partition and gpt, you could use Disks and just change type (not reformat) to Linux file system.

I might also see what gdisk shows. Change sda to correct drive if not sda.
       sudo gdisk -l /dev/sda

---

