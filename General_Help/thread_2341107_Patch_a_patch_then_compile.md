---
title: "Patch a patch then compile"
date: 2016-10-24
forum: General Help
---

### Post by Kevin McCready on 2016-10-24
I'm not sure of the order of doing things in these instructions.
[http://www.ziplabel.com/sm3840/](http://www.ziplabel.com/sm3840/)

In particular I  don't know how exactly what this means or how to do it  - "IDs will need to be patched into the source code (sane_get_devices)
I couldn't find the phrase "sane_get_devices" in the patch sm3840_patch2

My USB Scanner has two IDs:

found USB scanner (vendor=0x05da [Prolific Technology Inc.], product=0x3021 [USB Scanner               ]) at libusb:002:004

found USB scanner (vendor=0x0bda [Generic], product=0x0129 [USB2.0-CRW]) at libusb:001:003

I installed sane-backends-1.0.15

But I'm not sure I properly installed the patch and tar.gz file over them. I'm not sure what "tar.gz OVER" something means. Do I have to find the phrase "sane_get_devices"

The background to my overall scanner problem is on a different thread.
[https://ubuntuforums.org/showthread.php?t=2340378](https://ubuntuforums.org/showthread.php?t=2340378)  

In the directory
/etc/sane.d
I've added the two ID's to the microtek.conf and microtek2.conf files

In the directory
/etc/udev/rules.d
I made a new file with
sudo subl microtekscanner.rules
then I put in the file:
SYSFS{idVendor}=="05da", SYSFS{idProduct}=="0129", MODE="664", GROUP="scanner"

Still stuck.

---

### Post by Kevin McCready on 2016-10-25
I think the source code I need to modify might be in

sane-backends-1.0.15.tar.gz

When I drill down I find 6 microtek files as per the image attached.[ATTACH=CONFIG]271792[/ATTACH]

The two files with .c on the end of them contain the phrases 'sane_get_devices'

What do I do now?

---

