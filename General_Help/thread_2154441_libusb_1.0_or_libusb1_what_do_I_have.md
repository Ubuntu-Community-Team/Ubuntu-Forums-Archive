---
title: "libusb 1.0 or libusb1 what do I have"
date: 2013-06-14
forum: General Help
---

### Post by AgentZ86 on 2013-06-14
Hi

I'm going to install PyUsb
[https://github.com/walac/pyusb](https://github.com/walac/pyusb)

Say I need at least one of the supported libraries (libusb 1.0, libusb 0.1 or OpenUSB)
What do I have ? on ubuntu 13.04

I try apt -cache search libusb or libusb1
It shows libusb1

Is libusb1 the same as libusb 1.0 ? or .1 or OpenUSB ?
I'm not sure how to interpret this

Please advise
Thanks

---

### Post by HiImTye on 2013-06-14
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
apt-cache is not the best utility to check what you have installed unless you know the package name and want the version info. aptitude is the best tool for most command line jobs (except version info)
```
sudo apt-get install aptitude
aptitude search libusb~i
```

---

