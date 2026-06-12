---
title: "V4L2 Webcam Software?"
date: 2005-10-26
forum: General Help
---

### Post by sailor420 on 2005-10-26
I've got a webcam that I plugged in and Ubuntu automatically detected the driver. It seems to be working fine, except for one thing--it's a V4L2 driver, and there doesn't seem to be anything else out there for it.

Most software that I've found won't support V4L2 devices. Is there any good webcam/webchat software out there that supports V4L2? I know GnomeMeeting does, but that doesnt help me, as no one I know has NetMeeting, and it doesn't work (at least to my knowledge) as a webcam server software.

Any ideas? Thanks...

---

### Post by alUrdun on 2007-09-29
The integrated webcam on my M1330 is v4l2 only -- no workee under v4l. I, too, am looking for some simple software with which I can take snaps or videos.

I can see myself in ekiga, but it would be nice to do more.

---

### Post by Sylchat on 2008-01-09
luvcview &#8212; by Martin Rubli &#8212; last modified 2007-07-06 14:48
    Small video capture program ideal for webcam testing and problem debugging. 
Ekiga &#8212; by Martin Rubli &#8212; last modified 2007-07-06 14:48
    Audio and video conferencing software supporting H.232 and SIP. 
FFmpeg &#8212; by Martin Rubli &#8212; last modified 2007-07-06 14:48
    Program suite to record and convert audio and video streams. 
fswebcam &#8212; by Martin Rubli &#8212; last modified 2007-07-06 14:48
    Command-line tool to capture webcam images. 
GStreamer &#8212; by Martin Rubli &#8212; last modified 2007-07-06 14:48
    V4L2 plugin for the GStreamer multimedia framework. 
MJPG-streamer and UVC-streamer &#8212; by Martin Rubli &#8212; last modified 2007-11-19 00:26
    Resource-friendly IP-based webcam streaming server 
uvccapture &#8212; by Martin Rubli &#8212; last modified 2007-07-06 14:48
    Command-line tool to capture webcam images. 
UVC incompatible software &#8212; by Martin Rubli &#8212; last modified 2007-07-06 14:48
    List of a few programs that have V4L2 support but do not work with the Linux UVC driver because of implementation limitations. 
unicap and ucview &#8212; by Martin Rubli &#8212; last modified 2007-11-19 03:00
    Video capture library with supporting GTK widgets 

cheers

---

### Post by simplejordon on 2008-01-30
Gomeetnow supports attendees on Windows, Mac, Linux, Unix, iphone and all other know plateforms. Anyway Sylchat.. that is a good list . let me check the product features.

---

### Post by imon9 on 2008-03-30
as many linux user notice, flash perviously only supported v4l webcam, while most of the new distro is using v4l2 as standard driver and v4l2 is also the standard driver embedded in the kernel.

So, most of us who has new webcam (especially those build-in) are using v4l2 driver and dont have the opportunity to use webcam based flash sites like:
[www.mebeam.com](www.mebeam.com)
[www.flixn.com](www.flixn.com)


NOW YOU CAN!!!

a developer wrote a loopdriver for webcam, you can get it from his website:
[http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/)

---

