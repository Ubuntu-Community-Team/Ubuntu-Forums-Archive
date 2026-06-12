---
title: "Numerous Kubuntu Problems"
date: 2007-02-04
forum: General Help
---

### Post by Cheeco on 2007-02-04
Hi everyone, I have been having a lot of problems with Kubuntu (Dapper). I have organized them into a list below.

**Problem #1:**
I installed my Kubuntu system while using a LCD monitor but after the installation I switched back to a CRT monitor. I would like to set the resolution higher than 1024x768 but Kubuntu will not allow me to do so. I know that it is possible for the monitor to go at a much higher resolution because I have done it before. How can I increase the resolution?

**Problem #2:**
After the installation Kubuntu detects an incorrect graphics card (vesa, with a vesa driver) but my graphics card is nVidia GeForce 6150 LE. How can I change my graphics card to the correct one?

**Problem #3:**
After about 5-10 minutes my USB optical mouse stops working. It starts to work again after I unplug it and plug it back in, but then stops after 5 minutes again. How can I fix this?

**Problem #4:**
Everytime I log into Kubuntu, I receive an error message saying that I need a higher version of XOrg to enable tranlucency. How can I update the XOrg version?

Solutions to **any** of the problems above is greatly appreciated,

Thanks in Advance,
Cheeco :)

---

### Post by kodoku on 2007-02-04
Problem #1 and 2: Reconfigure X

In a terminal, type:

sudo dpkg-reconfigure xserver-xorg

You should be able to select your video card and your desired resolutions (use Tab and Space Bar to select)

Problem #3: Does this happen with other mice? If so, check system error logs

Problem #4: Have you applied all necessary updates via apt-get, aptitude or adept?

---

### Post by Cheeco on 2007-02-04
Solution #1 and #2:
I will go try that ASAP.

Solution #3:
This happens with every other USB mouse, there are some entries in the system log, I will paste them here.

Solution #4:
I have applied EVERY update, and upgrade possible with the default repositories. I am about to add extra repositories to see if that fixes some of the problems.


P.S. Thank you for the quick reply. I really appreciate it!

---

### Post by disturbedite on 2007-02-04
in regards to #3...
it sounds to me like you might have a failing mouse *and/or* a failing usb port...

---

### Post by Cheeco on 2007-02-04
Problem #1 and #2:
I was unable to find my driver that I need to select for a nVidia GeForce 6150 LE graphics card. Does anyone know what its called.

Problem #3:
I have tried numerous other mouses (all USB because PS/2 isn't available on my PC) and I have tried using different USB ports. On top of that it's a brand new computer. Below are any system log entries that I found related to the mouse:

[B]04/02/07 04:53:16 PM	Linux	kernel	[  222.089434] usb 2-7: USB disconnect, address 4
04/02/07 04:53:20 PM	Linux	kernel	[  224.251488] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
04/02/07 04:53:21 PM	Linux	kernel	[  224.403216] usb 2-7: new low speed USB device using ohci_hcd and address 6
04/02/07 04:53:21 PM	Linux	kernel	[  224.514115] input: USB Optical Mouse as /class/input/input4
04/02/07 04:53:21 PM	Linux	kernel	[  224.514160] input: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:0b.0-7
04/02/07 04:59:24 PM	Linux	kernel	[  455.401242] usb 2-7: USB disconnect, address 6
04/02/07 04:59:28 PM	Linux	kernel	[  459.393945] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
04/02/07 04:59:29 PM	Linux	kernel	[  460.008844] usb 2-7: new low speed USB device using ohci_hcd and address 7
04/02/07 04:59:29 PM	Linux	kernel	[  460.223478] input: USB Optical Mouse as /class/input/input5
04/02/07 04:59:29 PM	Linux	kernel	[  460.223530] input: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:0b.0-7[/B]

Problem #4:
I have attached a screenshot of the error messages.

---

### Post by Cheeco on 2007-02-05
Anyone have any ideas?

---

### Post by Happy_Man on 2007-02-05
Well, in regards to your mouse problem, using my limited abilities to decipher error text (what happened to English?! ;)), it seems that your computer cannot manage to hold on to your USB mouse. Have you tried googling "IRQ INTR_SF lossage"? That appears to be the root of the problem, and googling it may help find a solution. Sorry I can't help more!

---

### Post by ltmon on 2007-02-05
The error popup is based on a KDE setting.

Go to "System Settings -> Look & Feel -> Window Behaviour".  Select the "Translucency" tab and disable it with a checkbox.

Once you've got your video driver sorted out you could re-enable it, but it's probably better not to and use beryl instead.

To fix your drivers you need the "nv" driver (open source, but with no 3d acceleration) or the "nvidia" driver (closed source, with 3d acceleration).  "nv" should work by using the reconfigure command given above.

To install "nvidia" use this page: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia).  It's written for Ubuntu rather than Kubuntu, but the only thing you should have to do differently is to use the "Adept" package manager instead of the "Synaptic" package manager.

---

### Post by Cheeco on 2007-02-06
**Solution #1 and #2:**
I just used the command "sudo dpkg-reconfigure xserver-xorg" to reconfigure the X-Server.

**Solution #3:**
The mouse wasn't working due to a problem in the BIOS. I downloaded and updated the newer version from [www.dell.ca](www.dell.ca). Anyone with this problem should try the same thing.
[B]
Solution #4:[/B]
I disabled translucency.

I want to say a [B]BIG thank you to:
kodoku, disturbedite, Happy_Man, and ltmon.[/B] Thank you guys, I really appreciated all the quick resposes and hopefully this thread can help other users who are having the same problems.

THREAD SOLVED :)

---

### Post by disturbedite on 2007-02-06
> **Cheeco said:**
> 
**Solution #3:**
The mouse wasn't working due to a problem in the BIOS. I downloaded and updated the newer version from [www.dell.ca]("http://www.dell.ca"). Anyone with this problem should try the same thing.
[B]
[/B]I want to say a [B]BIG thank you to:
kodoku, disturbedite, Happy_Man, and ltmon.[/B] Thank you guys, I really appreciated all the quick resposes and hopefully this thread can help other users who are having the same problems.

THREAD SOLVED :)

i'm glad that it wasn't your usb port(s) failing, cuz i know what it feels like.  the two on the front of my box were fried a year ago...  nice it was a bios update.  must have been a bios bug/flaw then...

---

### Post by NeoChaosX on 2007-02-06
edit:nevermind

---

