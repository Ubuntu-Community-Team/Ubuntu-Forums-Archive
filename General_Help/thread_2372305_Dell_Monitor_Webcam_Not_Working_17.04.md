---
title: "Dell Monitor Webcam Not Working 17.04"
date: 2017-09-23
forum: General Help
---

### Post by spode2 on 2017-09-23
For some reason, /dev/video0 is not created, although it is if I plug in an external webcam, and the external camera works OK.

The result of *lsusb* includes:

Bus 001 Device 004: ID 05a9:2649 OmniVision Technologies, Inc.

And *lsmod | grep video* gives:

uvcvideo                   90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops     16384  1 videobuf2_vmalloc
videobuf2_v4l2           24576  1 uvcvideo
videobuf2_core           40960  2 uvcvideo,videobuf2_v4l2
videodev                  172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                       40960  2 uvcvideo,videodev

And  *dmesg | grep 05a9* gives:

[    2.421502] usb 1-1.3.1: New USB device found, idVendor=05a9, idProduct=2649
[    4.295365] uvcvideo: Found UVC 1.00 device Monitor Webcam (05a9:2649)
[ 2771.428138] uvcvideo: Found UVC 1.00 device Monitor Webcam (05a9:2649)


I have no idea how to interpret this information, and would be grateful for any help.

---

### Post by spode2 on 2017-09-28
The problem was solved by  sudo apt install libv4l-dev and a reboot.

---

