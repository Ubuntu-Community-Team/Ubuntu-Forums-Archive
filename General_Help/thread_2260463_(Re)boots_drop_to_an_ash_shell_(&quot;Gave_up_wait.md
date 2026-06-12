---
title: "(Re)boots drop to an ash shell (&quot;Gave up waiting for root device&quot;)"
date: 2015-01-12
forum: General Help
---

### Post by The Thunder Chimp on 2015-01-12
I've been using Ubuntu on a Windows dual-boot Sony Vaio VGN-CS390  laptop for more than five years now. Yesterday I made a fresh install of  14.04 LTS over 12.04 LTS. Everything worked fine, even after several  shutdowns and boot-ups. Today, after booting up in Ubuntu, everything  looked prime and proper, but my USB optical mouse wasn't working (it  wasn't even recognized by the lsusb command). I tried a reboot.


  But immediately after power on, *before* the GRUB screen or  the Sony Vaio screen appeared (before any operating system was loaded),  everything was slowed down by two orders of magnitude. The Sony Vaio  screen appeared after 5 minutes (it should take 2 seconds), and the Grub  screen, in which I selected Ubuntu, after 10 more minutes. I then  waited an extra 10 minutes for the following to appear:

```

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
    -Check rootdelay= (did the system wait long enough?)
    -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev
ALERT! /dev/disk/by-uuid/ceafd64e-e02d-403a-a558-ce5d8f748c3a does not exist. Dropping to a shell!

Busy Box v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

```


I shut the laptop down with the power button (apparently shutdown isn't part of the ash shell).


  I went on another computer and googled *Gave up waiting for root device*.  Apparently, it has something to do with USB ports. Maybe something is  wrong with the boot order, which I changed in the BIOS yesterday to  "USB-first" in order to install Ubuntu.


  I booted my computer up again, and this time it went fast, like it  had done for years. I thought the USB key that was plugged in had  something to do with it. But after rebooting 10 times with slight  differences (mouse plugged in, mouse plugged out, USB key in, USB key  out, etc.), I noticed that what makes the difference between a slow and a  fast boot is the amount of time the laptop has been turned off. It  takes 30 minutes to get to the *Gave up waiting for root device*  screen IF (at boot time) the laptop has been powered off for less than 5  minutes. If I boot the laptop when it has been turned off for over 5  minutes, it boots normally and fast, but doesn't recognize my dear USB  mouse.

  So guys and gals, where do we start?

---

