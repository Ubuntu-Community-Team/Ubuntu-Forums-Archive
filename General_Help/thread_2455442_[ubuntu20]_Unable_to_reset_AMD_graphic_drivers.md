---
title: "[ubuntu20] Unable to reset AMD graphic drivers"
date: 2020-12-19
forum: General Help
---

### Post by dpeg on 2020-12-19
Longtime linux user, first-time poster.

My machine's GUI has stopped working altogether: the startup screen is a mishmash of gray patterns. At first I thought the screen is just broken but during boot-up it works just fine, and I can use the Alt-F2 console. One of the last things I did before the incident was an unfortunate Zoom update (it was for an interview, I had no real choice). So I then thought this update may have done something to the graphics drivers. [Note: I am using bash, linux and tik and I can code a little but I never had to look under the hood of linux.]

Anyway, the still-working console allowed me to upgrade from Ubuntu 18.04 to 20.04 which I did, to no avail. I also followed some threads about updating xserver, which did not change anything. I tried to understand how to reset the graohic drivers to their original states but I failed. I am at a loss and so I ask for your help.
Many thanks for reading and any input! David

Here's part of the output of inxi -Fxaa. Please tell me if other/more data could be useful:

```
Machine: Type: Laptop System: Sony Product: SVE171121EB V: C903FULE 
                Mobo: Sony Model: VAIO UEFI [Legacy]: Insyde v: R0200E6 Date: 04/02/2012

Graphics: Device-1: Advanced Micro Devices [AMD/ATI] Thames [Radeon HD7550M/7570M/7650M] Vendor: Sony Driver: radeon
                v: kernel bus ID: 01:00.0 chip ID: 1002:6841
                Display: server: X.org 1.20.8 driver: radeon compositor: gnome-shell tty: 240x67
                Message: Advanced graphics data unavailable in console. Try: -G --display

CPU:      Topology: Quad Core Model: Intel Core i7-3612QM
```

---

### Post by CelticWarrior on 2020-12-20
Welcome.

If you were having issues already why did you go for a release upgrade? Why not do a fresh installation (of 20.04) instead?

---

### Post by grahammechanical on 2020-12-20
Do you get the Grub boot menu? If so, then select Advanced Options for Ubuntu and then select a Linux kernel with a Recovery Option. 

That should load the Recovery menu. Select Resume and Ubuntu should load to a login screen with a low resolution open source video driver. From there you can open Software & Updates>Additional Drivers. Now deactivate the proprietary video driver and reboot. Ubuntu should load with an open source video driver. Running Software & Updates>Additional Drivers again will allow Ubuntu to find an appropriate proprietary video driver for you.

Regards

---

### Post by CelticWarrior on 2020-12-20
@grahammechanical

Currently (and since many years ago) there are no proprietary drivers for AMD graphics*, new or legacy. All should work either with the 'radeon' or the 'amdgpu' drivers, depending on the hardware, and the proper one is automatically installed.

* For newer cards/chips, the ones running with 'amdgpu' there is an alternative 'amdgpu-pro' AMD proprietary driver that can be used instead of the the default open-source 'amdgpu'. Usually there are no advantages (and many obvious disadvantages) in using the proprietary variant except for some very specific usages.

---

### Post by dpeg on 2020-12-23
Many thanks for the replies!

CelticWarrior: It was a bad idea to upgrade from the console, I agree. But I was surprised that it was possible, and had hoped it might help.

grahammechanical: I did use the Grub menu to enter recovery mode but after choosing "resume", the screen went black with the cursor blinking in the top left (I waited for half an hour).

Another thing that surprised me: I had just USB-installed Ubuntu 20.04 on another machine, and so I tried it on the VAIO too. It booted from the stick but didn't fix the screen issue.

Perhaps I am asking the entirely wrong question... Here are two screenshots I made. Because they're pretty big and I found no way to scale them in this forum posting, I just link them (these are two jpg files on a university server):
[https://www.mathematik.hu-berlin.de/~ploog/VAIO_screenshot_login.jpg](https://www.mathematik.hu-berlin.de/~ploog/VAIO_screenshot_login.jpg)
[https://www.mathematik.hu-berlin.de/~ploog/VAIO_screenshot_console.jpg](https://www.mathematik.hu-berlin.de/~ploog/VAIO_screenshot_console.jpg)
The first one shows the non-working GUI login screen. You can see the moue cursor. The other one is me entering console from that screen, showing that it's (likely?) not a hardware problem.

If you have any ideas, please fire away. Would be a shame to lose a still good machine. Thank you!

---

### Post by CelticWarrior on 2020-12-23
That it can work in a TTY (command line mode) doesn't exclude hardware issues. Problems can happen only under load with drivers running.
Have you tried with a live session?

---

### Post by dpeg on 2020-12-23
Yes! Like I said, it didn't work at first but then I learned how to interrupt the Ubuntu boot process (Down-key) which gives the language selection screen (which looked a bit fuzzy and warbled but was readable) and afterwards boot choices. I went for 
"Try Ubuntu without installing (safe graphics)"

After that it got me in glaring red:

[   XX.XXXXXX] [drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!

What does that mean? 
Anyway, afterwards, it was doing all kinds of things (also nvidia was confusingly mentioned), brought up the above message again (with a different number) but did proceed to a working Ubuntu session. With the polygon panther background picture. Graphics were fine (not warbled or goofy) and I started a few programs which worked fine. If it helps, I can bring more screenshots. By the way, is there a possibility to access the long list of boot messages in some log file?

---

