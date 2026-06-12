---
title: "Boot-Repair question with Ubuntu on external HD"
date: 2016-02-15
forum: General Help
---

### Post by sonicwind on 2016-02-15
Hey guys. I was getting familiar with Boot-Repair today in case I ever need it. Yes, I know to be careful!

When I start Boot-Repair, it asks "Is sda (1000 mb) a removable drive?"

I have Ubuntu installed on an external hard drive (sda). Windows is on the internal hard drive (sdb).

Is my external hard drive (with Ubuntu on it) considered a removable drive? My BIOS doesn't list it under Removable Devices but rather as a second hard drive. I'm not sure if that matters.

Thank you so much.

---

### Post by yancek on 2016-02-15
An external drive attached via usb is considered an external drive.  

> 
I have Ubuntu installed on an external hard drive (sda). Windows is on the internal hard drive (sdb).

That's unusual as generall the internal drive will be sda?

---

### Post by sonicwind on 2016-02-15
Thanks for replying yancek.

So are you saying the external drive is a removable drive for the purposes of Boot-Repair? I'm not exactly sure what you're saying.

I guess it's sda because when I'm using Ubuntu the external drive is my system drive. That's what I figured.

---

### Post by yancek on 2016-02-15
It's not uncommon to see an external drive listed under hard drives rather than Removable devices.  If you are testing the boot repair software, select the option to Create BootInfo Summary which will not make any changes and then view the output to see how the drives are shown, sda, sdb etc.

---

