---
title: "Fingerprint GUI does not work"
date: 2016-02-11
forum: General Help
---

### Post by &amp;()@fr4%&amp; on 2016-02-11
[ATTACH=CONFIG]267230[/ATTACH]

When I try to enrol my left index finger (and other fingers) in the Ubuntu Fingerprint GUI on 14.04 LTS, after swiping my finger one time on the fingerprint reader on my PC, it shows a 'waiting' sign (in the screenshot above) and it does nothing after that. When I try to press any other buttons in the app, it force closes itself. What should I do? Hopefully someone can reply as soon as possible, and thank you.

---

### Post by yetimon_64 on 2016-02-11
> **elroygoh said:**
> ...
When I try to enrol my left index finger (and other fingers) in the Ubuntu Fingerprint GUI on 14.04 LTS, after swiping my finger one time on the fingerprint reader on my PC, it shows a 'waiting' sign (in the screenshot above) and it does nothing after that. When I try to press any other buttons in the app, it force closes itself. What should I do? Hopefully someone can reply as soon as possible, and thank you.

Going on the embedded picture the device is not recognized (no device name showing). Fingerprint reader support is patchy at best in linux, the fingerprint gui or the PPA for it only support a limited number of devices. Some devices are not supported at all.

 Try to find the device identifier with the command ...
```
lsusb
```
In my case the device reads as ...
> ```
Bus 001 Device 003: ID **138a:0050** Validity Sensors, Inc.
```
This bit of detail (shown bolded) can help you find out if it is possible to get the device recognized. IF you can find the device identifier it will be easier to tell if the reader (either in the repos or the ppa) can be made to work with your device. In my case even the ppa didn't work but a bit of source code for a driver was found online that could be built for the needed support for that particular sensor identifier number above (138a:0050). The code I found online was a university project for the developer and was a fork of libfprint for the purpose of adding support for the above mentioned fingerprint reader. I was very lucky to be able to build my own driver for the device from that source code.

---

