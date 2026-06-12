---
title: "complete freeze at boot"
date: 2008-05-19
forum: General Help
---

### Post by m4lysh on 2008-05-19
First of all: hi, im new on this forums :]

Now the problem:
I have a HP Compaq 6715s laptop with ATI X1250 graphic card. On it i had installed ubuntu feisty 64bit version, which worked quite well after some work with graphic drivers. Today i tried to update it to Gusty but it didn't go well. After the update and reboot the system won't load, after the ubuntu logo splash the screen goes black and freezes (No cursor at all, everything is black). Ctrl + Alt + F1 or Ctrl + Alt + backspace does nothing, and its the same story when i try to boot in recovery mode. I also tried to boot with nosplash and video=ofonly options, also with no success. The question is: is there any other way to log into the system so that i can actually see what is going wrong? Or is fresh installation the only way out of my problem?

---

### Post by m4lysh on 2008-05-21
bump.
the system runs when i run it with noapic noacpi parameters, however it takes almost 30 minutes to get to login screen oO any ideas? ;p

---

### Post by perillux on 2008-05-21
check my post here:
[http://ubuntuforums.org/showthread.php?t=802113](http://ubuntuforums.org/showthread.php?t=802113)

I'm positive that it applies to you.
However, you do need to log into ubuntu to be able to do those steps, so you have a few options.  When I used to get this error, I would have to wait like 10-15minuites to get in, so just try waiting for a very long time you should get to the login screen eventually.  If you can't get in.
Another option is to hit escape when GRUB is loading and select maintenance or safe boot or something like that I don't remember what it's called.  Then get to the command line log in and follow the instructions I posted on that other thread.

BTW: this should be fixed in Ubuntu 8.04 Hardy Heron.

---

### Post by m4lysh on 2008-05-23
Thanks for the reply.
I added 'acpi=off' parameter to boot line and now ubuntu starts at normal speed. However some issues like power management and wifi button doesnt work so im still interested in fixing the problem. I tried your solution, however  my /etc/usplash.conf already looks as it should (1280x800 - its a widescreen laptop :]) Any more ideas? 
Also i made a mistake in my first post, i updated it to Hardy, not Gusty, sorry ;]

---

### Post by m4lysh on 2008-05-30
bump.
After updating to the newest kernel even acpi=off parameter doesn't help :|

---

### Post by fonzai on 2008-06-04
> **m4lysh said:**
> bump.
After updating to the newest kernel even acpi=off parameter doesn't help :|

I have the same laptop, and I am running Hardy with all recent updates (backports enabled).

Adding the following parameter did the trick for me:
```
nohz=off
```
It is an upstream kernel bug, if I remember it correctly.

Still the WLAN doesn't work even though the ndiswrapper driver seems to be okay. For some reason the network manager doesn't show anything Wireless LAN related. It used to work on Gutsy but the upgrade broke something. I need to figure it out later.

---

