---
title: "Creative WebCam, no /dev/video after load gspac"
date: 2007-12-03
forum: General Help
---

### Post by ricewin on 2007-12-03
Hi,

I have a Creative WebCam PD1100, which is supported by spca5xx. My system is ubuntu 7.10

After plug it in usb, I can see it with
lsusb
Bus 001 Device 002: ID 041e:401b Creative Technology, Ltd

and the gspca is loaded with modprobe gspca
lsmod | grep gspca
gspca 608336 0
videodev 29312 1 gspca
usbcore 138632 4 gspca,ehci_hcd,uhci_hcd

However, there is no /dev/video files.
ls -al /dev/video*
ls: /dev/video*: No such file or directory

I also installed camorama. It says "could not connect to video device. Please check connection". Please let me know how to creat this /dev/video file.

Thank you

---

### Post by Yoochan on 2008-01-04
Exactly the same problems with a live! pro

---

### Post by fragos on 2008-01-04
I have no experience with that web cam.  There is a udev rule that creates the /dev/video* mount points.  Plug in your camera and do "lsusb" and see if the hardware is recognized.  The detail in lsusb can be matched with the existing rules.  If the device is recognized you can always write your own rule.

---

### Post by buntu_Geek on 2008-02-09
ME too having the same problemo... :( with the same cam... PD1100 after installing the gspca package...


The point is that ... even though the USB Creative Webcam is recognised...

venkat@venkat-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 041e:401a Creative Technology, Ltd 
Bus 001 Device 001: ID 0000:0000 

Camorama gives me this error....

Cannot connect to video device (/dev/video0)

Please help....

---

### Post by fragos on 2008-02-09
Look here [http://www.quickcamteam.net/hcl/linux/](http://www.quickcamteam.net/hcl/linux/)

---

