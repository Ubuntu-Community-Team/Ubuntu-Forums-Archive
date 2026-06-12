---
title: "Logitech Quickcam Pro 9000 Image very instable in lucview and skype"
date: 2008-05-17
forum: General Help
---

### Post by Roger D on 2008-05-17
Hi

I'm having real problems with the Logitech Quickcam Pro 9000 on my Hardy desktop system, although it's supposed to 'work out of the box'

When I run luvcview in a terminal, the program starts, but the image is very unstable. It's a bit hard to describe - I can see myself clearly, but the image is broken up into squares which keep jumping about. When I try the test in Skype, I get the same effect, only worse - I can hardly see anything.

I've been digging around on this. According to my system log the uvc video drivers have been installed:

May 17 12:12:02 roger-desktop-new kernel: [   39.054334] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
May 17 12:12:02 roger-desktop-new kernel: [   39.067692] usbcore: registered new interface driver uvcvideo
May 17 12:12:02 roger-desktop-new kernel: [   39.067697] USB Video Class driver (v0.1.0)


But the end of dmesg doesn't look encouraging:

[  198.353108] uvcvideo: Failed to query (132) UVC control 4 (unit 2) : -71 (exp. 2).
[  259.490565] uvcvideo: Failed to query (130) UVC control 8 (unit 2) : 0 (exp. 2).
[  945.986534] uvcvideo: Failed to query (132) UVC control 3 (unit 2) : -71 (exp. 2).
[ 1319.993004] process `skype' is using obsolete setsockopt SO_BSDCOMPAT


Although I don't know what all this 'stuff' really means.

Getting a bit desperate, and all help much appreciate.

I know the camera works fine - I tested it in Windows

Roger D

---

### Post by andersvolker on 2008-05-22
Please see the picture delivered from Quickcam Pro 9000 attached in this post. In opposite the WEBCAM works properly in Vista.

The System is Gutsy on a laptop with AMD64. The WEBCAM is in Skype under UVC Camera (046d:0990) (/dev/video0). Offline Testpicture is o.k.

Is there anybody who can help a new ubuntu user.?

---

