---
title: "Mount kicks in when fsck on usb"
date: 2012-12-15
forum: General Help
---

### Post by kuifje09 on 2012-12-15
When I try to fsck an usb drive, ( no automatic fsck is run when mounted ), fsck starts but at some point for an unkown reason to me, the drive is mounted.
Which causes fsck to fail.  This is very unpleasend.
I already edited fstab to block the mount by normal user because mount cannot be run then. ( Needs to umount first , and as root )

When I run fsck on /dev/sdh1 then the mounted disk when fsck is running on it, becomes /dev/sdi1.  ( funny is it ? )

How can I solve this beeing able to run fsck in orderly manner?

---

### Post by dino99 on 2012-12-15
[http://www.google.fr/#hl=fr&safe=off&tbo=d&sclient=psy-ab&q=ubuntu++no+auto+mount&oq=ubuntu++no+auto+mount&gs_l=serp.12...0.0.5.7140.0.0.0.0.0.0.0.0..0.0...0.0...1c.6nzV25I7ToA&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=ac9d2c5f7cf2a4ff&bpcl=39967673&biw=1485&bih=909](http://www.google.fr/#hl=fr&safe=off&tbo=d&sclient=psy-ab&q=ubuntu++no+auto+mount&oq=ubuntu++no+auto+mount&gs_l=serp.12...0.0.5.7140.0.0.0.0.0.0.0.0..0.0...0.0...1c.6nzV25I7ToA&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=ac9d2c5f7cf2a4ff&bpcl=39967673&biw=1485&bih=909)

---

### Post by Rexilion on 2012-12-15
Maybe it errors out, disconnects the drive and then reconnects. The system detects the reconnect and mounts it as it thinks a new different device has been mounted.

I think this is the case since it shows up as another device under /dev.

Could you try to fsck the device and post the output of:

```
sudo dmesg | tail -n30
```

Maybe you have USB issue's...

---

### Post by kuifje09 on 2012-12-15
Hey Rexilion, you are me just a step ahead.
I was doing the fsck on the console now, and I had the error you just presumed.

So this is the problem:

[..] Buffer I/O error on device sd[hi]* , logical block ...

Indeed immediatly thereafter the disk is remounted.

Wow, could this be solved?  Usb problem or Disk problem....

Just tested:  Disk is not SMART enabled.

---

### Post by Rexilion on 2012-12-15
Don't know. Try another USB stick to check which one of the two is the culprit.

Where there any more messages? The above command should have given you about 30 lines or so...

---

### Post by kuifje09 on 2012-12-16
Okay, this is not as good as I hoped for.
It seems to be a problem with my usb ports. Some 1.1, some 2.0
It looks very strange to me but I checked it all over again, and connected the usb disk to a usb 2.0 port, then checked again.  Now the disk , as fsck -p says, has no errors.
Although lots of pictures cannot be seen/opened. Remain whole or partial grey.
Maybe It is caused when writing to the disk? I do not know. But very sad, ans lucky...
The original pictures are kept save elswhere, so I can repair the content of the disk.

Afterall, I am not shure what has happend. I think 2 partitions where writen via usb 2 and 1 partition was written via usb1.1 port?  Only 1 partition had problems and when connected to a truly usb2 port the disk could be checked, altough the contend has some errors.

Even more strange, I made several backups on the (defect) partition with dump/(restore) which was always okay!

Thank for your help and ideas.

---

### Post by Rexilion on 2012-12-16
How old are the USB ports and the USB disk? Could be that their time has come...

On one of my parents PC's, the USB2.0 adapter died after 2 years! The box itself is still functioning after 9+ years.

---

### Post by kuifje09 on 2012-12-19
Hi, No it is not a problem of age or some defect.
There must be some issue using an usb2 device on a usb1.1 port.
Which is in fact stupid to do so... But nothing keeps you for doing so.
Now I know I have been faked, expected 4 usb2 and 2 usb1.1 ports but
I tested them out because of these problems and now I see I have 2 usb2.0 and 4 usb1.1
port. ( older MSI-Mobo but still okay. )
Even a pci board with 2 usb ports should be usb 2.0 but is tested as usb1.1
Don't know the make or type, not on the board visible...
( but this is going off topic, although in line of the problem )

But I have recreated a filesystem ,  and  no more problems.

---

