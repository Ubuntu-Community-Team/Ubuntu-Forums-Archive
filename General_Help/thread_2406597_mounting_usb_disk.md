---
title: "mounting usb disk"
date: 2018-11-22
forum: General Help
---

### Post by dreweinhorn on 2018-11-22
Can somebody point me to a document the explains what happens in ubuntu when USB storage is plugged in?

Sometimes it automounts as it is supposed to.

Sometimes I have to use lshw to determine the device name and mount it manually.

Sometimes the device does not appear in the lshw output.

Right now I am struggling with a USB device that is not automounting and not even showing up lshw.

But, I can see the device appear and disappear using lsusb when I plug it in and remove it.

In the meantime, I'll be looking at stuff in /var/log and trying it on a different system.

---

### Post by TheFu on 2018-11-23
I don't know of any clear answer.  Ubuntu isn't 1 project. It is thousands of smaller teams each trying to make 1 tiny thing better, for certain values of "better."

How this happens has changed drastically over the different releases, so depending on the release, it is completely different.
USB storage isn't just 1 thing. There are thousands of different types and not all are supported.  It is a best effort attempt.  Not all USB devices are compatible with all USB controllers.  We see this all the time around flash drives and booting from them.  Not all have this capability on every system.  

So ... when systemd came along, the udev team decided to hand over their project to the systemd guys. I would start seeking an answer from the systemd documentation.  [https://www.freedesktop.org/software/systemd/man/udev.html](https://www.freedesktop.org/software/systemd/man/udev.html)

If you are just looking for a way to control where storage gets mounted with the minimal effort at mount time, then something like autofs might be what you seek. I use autofs to control USB storage mounts using the partition LABELS of the storage.  The main reason I want autofs instead of just trusting udev mounts is that autofs lets me control all the mount options directly.

---

### Post by dreweinhorn on 2018-11-23
Looks like my last reply got lost instead of posted.


D'Oh! I'm running 18.04 Ubuntu Mate ARMv7 on an Odroid XU4 Exynos5 Octa processor.

The current problem is storage is not mounting. It's not even showing up with lshw -short. It is appearing with lsusb.

I'm pretty sure the disk mounted with a prior operating system installation.

I hope to get back to this in the next couple of days.

I'll be looking in /var/log and trying it on other similar systems.

---

