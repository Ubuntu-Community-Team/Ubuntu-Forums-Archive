---
title: "Webcam only receive static image"
date: 2006-12-08
forum: General Help
---

### Post by snowice on 2006-12-08
Hello,

I'm having a few problems with getting my webcam to work. I am using a Philips ToUCam PCVC 750K with kopete and I have contacts that use yahoo and others that use msn. 

Initially I got a black image from my own webcam and received a static image from my contact's webcam.

The first thing I discovered from browsing the forums was that the pwc driver appears to be broken in edgy. This I could solve by replacing the driver following the (excellent!) instructions in this thread [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090).

After replacing the driver, I had a nice webcam preview in kopete and my contact was also able to receive this video stream. The only problem I still have is that my USB device does not always seem to be detected automatically. Sometimes lsusb does not detect my attached webcam, but then a bit later it does show up again. So I wonder how I could fix this (use devfs?).

The biggest problem though at the moment is receiving video stream. I currently tried with a yahoo contact only. When he invites me to view his webcam, I only receive a static image, probably only the first picture in the stream gets through. He has no problem viewing my webcam though. So I was wondering whether this is a Firewall/NAT problem and how I could fix this last obstacle. My PC is behind a broadband firewall/router that does NAT. I tried opening port 5100 on the router, but the result was still the same. Please help!

---

