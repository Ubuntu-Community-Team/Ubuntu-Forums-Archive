---
title: "Desktop constantly stalling / crashing on Ubuntu"
date: 2014-05-05
forum: General Help
---

### Post by Dr Spliff on 2014-05-05
I am having extremely frustrating problems with my desktop.  I had only Windows 7 installed, and an update got applied that messed up the bootloader.  I formatted and did a clean install of W7, installed the latest BIOS for my motherboard, tried the update again, and it still messed up the bootloader.  So again I formatted and reinstalled W7, this time shutting off all the updates.  It worked, but was extremely laggy and constantly stalled before and after I installed the proper drivers.  I tried a different hard drive, same thing.  Tried switching/taking RAM out of every possible slot, same thing.  I completely removed my graphics card and used the mobo video output, same thing.  So I finally said screw W7 and installed Ubuntu via a live CD.  

Ubuntu definitely is smoother than what W7 was, but still super laggy.  For instance, simply clicking on "files" I will get the circle spinning cursor, and it will be a good 15 seconds before the window pops up.  Firefox was constantly crashing on me, so I installed Google Chrome.  It takes about 30 seconds before the browser window pops up after I click on it.  If I have multiple windows up and try to open something, I get lagged so bad that the background fades to white and the very front windows turns dark black as the cursor spins.  I have had the resource monitor up trying to troubleshoot, and the RAM rarely goes above 20% and the CPU cores rarely go above 50%.  Keep in mind this happens while doing simple google searches or just navigating through folders.  If I have a video streaming it is really bad.  Everything is updated.   

I tried resetting CMOS, tried messing with some BIOS settings but nothing seems to help.   

System Specs :
-GIGABYTE GA-B75M-D3H LGA 1155 Intel B75 HDMI SATA 6Gb/s USB 3.0 Micro ATX Intel Motherboard
-16GB (4) x HyperX 4GB 240-Pin DDR3 SDRAM DDR3 1600 Desktop Memory Model KHX1600C9D3/4G
-Rosewill RP600V2-S-SL 600W ATX12V v2.01 SLI Ready Power Supply
-Western Digital WD Blue WD10EZEX 1TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive Bare Drive
-EVGA 02G-P4-2643-KR GeForce GT 640 2GB 128-Bit DDR3 PCI Express 3.0 x16 HDCP Ready Video Card
-Celeron CPU G530 @ 2.40GHz x 2 

I have eliminated everything possible I can think of.  Is anyone having problems with similar hardware or do you experts have any advice for trouble shooting?  Thanks in advance for any help.

---

### Post by Dr Spliff on 2014-05-05
Sorry forgot to mention I'm running Ubuntu 14.04 LTS 64-bit.

---

### Post by sarahfoxnz on 2014-05-05
i see a number of thereads of similar nature to this - Lagging, freezing / closig / rebooting problems etc. Ive posted to 2 of these threads myself.

Anyone know of a general / all-purpose reason for these general problems ? They appear to have started quite recently.

---

### Post by Dr Spliff on 2014-05-05
It's quite annoying.  I have a single core desktop with 1 GB of RAM that runs Windows XP faster than my new desktop.  And the worst part is that not all of the resources are being allocated when the freezing happens, yet everything is rendered useless because I can't click anything until the system "catches up."  I have tried everything down to different SATA cables, power supply, and completely removing the graphics card and cd drive.  This has been driving me crazy for 2+ months now.

---

### Post by Dr Spliff on 2014-05-05
I just did a fresh install of Ubuntu.  No improvement what so ever.  I am getting the "Force Quit" a lot more frequently now.  Tried the 32-bit version with same results.  Please help!

---

### Post by Dr Spliff on 2014-05-05
I am running the Gigabyte - UEFI DualBIOS Version F15 (Newest Version).  I only bothered to update it after I started experiencing problems.

---

### Post by deadflowr on 2014-05-05
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Aside from the link, do you know what driver you have installed for the graphics card?

---

### Post by Dr Spliff on 2014-05-06
Checking the Xorg log file I found :

```
[    15.013] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    15.052] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.052]     compiled for 4.0.2, module version = 1.0.0
[    15.052]     Module class: X.Org Video Driver
[    15.061] (II) LoadModule: "nouveau"
[    15.084] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    15.091] (II) Module nouveau: vendor="X.Org Foundation"
[    15.091]     compiled for 1.15.0, module version = 1.0.10
[    15.091]     Module class: X.Org Video Driver
[    15.091]     ABI class: X.Org Video Driver, version 15.0
[    15.091] (II) LoadModule: "modesetting"
[    15.091] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    15.091] (II) Module modesetting: vendor="X.Org Foundation"
[    15.091]     compiled for 1.15.0, module version = 0.8.1
[    15.091]     Module class: X.Org Video Driver
[    15.091]     ABI class: X.Org Video Driver, version 15.0
[    15.091] (II) LoadModule: "fbdev"
[    15.092] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.092] (II) Module fbdev: vendor="X.Org Foundation"
[    15.092]     compiled for 1.15.0, module version = 0.4.4
[    15.092]     Module class: X.Org Video Driver
[    15.092]     ABI class: X.Org Video Driver, version 15.0
[    15.092] (II) LoadModule: "vesa"
[    15.092] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.092] (II) Module vesa: vendor="X.Org Foundation"
[    15.092]     compiled for 1.15.0, module version = 2.3.3
[    15.092]     Module class: X.Org Video Driver
[    15.092]     ABI class: X.Org Video Driver, version 15.0
[    15.092] (II) NVIDIA dlloader X Driver  304.117  Tue Nov 26 21:27:08 PST 2013
[    15.092] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    15.092] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000

```

---

### Post by Dr Spliff on 2014-05-06
Reading through your link it does sound like GPU lockup.  I read through [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") and installed bumblebee 3.2.1-5 but it still seems to be occurring.

---

### Post by deadflowr on 2014-05-06
It seems like you're running the open-source nouveau drivers, which for some cards, aren't that great.:icon_frown:

Of course, that's what it seems, to confirm run this
```
lspci -nnk | grep -iA3 vga
```
It'll list the kernel module in use.

If looking into the closed source driver interests you
(If you happen to be running the nouveau driver, that is)
You can install it several ways.
Here's a good overview
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

and for extra, in case you want to install the drivers by through the command line, look over this
[http://askubuntu.com/questions/22118/can-i-install-extra-drivers-via-the-command-prompt](http://askubuntu.com/questions/22118/can-i-install-extra-drivers-via-the-command-prompt)

Though, I myself, would prefer to run only open-source drivers, but  some cards, (seemingly) nvidia more than others, perform much better with the close-source drivers a lot of the time. And in my experience tend to freeze far less often.

---

### Post by deadflowr on 2014-05-06
> **Dr Spliff said:**
> Reading through your link it does sound like GPU lockup.  I read through [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) and installed bumblebee 3.2.1-5 but it still seems to be occurring.

If you're running bumblebee, maybe try nvidia-prime
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
(Note there are install instructions after the first section.)

---

### Post by Dr Spliff on 2014-05-07
Thanks for the info.  I stupidly used a version 13 Ubuntu disk and then updated on my new install, which caused me to lose all searching capabilities in Unity, and I also could not access my bin folder to access apps, which would cause the whole system to lock up.  My dpkg then became corrupt, so I decided to start over.  

So I just did another (sigh) fresh install of Ubuntu 14.04 LTS 64-bit.  I completely removed my video card, and set the onboard video to 1GB.  It just restarted off the install disk, and I'm receiving a black screen with about a 1" brownish-black border that appears for about 10 minutes.  I am now getting a terminal-screen that says 

 usr/sbin/alsact1 terminated by signal 9 (Killed)

I cannot proceed to login on the terminal screen.  Will let it sit and see if anything progresses.  Regardless, waiting 20 minutes for a dual core to boot with 16 gigs of RAM is asinine.

---

### Post by Dr Spliff on 2014-05-07
It just switched to the "ubuntu" loading screen with 5 dots on it.  All dots are solid orange and not changing so far.  

I almost want to say this has something to do with the Intel fast-boot on my mobo, but disabling / tweaking the settings from the BIOS does absolutely nothing performance wise.  

It has moved past the "ubuntu" loading screen and is now just a black screen (no blinking cursor), although my monitor is still receiving a signal.

---

### Post by Dr Spliff on 2014-05-07
After about 20 minutes of loading I'm in.  Similar symptoms as previous installs so far.  Installing some updates and then I'll update you.

---

### Post by deadflowr on 2014-05-07
> **Dr Spliff said:**
> After about 20 minutes of loading I'm in.  Similar symptoms as previous installs so far.  Installing some updates and then I'll update you.

Is that just booting the installer?

Seems rather long.

I wonder you need to set a boot flag.

When you boot the install disk/usb-thingy at the selection screen where it asks to try or install, hit F6 to get a list of options. Press the spacebar?(I think that's it) for an option. ESC to get back to the main screen after the option is set.
The most common option is nomodeset, but I don't know which option might help, if any will help all.

---

