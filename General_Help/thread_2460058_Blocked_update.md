---
title: "Blocked update"
date: 2021-04-01
forum: General Help
---

### Post by john315 on 2021-04-01
Upgrade issue. How to find and remove the offending code?
---------------------
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:


openjdk-8-jre: Depends: openjdk-8-jre-headless (= 8u282-b08-0ubuntu1~20.04) but 8u275-b01-0ubuntu1~20.04 is installed
openjdk-8-jre-headless: Depends: libnss3 (>= 2:3.17.1) but 2:3.49.1-1ubuntu1.5 is installed
                        Depends: zlib1g (>= 1:1.1.4) but 1:1.2.11.dfsg-2ubuntu1.1 is installed
openjdk-8-jre-headless:i386: Depends: libnss3 (>= 2:3.17.1) but 2:3.49.1-1ubuntu1.5 is installed
                             Depends: zlib1g (>= 1:1.1.4) but 1:1.2.11.dfsg-2ubuntu1.1 is installed
------------
I accidently / foolishly down loaded a RaspBerryPi install application.
-----------
Install Raspberry Pi OS using Raspberry Pi Imager
imager_1.6.1_amd64.deb
From: [https://www.raspberrypi.org/software/](https://www.raspberrypi.org/software/)
--------
It worked and installed the code on the Raspberry Pi OS and
other operating systems to a microSD card for the RPi.
---
But now I can't find it nor remove it?!?! HELP!

---

### Post by TheFu on 2021-04-01
> But now I can't find it nor remove it?!?! HELP! 
Find what?
Remove what?  The microSD?

I'm lost.  

I've never used any special program to put an OS onto a microSD for use in a r-pi.  Any program that can copy bits from A-->B unmolested can be used.  On Unix-like OSes, there are lots of choices already built into the system.  cp, dd, cat can all be used.  The trick is to point the target location at the device "file" for the entire storage (microSD) in this situation.

---

### Post by ActionParsnip on 2021-04-01
are you trying to put a Raspberry Pi image on an SD Card? Is this the goal?

---

### Post by deadflowr on 2021-04-01
The imager package and the dependency issues are unrelated.
Most of the time we ask users to post the full outputs for
```
sudo apt update
sudo apt upgrade
```
So we can see what the real state of the packaging management utilities are.

---

### Post by john315 on 2021-04-03
I installed an app from Raspberry Pi. The installation has blocked any and all updates to my OS.
I need some way to find and remove the offending installed files? PLEASE!

---

### Post by grahammechanical on 2021-04-03
What command did you run to install Raspberry Pi Imager on Ubuntu? Was it this one?

> To install on **Raspberry Pi OS**, type sudo apt install rpi-imager in a Terminal window.

If you used apt install then you can remove the Raspberry Pi imager in 2 ways.

1) Open Ubuntu software and search for Raspberry Pi Imager. Then you can select remove/uninstall.

2) Run this code in a terminal

```
sudo apt remove rpi-imager
```

Knowing how you installed the imager gives us a clue to how you can remove/uninstall the imager.

Regards

---

### Post by mikewhatever on 2021-04-03
I am not sure the problem has anything to do with rpi-imager.
You could try to remove it with <sudo dpkg -P rpi-imager>.

---

### Post by TheFu on 2021-04-03
Read post #4 above.  Do that.  We ask for commands to gather facts. If you don't do what's requested, how can anyone help?

Uninstall the app.  If you don't know how to do that, how did you install it?  What sort of package was it?  Did you compile it? Download some file directly or what?  In theory, **sudo apt purge imager** should remove it, but the actual package name may be different.

---

