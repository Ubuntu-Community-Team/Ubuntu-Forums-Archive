---
title: "Webcam works with VLC but not with Skype"
date: 2018-02-21
forum: General Help
---

### Post by ericjoh on 2018-02-21
Hi,

I'm running Ubuntu 16.04 amd64 and have this webcam:
# lsusb -v
[...]
 Bus 003 Device 004: ID 0bda:57a4 Realtek Semiconductor Corp.
 [...]
    iConfiguration          4 USB Camera
 [...]
      iFunction               5 HP 2.0MP High Definition Webcam
 [...]
      iInterface              5 HP 2.0MP High Definition Webcam

When I run e.g. "vlc" the webcam works as it should when I test it (Media - Open Capture Device: Video device name = /dev/video0) but when running skypeforlinux the webcam is identified as "HP 2.0MP High Definition Webcam" (which seems correct) according to Skype, but the image is black. I have tried different versions of skypeforlinux between 8.10.0.4 and 8.16.0.4 but the problem is the same. I have tried both the kernel 4.4.0-112-generic and 4.13.0-32-generic with same result. Any idea?

---

### Post by ericjoh on 2018-02-23
Since I have access to a few more computers of the same model, HP  EliteOne 800 G1 AiO, I have now tried skypeforlinux 8.16.0.4 on four  computers of the same model. The webcam works perfectly on all four of  them with VLC, but only on one of them with Skype.  It seems like HP is using different webcam hardware even for the same  computer model. The three that does not work with Skype has the  following webcam hardware according to "lsusb":

Bus 003 Device 004: ID 0bda:57a4 Realtek Semiconductor Corp.

The one that works with Skype has the following webcam hardware according to "lsusb":

Bus 003 Device 004: ID 0bda:5730 Realtek Semiconductor Corp. HP 2.0MP High Definition Webcam

Since the webcam hardware 0bda:57a4 works with  VLC it seems like the Ubuntu 16.04 system has a working driver for the  webcam hardware. Is there a way to get it to work with Skype?

---

