---
title: "Convert Ubuntu install to ISO file"
date: 2018-07-31
forum: General Help
---

### Post by timc00k on 2018-07-31
I have Ubuntu installed and configured on my hard drive.

How can I convert this customised version of Ubuntu into an ISO file so that I can burn it to a USB stick and boot off of it?

---

### Post by HermanAB on 2018-08-01
One way is to install Ubuntu to a USB stick to begin with.

---

### Post by timc00k on 2018-08-01
> **HermanAB said:**
> One way is to install Ubuntu to a USB stick to begin with.

That's true, this would work, but my ideal preference is to be able to convert my desktop into an iso so that I can share copies with others as needed....Thank you

---

### Post by kurt18947 on 2018-08-01
Could you back up your install then restore that backup to as many USB drives as you wish? If you just want others to be able to boot from a single USB drive, Herman's suggestion should work. Just don't install any proprietary drivers, particularly video drivers. For instance, an install with Nvidia drivers will not boot on a system that doesn't have an Nvidia card. Keep everything 'vanilla' and it should boot on most machines. I've installed linux distros to USB drives and they've worked reliably. They're somewhat slower than installs to a hard drive or SSD but they've worked reliably. If you want to be safe, unplug/remove any hard drives before booting the live USB, that way you can be certain of not overwriting your daily use install.

---

### Post by yancek on 2018-08-01
> That's true, this would work, but my ideal preference is to be able to  convert my desktop into an iso so that I can share copies with others as  needed....Thank you 				

Does that mean including the ability to install your modified Ubuntu?  I would suggest doing an online search for 'Systemback' and 'PinGuyBuilder', both of which worked on earlier versions of Ubuntu.  Haven't tried either on 18.04.  If you want the ability to install from the iso you create you will probably need to install on your system the Ubiquity installer which obviously isn't installed on a standard installed system.

---

### Post by HermanAB on 2018-08-01
Just get Knoppix:
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

Yes, you can make your own Knoppix like version of Ubuntu, but it is not as easy as it may seem.

---

### Post by C.S.Cameron on 2018-08-01
You can convert your install into an .img, (image file) using dd.
An image file can be written to USB using mkusb in Ubuntu or Win32Diskimager in Windows.

---

### Post by sudodus on 2018-08-01
> **kurt18947 said:**
> Could you back up your install then restore that backup to as many USB drives as you wish? If you just want others to be able to boot from a single USB drive, Herman's suggestion should work. Just don't install any proprietary drivers, particularly video drivers. For instance, an install with Nvidia drivers will not boot on a system that doesn't have an Nvidia card. Keep everything 'vanilla' and it should boot on most machines. I've installed linux distros to USB drives and they've worked reliably. They're somewhat slower than installs to a hard drive or SSD but they've worked reliably. If you want to be safe, unplug/remove any hard drives before booting the live USB, that way you can be certain of not overwriting your daily use install.

At least in Ubuntu 18.04.1 LTS a proprietary nvidia driver **can** be installed (in an installed Ubuntu system) with the advantage, that some additional nvidia graphics chips/cards will work and without too much damage to portability. Only nvidia graphics chips/cards, that do not work with that proprietary nvidia driver will be affected. Intel and Radeon graphics are not affected. See this link,

[Install Nvidia drivers Full install USB flash drive](https://askubuntu.com/questions/1060435/install-nvidia-drivers-full-install-usb-flash-drive/1060548#1060548)

---

### Post by kurt18947 on 2018-08-04
> **sudodus said:**
> At least in Ubuntu 18.04.1 LTS a proprietary nvidia driver **can** be installed (in an installed Ubuntu system) with the advantage, that some additional nvidia graphics chips/cards will work and without too much damage to portability. Only nvidia graphics chips/cards, that do not work with that proprietary nvidia driver will be affected. Intel and Radeon graphics are not affected. See this link,

[Install Nvidia drivers Full install USB flash drive]("https://askubuntu.com/questions/1060435/install-nvidia-drivers-full-install-usb-flash-drive/1060548#1060548")

That's a change for the better, thanks!

---

