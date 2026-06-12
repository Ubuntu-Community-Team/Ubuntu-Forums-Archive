---
title: "Logitech Quickcam Communicate STX...spca5xx..not working"
date: 2006-11-07
forum: General Help
---

### Post by jadacyrus on 2006-11-07
I'm going so crazy..These are the details for my camera:
[http://www.qbik.ch/usb/devices/showdev.php?id=3503](http://www.qbik.ch/usb/devices/showdev.php?id=3503)

It says to load the spca5xx module.. I did that.. It loaded fine, still the camera is not detected by any means.. 

lsusb:
Bus 001 Device 010: ID 046d:08d7 Logitech, Inc. 

... I have no idea why this isnt working..it should work!!

---

### Post by fragos on 2006-11-07
Go to [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) and you can download a newer version of the driver that will work with the kernel in Edgy.

---

### Post by jadacyrus on 2006-11-07
Okay..I assume it is this package: gspcav1-20060925 ?

---

### Post by jadacyrus on 2006-11-07
Nuts on a Chipmunk! It worked...!! TYTYTYTY!!

---

### Post by fragos on 2006-11-07
> **jadacyrus said:**
> Nuts on a Chipmunk! It worked...!! TYTYTYTY!!

I'm glad the Chipmunk is so happy!!!! 8)

---

### Post by ztirffritz on 2006-11-22
I've downloaded the file you linked to, but what do I do with it next.  It is just a zipped file.  I unzipped it, but there is not read-me file explaining what to do with it.  There is no installer.

---

### Post by fragos on 2006-11-22
In what I downloaded there was a READ_AND_INSTALL file.  Open a terminal in the gspcav1 directory and run gspca_build.

---

### Post by razorbuzz on 2006-12-20
A few weeks late, but still great information. Terrific!  Thanks.

---

### Post by Ningbojoe on 2007-05-20
If still having problems installing Logitech Quickcam Communicate STX webcam, try this application.

[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

;)

---

