---
title: "Issue with a sd card adapter"
date: 2022-08-05
forum: General Help
---

### Post by pratir2 on 2022-08-05
I bought an SD card reader (capable of using USB 3.0 read/write), but it does not work right on my linux OS. When I plug in my device to my computer's front panel or motherboard USB 3.0 ports, it takes maybe half a minute or a full minute to show up as a mounted device in Files. Sometimes, the SD card does not even show up (not even in unmounted drives), but when it does mount, I usually get an error message saying the device is busy. The device shows up in the lsusb console list as "Bus 001 Device 008: ID 05e3:0756 Genesys Logic, Inc. USB Storage" no matter what USB port I am using. I tried other SD cards. I am able to use my device with the USB 3.1 and 2.0 ports (but those are at the back of my computer). I upgraded to jammy from 20.04, and that did nothing. I tried two things from other posts I found. One was reinstalling udisk2, and the other was installing a couple of packages that I can not name at the moment. I am still new to the Linux world, so I would not even know where to begin troubleshooting further.

The SD card reader in question is this: [https://www.amazon.com/uni-Adapter-Supports-Compatible-MacBook/dp/B081VHSB2V/ref=sr_1_8?crid=29DI5YQXUG90Y&keywords=usb+3.0+sd+card+adapter&qid=1659752655&sprefix=usb+3.0+sd+card+adapter%2Caps%2C100&sr=8-8](https://www.amazon.com/uni-Adapter-Supports-Compatible-MacBook/dp/B081VHSB2V/ref=sr_1_8?crid=29DI5YQXUG90Y&keywords=usb+3.0+sd+card+adapter&qid=1659752655&sprefix=usb+3.0+sd+card+adapter%2Caps%2C100&sr=8-8)

Thanks in advance.

---

### Post by sudodus on 2022-08-06
USB devices are not always fully compatible. Both built-in and external devices can be 'guilty'.

If the USB cable is long enough, I would keep it connected in one of the USB ports in the back of the computer where it works. An additional advantage is that one more USB port in the front will be available for other tasks.

---

### Post by pratir2 on 2022-08-08
Fair enough. I just wish I knew more about programming to see if I could make it work. I have a few USB devices around that I would love to make compatible. What resources would you recommend for making or adapting device drivers and such?

---

### Post by sudodus on 2022-08-08
I don't know enough to give you a good answer. Let us hope that somebody who knows better will see this thread ...

---

### Post by pratir2 on 2022-08-08
Alrighty. Thanks for your reply! Looks like it's gonna be a USB extension for now.

---

