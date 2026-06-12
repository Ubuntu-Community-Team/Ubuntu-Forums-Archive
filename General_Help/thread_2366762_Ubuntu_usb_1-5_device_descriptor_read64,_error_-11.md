---
title: "Ubuntu usb 1-5 device descriptor read/64, error -110"
date: 2017-07-21
forum: General Help
---

### Post by Steve_Corman on 2017-07-21
I've been having some problems with a Linux box I set up to do video capture.  The capture device is a Hauppauge HDPVR.  It was working for years then suddenly failed.  I've verified that the device is OK by connecting it to a Windows system and using the Hauppauge capture software. 

It connects via USB. On boot I have been getting various errors:

```
usb 1-5: device descriptor read/64, error -110
usb 3-1: device descriptor read/64, error -71
usb 3-1 device not accepting address 4, error -71
```

I found a post about [how to get these error number definitions]("https://askubuntu.com/questions/653766/error-using-usb-flashdrive-what-usb-error-codes-mean") from the Linux headers, and apparently 71 means protocol error and 110 means connection timed out.  

Nothing changed on the hardware or bios before I started having these problems so I don't think it's a bios or bios settings problem, and I updated to a fresh install of 16.04, which would seem to rule out corrupted drivers.  Wondering if I might be having hardware issues with the USB system but would like to know for sure before I go replacing the mobo.  I have a usb keyboard and mouse and they're working OK.  So this whole thing is a little confusing.  Ady advice on troubleshooting would be appreciated.

---

