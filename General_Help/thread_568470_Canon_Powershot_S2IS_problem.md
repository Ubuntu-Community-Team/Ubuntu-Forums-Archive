---
title: "Canon Powershot S2IS problem"
date: 2007-10-05
forum: General Help
---

### Post by dachinster on 2007-10-05
Hi guys,
I have a Canon Powershot S2IS. Pretty great camera.
I accidentally deleted a movie file on the camera (.avi) and I would like to get it back.

When i plug the camera in, it comes up in PTP mode (meaning no drive letter assigned) only.

I need to find a utility that will recover the file for me.

Please note, i do NOT have a card reader or access to one.

Are there any utilities that can recover in PTP mode?

---

### Post by dachinster on 2007-10-06
file recovery from flash media in linux that recognize ptp mode anyone?

---

### Post by dachinster on 2007-10-07
ok, i finally got access to a laptop with a card reader.
it shows up as a normal usb drive now.

what utilities are available for linux to restore the deleted avi file?

---

### Post by dachinster on 2007-10-08
guys?
linux must have utilities do recover deleted files from flash disks right?

---

### Post by antonr on 2008-03-12
I have a similar problem with my Canon IXUS 860 IS.
I cut and pasted 2 JPEGs and 2 AVIs from the camera to the hard disk using konqueror.
The JPEGs made it but the AVIs arrived with 0 byte length. The "cut and paste" operation obviously believed that it was successful in transferring the AVIs because they were deleted from the camera.

So I am looking for recovery software.

I'm on Kubuntu 7.04 and I tried testdisk and photorec, but they don't seem able to get the correct partition information for the SD memory card in the camera, reporting it as only 512 Bytes (or so it appears to me).

```
sudo testdisk /list /dev/bus/usb/003/004
TestDisk 6.5, Data Recovery Utility, October 2006
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Please wait...
Disk /dev/bus/usb/003/004 - 512 B - CHS 1 255 63, sector size=512

Disk /dev/bus/usb/003/004 - 512 B - CHS 1 255 63
     Partition                  Start        End    Size in sectors

Partition sector doesn't have the endmark 0xAA55
```

I have the feeling that access to the SD ("secure digital") memory card is limited to some file transfer protocol that does not allow raw partition access.
There is an interesting read here:
[http://en.wikipedia.org/wiki/SD_memory](http://en.wikipedia.org/wiki/SD_memory)
Or it could just be an incomplete driver implementation.

---

### Post by Sef on 2008-03-12
> I tried testdisk and photorec

Links to [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and [photorec]("http://www.cgsecurity.org/wiki/PhotoRec").

---

