---
title: "installation / boot problem 7.10 radeon 7000"
date: 2008-03-12
forum: General Help
---

### Post by rshiggs on 2008-03-12
Hello all, I am having a frustrating issue with trying to install Ubuntu 7.10 on one of my spare boxes.  I was not able to use the regular livecd / install cd to boot to the desktop.  I could see the status bar, but after that loaded, all I got was a black screen.  I tried playing around with the vga=xxx settings with different resolutions, but it all did the same thing.

Then I downloaded the alternate install cd, and that installed everything fine including grub.  Now I try to boot into ubuntu, all I get is a black screen after the ubuntu logo and status bar finishes.

I am thinking it has to do with the Radeon 7000 (pci) video card that is in the box.  Here are the specs:

Intel PIII 1.0Ghz (coppermine)
512mb ram
80gb HDD - with Windows XP SP2 installed
40gb HDD - where I installed ubuntu 7.10
2 x dvd/cd drives
Radeon 7000 video (pci)
SB Live card

Windows XP runs perfectly fine, so I am banging my head against the wall trying to get Ubuntu to work.  I have tried the Knoppix livecd, and that loads perfectly fine.  I tried searching for other posts about using the radeon 7000, but at least they can get to the login screen and boot to the desktop.  They seemed to be having dual display problems, but I cant even get one display to work.   Any suggestions would be greatly appreciated.

 -- Rich

---

### Post by phiphedog on 2008-03-12
Can you post your /var/log/dmesg so we can see what's happening at boot-up

---

### Post by rshiggs on 2008-03-12
What is the best way to do that?  I tried using that recovery mode, which brings me to a command prompt, but I could not change directories.

Is there something I press while the regular boot is going when the screen goes black?

---

### Post by chewit on 2008-03-12
I have a ATi Radeon 7000 64mb (pci). Worked striaght away after installing Ubuntu 7.10. It deteched using the "Radeon" driver. Maybe it hasn't used that.

---

### Post by rshiggs on 2008-03-12
Is there any way to ensure it is using the radeon driver?  I know the motherboard has an onboard video adapter as well, so I wonder if it is trying to pick that up, even though my monitor is connected to the radeon card.

---

### Post by phiphedog on 2008-03-12
When you boot into recovery mode type ```
dmesg
``` and this will output the contents to the screen. Perhaps you can just read the last few lines to see what's failing.

If you can access the hard disk from the live CD then you can open the file from there and post it that way.

If not then let me know and I'll send instructions to copy the file to your windows partition and you can read it from windows.

---

### Post by phiphedog on 2008-03-12
you can list the modules loaded into your kernel using lsmod

```
lsmod | grep radeon
```

---

