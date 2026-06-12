---
title: "Static fuzz flickering on text in 12.10"
date: 2012-10-19
forum: General Help
---

### Post by PyGuy on 2012-10-19
Hey everyone. I'm having some issues with 12.10. In some applications, certain icons and text will have static flickering all over them. Is there a way to get rid of this?

What exactly is going on --> [http://i.imgur.com/fWnmi.png](http://i.imgur.com/fWnmi.png)

---

### Post by AirForceGuy2011 on 2012-10-19
I am having this same exact problem. Could it be a display driver issue? I don't know what your GPU is, but I'm running an Nvidia Geforce GT430. Never had this problem with Ubuntu 12.04.

---

### Post by 2F4U on 2012-10-19
I would also guess that it is a graphics problem.
@AirForceGuy2011: What graphics driver are you using?
@PyGy: Post your hardware specs, graphics card, and graphics driver.

---

### Post by ontaiwolf on 2012-10-19
That's the Nouveau driver, just install the regular Nvidia drivers and it will be fine.

---

### Post by PyGuy on 2012-10-19
My specs are:
64 Bit Ubuntu 12.10
GPU - Nvidia GeForce GTX 560 (not sure about the driver version, plus I'm not sure how to update the driver in 12.10 since nothing comes up in Software Sources)
CPU - Intel Core i5-2400 3.2 GHz
RAM - 8GB

---

### Post by Joao Lacerda on 2012-10-20
Hi friends, can maybe someone help on this issue?
I am having the exact same problem as described on the image send by PyGuy, that is also happening on the libreOffice when typing and on the browser menu and icons.

ubuntu 12.10 quantal 64bits
NVIDIA GTS 450
Using X.Org X server -- Nouveau display driver from xserver-xorg-video-nouveau (open sorce)

I have tried to isntall nvidia-current but everything went wrong.
Nvidia drivers do not work for me. 

Thanks in advance for any help

---

### Post by pikefan23 on 2012-10-27
im having this same problem.  just installed today, not sure what to do
specs:
Ubuntu 12.10 64-bit
intel core 2 duo 2.93 GHz
2 GB DDR3 ram
Nvidia geforce gts 450

anyone having this problem on ati or integrated graphics?  maybe just problem with nvidia

---

### Post by Eric Goulet on 2012-11-14
I experienced the problems all of you mentioned. Dell laptop with Nvidia card, fuzzy text with Xorg, and broken resolution with Nvidia driver.

The steps below solved the problem for me.

Install linux source: (sudo apt-get install linux-source) and headers (sudo apt-get install linux-headers-generic).

Uninstall your nvidia driver - for example: (sudo apt-get remove nvidia-current or sudo apt-get remove nvidia-current-updates or sudo apt-get remove nvidia-experimental-304).

Reinstall nvidia driver: (sudo apt-get install nvidia-current-updates).

When this successfully installs, use this command: (sudo shutdown -r now)

---

### Post by optimusLime on 2012-11-14
> **Eric Goulet said:**
> I experienced the problems all of you mentioned. Dell laptop with Nvidia card, fuzzy text with Xorg, and broken resolution with Nvidia driver.

The steps below solved the problem for me.

Install linux source: (sudo apt-get install linux-source) and headers (sudo apt-get install linux-headers-generic).

Uninstall your nvidia driver - for example: (sudo apt-get remove nvidia-current or sudo apt-get remove nvidia-current-updates or sudo apt-get remove nvidia-experimental-304).

Reinstall nvidia driver: (sudo apt-get install nvidia-current-updates).

When this successfully installs, use this command: (sudo shutdown -r now)
Much thanks Eric! Worked for me :)

---

### Post by hSync on 2012-12-01
> **Eric Goulet said:**
> I experienced the problems all of you mentioned. Dell laptop with Nvidia card, fuzzy text with Xorg, and broken resolution with Nvidia driver.

The steps below solved the problem for me.

Install linux source: (sudo apt-get install linux-source) and headers (sudo apt-get install linux-headers-generic).

Uninstall your nvidia driver - for example: (sudo apt-get remove nvidia-current or sudo apt-get remove nvidia-current-updates or sudo apt-get remove nvidia-experimental-304).

Reinstall nvidia driver: (sudo apt-get install nvidia-current-updates).

When this successfully installs, use this command: (sudo shutdown -r now)

Thank you! Worked pretty good :D

But... now my side bar doesn't appear anymore with mouse. do you know how to fix it? thanks

---

