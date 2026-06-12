---
title: "Cannot install Ubuntu"
date: 2017-11-30
forum: General Help
---

### Post by alexandru-prahova on 2017-11-30
Hi! I'm trying to install ubuntu 16.04 LTS and I'm facing a wierd issue that Ubuntu should definetely fix! I have an ASUS ROG laptop with NVIDIA GEFORCE GTX 960M, i7 processor etc. The issue is, I cannot boot to the Ubuntu instalation disk. It's just stuck at the purple screen. I tried with nomodeset trick but after I have installed it and and installed the proprietary drivers(booting with nomodeset), when i try to boot the pc, it's just stuck at the purple screen. Neither nomodeset nor quiet splash parameters help. Please help me! I don't wanna go back to Windows anymore!

---

### Post by Bashing-om on 2017-11-30
alexandru-prahova; Hello - Welcome to the forum :)

The procedure you employed "should" have been successful to install and use ubuntu . So we must question the integrity of the install medium.

What means did you use to burn the .iso ? to a USB device or a DVD ? Let's verify what you have and then proceed.

[INDENT][INDENT]there is that process
[/INDENT][/INDENT]

---

### Post by alexandru-prahova on 2017-11-30
Thank you for greeting me! Ubuntu iso file was burned on to a WD portable hard drive using the built-in Startup Disk Creator. BTW, I have used the same drive to install Ubuntu to another PC ( Mac Mini 2013 or something like that).

---

### Post by Bashing-om on 2017-11-30
alexandru-prahova; K -

Let's back up and regroup - establish a firm foundation.

Verify that .iso image file:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

verify the copy to the WD portable hard drive :
Boot the live install medium;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -

Here there is " check disk for defects" are any errors found when this option is selected ?

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by alexandru-prahova on 2017-11-30
The checksum is ok, and the check disk for defects returned no errors. What should I do next?

---

### Post by Bashing-om on 2017-11-30
alexandru-prahova; Well ....

Pleasant surprise that the medium is consistent .
As you are able to boot up with the 'nomodeset' boot parameter it does point to a graphic's driver issue .

Let's see what is installed for the nvidia driver.
post back - Between code tags -
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
the outputs of terminal commands:
```

lsmod | grep nvidia
lsmod | grep nouveau
dpkg -l | grep -i nvidia

```

look'n at this as
[INDENT][INDENT]nothing but a thing[/INDENT][/INDENT]

---

### Post by alexandru-prahova on 2017-12-01
I ran these commands from the recovery shell as I cannot boot into the computer. [https://imgur.com/gallery/ovkbL](https://imgur.com/gallery/ovkbL)

---

### Post by Bashing-om on 2017-12-01
alexandru-prahova; Well !

That shows that the driver is not fully installed -- perhaps also there is a driver conflict /

Can you not boot with the 'nomodeset' boot parameter ? Booting nomodeset will make things so much easier to clean up and get a driver installed .

my little mind ->
[INDENT][INDENT]one way of looking at it
[INDENT][INDENT][INDENT]a way to getter done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

