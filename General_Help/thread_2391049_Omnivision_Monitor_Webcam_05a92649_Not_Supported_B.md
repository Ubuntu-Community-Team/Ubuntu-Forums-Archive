---
title: "Omnivision Monitor Webcam 05a9:2649 Not Supported By 18.04?"
date: 2018-05-05
forum: General Help
---

### Post by spode2 on 2018-05-05
I had a similar problem with 17.04 which was fixed by installing libv4l-dev. I have now upgraded to 18.04 and the problem has returned, even though libv4l-dev is present. Any attempt to access the camera gives an error that no video device is found, or that the file /dev/video0 does not exist.

Please can anyone confirm that this is a bug, or suggest a fix?

```
~$ lsusb
Bus 002 Device 003: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 006: ID 413c:2107 Dell Computer Corp. 
Bus 001 Device 005: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 004: ID 05a9:2649 OmniVision Technologies, Inc. 
Bus 001 Device 003: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
~$ lsmod | grep video 
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
~$ dmesg | grep 05a9 
[    2.506448] usb 1-1.1.1: New USB device found, idVendor=05a9, idProduct=2649
[    4.512430] uvcvideo: Found UVC 1.00 device Monitor Webcam (05a9:2649)
```

---

### Post by spode2 on 2018-05-05
So I just thought I would try reinstalling libv4l-dev, and it has solved the problem. Looking back at the same issue I had with 17.04, it looks as if the library was present in that case too, but a normal install worked that time, without needing a forced reinstall.

---

### Post by spode2 on 2018-05-06
It seems that what I thought was a fix was simply coincidence, and the fault has returned.

I found some more information from dmesg:

[    4.862756] uvcvideo: Found UVC 1.00 device Monitor Webcam (05a9:2649)
[    4.863352] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    4.864049] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[    4.864050] uvcvideo: Failed to initialize the device (-5).
[    4.864073] usbcore: registered new interface driver uvcvideo
[    4.864073] USB Video Class driver (1.1.1)
[    4.899781] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[    4.937695] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)


Due to the fact that the camera does work sometimes, I would guess that this is due to a timeout period during boot being too short, but I have no idea how to fix this.

---

### Post by spode2 on 2018-06-18
In case it helps anyone else, a fix which appears to work is:

Create a file 

/etc/modprobe.d/uvcvideo.conf 

and add this line to it

options uvcvideo quirks=0x100

---

