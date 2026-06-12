---
title: "Camera unmounts after 5 sec"
date: 2007-05-23
forum: General Help
---

### Post by QOLIM on 2007-05-23
I have a HP Photosmart 635 and updated ubuntu to 7.04 last week.
Since then I can't import the photos from the camera anymore.
Everytime I connect it I get a popup saying the camera was found.
But after 5 seconds it unmounts and so he can't find the device anymore
> An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x3f0, product 0x7102). Make sure this device is connected to the computer.

Normaly the display of the camera shows "connected to computer" but now it only shows the message for 5 seconds and goes back into normal camera mode. 

And it isn't the bug I got in 6.10 in /etc/udev/rules.d/45-libgphoto2.rules 

the third line says SUBSYSTEM!="usb_device*", GOTO="libgphoto2_rules_end"

so thats ok i guess

but still it wont work and keeps disconnecting all the time :/

any help?

---

### Post by snobel on 2007-05-25
Try booting on the older kernel from the edgy-installation, and see if that cures it. If it does, then this is probably related to the same usb bug that gave my scanner narcolepsy after the feisty upgrade...

In that case you can either stick to the old kernel, or recompile the new kernel without the suspend/resume module. In my case, installing 'scanbuttond' solved it, because it polls the scanner all the time, but I don't know if it will work with a camera.

---

### Post by QOLIM on 2007-05-26
You were right, on the old kernel it still works.

Maybe I'll try to recompile the kernel when I have the time.

Thanks for your help

---

### Post by fragos on 2007-05-26
Interesting, I hadn't noticed because I always remove the media from camera and put it in the card reader to save camera battery power.

---

### Post by snobel on 2007-05-27
> **QOLIM said:**
> You were right, on the old kernel it still works.

Maybe I'll try to recompile the kernel when I have the time.

Thanks for your help
You're welcome. [Here]("https://bugs.launchpad.net/sane-backends/+bug/85488") is the link describing the workarounds. Actually, the more elegant method is to add your camera's ID to the file quirks.c before compiling the kernel - as described...

---

### Post by QOLIM on 2007-06-03
the funny thing is when I open digikam it says camera not found because its already unmounted
but if i pluy the camera out and in and click on retry on the right moment (right when it's mounted)
it stays mounted and I can transfer the pictures.

So I gues I just have to be quick :D

---

### Post by vanadium on 2007-06-03
Since Feisty, I also have an issue with my camera, Canon Powershot S50, though not so seriously. I can download pictures, but after a while, the remaining pictures are saved just as files with length 0. I then reconnect the camera, select these remaining pictures and at the end, I manage to download them all. I can just survive with this bug and I still have the option to buy an external card reader. I am not going to recompile my kernel, though!

---

