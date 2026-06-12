---
title: "Webcam not working"
date: 2020-08-01
forum: General Help
---

### Post by natbrowne on 2020-08-01
Hi,
So I have a Logitech Stream cam, which works at 1080 60fps in obs and logitech capture in windows fine, but will not work in linux. If I start OBS or GUV or similar it opens the cam at a certain res (480) once I try to change anything the software locks up and eventually the cam cannot be accessed at all. After a few tries it no longer shows in lsub, and now I notice that connecting a usb stick drive to a different port no longer works.

Any fix?

---

### Post by TheFu on 2020-08-02
What is the model number and **lsusb** number pairs for the device?  Generic terms aren't sufficiently exact.

---

### Post by natbrowne on 2020-08-02
> **TheFu said:**
> What is the model number and **lsusb** number pairs for the device?  Generic terms aren't sufficiently exact.

Bus 004 Device 002: ID 046d:0893 Logitech, Inc. Logitech StreamCam

---

### Post by TheFu on 2020-08-02
[http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids) doesn't have it in the supported list.
[https://usb-ids.gowdy.us/read/UD/046d](https://usb-ids.gowdy.us/read/UD/046d) either.

Appears you are on the bleeding edge.

---

### Post by natbrowne on 2020-08-03
Is there a cure for bleeding edgness :p anyone have any ideas? or will it solve itself with future updates?

---

### Post by ActionParsnip on 2020-08-03
[https://sourceforge.net/p/linux-uvc/mailman/message/36992708/](https://sourceforge.net/p/linux-uvc/mailman/message/36992708/)

May help. Seems 
```

mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0 -fps 30

```
(Not sure about the spacing there. Might be)
```

player tv:// -tvdriver=v4l2:width=640:height=480:device=/dev/video0 -fps 30

```

Will produce video. Does that work?

---

### Post by natbrowne on 2020-08-03
Kinda worked, so ran the mplayer command and the output was :
> mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0 -fps 30
Creating config file: /home/patrick/.mplayer/config
MPlayer 1.3.0 (Debian), built with gcc-9 (C) 2000-2016 MPlayer Team
do_connect: could not connect to socket
connect: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: Logitech StreamCam
 Capabilities:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Inappropriate ioctl for device
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Movie-Aspect is undefined - no prescaling applied.
VO: [vdpau] 640x480 => 640x480 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Audio: no sound
FPS forced to be 30.000  (ftime: 0.033).
Starting playback...
V:   0.0 1132/1132  0%  1%  0.0% 0 0 
v4l2: ioctl set mute failed: Invalid argument
v4l2: 1132 frames successfully processed, 8 frames dropped.

Exiting... (Quit)

The Image was live and connected the cam and didn't freeze anything - HOWEVER the image was garbled all over, like old style TV interference with greens and red mesh all over - basically unusable.

---

### Post by TheFu on 2020-08-03
> **natbrowne said:**
> Is there a cure for bleeding edgness :p anyone have any ideas? or will it solve itself with future updates?

A linux driver.  For my Logitech C920 Pro, it took about 3 yrs before a driver was available and I noticed.  I'd bought the webcam because it was listed as "the best" at the time, but didn't pay much attention to Linux support. I was burned, which has been common with certain vendors over the decades.

No way to know how long or if it will ever be supported. Most really popular device eventually get support.

A few months after I bought the C920, the C910 became known to support Linux and OSX. It was $20 more and I'm cheap. The webcam working on Linux wasn't a priority for me at the time.

There must be 10 hardware devices here that only have WinXP drivers. Only 1 of them do I hope to use again - a slide/negative scanner. The printers, scanners, RAID cards are all in the pile to be recycled.  When $55 gets me a laser printer and separate all-in-one fax, auto page-feed scanner, why would I fight to try and keep old hardware working? Heck, my all-in-one inkjet has never printed anything after the demo-ink ran out. I wanted just the automatic page feed scanner and fax on it. All have been working over 10 yrs now ... except the slide/negative scanner.  I still have hope, really, I do. ;)

---

