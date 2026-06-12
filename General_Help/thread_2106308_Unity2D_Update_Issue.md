---
title: "Unity2D Update Issue"
date: 2013-01-18
forum: General Help
---

### Post by bman on 2013-01-18
I just did some updates which had Linux Headers and other stuff like that.

Once I rebooted and got back into Ubuntu, all my tweaks and customizations are gone. After playing with it for a bit, I figure out that it's acting like it's in a 2D mode. So I log out and choose the normal Ubuntu, and yet its still the same.

So now it's stuck in Ubuntu 2D mode no matter what I do. 

Anyone else with this issue?

AMD 12.11 Beta drives if it matters, normal Unity runs just fine.

---

### Post by ManamiVixen on 2013-01-18
Your current Ubuntu version please? Also specifically list your hardware including cpu, memory, graphics, motherboard chipset, ect...

---

### Post by bman on 2013-01-18
12.04

8GB DDR2 RAM
2.4GHz Q6600 Quad Core
780i SLI mobo
5850 Radeon

---

### Post by ManamiVixen on 2013-01-18
Most likely the beta driver is too new, need an older version.  Usually the beta version of a graphics driver supersedes the current xorg version as a dependency and is sometimes not caught by apt-get. So use the last stable release. :)

---

### Post by bman on 2013-01-18
I don't know why this always happens.

Ubuntu 12.04, Unity and all that was working perfectly fine without issues, on those drivers. I ran an update, rebooted and it's dead. So I know everything can run fine, the update caused an issue of some sort.

I tried to uninstall the drivers so that I could re-install them, thinking it might help, and it tells me 

```
Package fglrx is not installed, so not removed
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-amdcccle-updates is not installed, so not removed
Package fglrx-dev is not installed, so not removed
Package fglrx-updates is not installed, so not removed
Package fglrx-updates-dev is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

``` 

Not sure how that is possible. Can't install the drivers, because AMD says to uninstall them first.

---

### Post by ManamiVixen on 2013-01-18
try this:

sudo add-apt-repository ppa:xorg-edgers/ppa && sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install fglrx-installer

That face there is supposed to be : x with no spaces. But that shouldn't matter if you paste it in a terminal.

---

### Post by bman on 2013-01-18
So after doing that I'm stuck in text mode on reboot.

---

### Post by ManamiVixen on 2013-01-18
:-k Huh. Usually xorg-edgers fixes graphics issues. Sorry.

---

### Post by bman on 2013-01-18
I guess I am re-installing ubuntu

---

### Post by bman on 2013-01-22
So after a fresh install, and everything just fine, it happened again.

I installed lm-sensors and played with that, rebooted and I am back in 2D mode, at least something like 2D mode.

---

### Post by bman on 2013-01-22
There is no reason for this too be happening. I didn't do anything to it. 

I do not want to wipe my system again, it's a hassle.

---

### Post by bman on 2013-01-22
So I logged out and logged in with Gnome, the latest version, and it's broken as well, nothing is displayed, I can right click on desktop, that's about it. 

WTF is going on...

---

### Post by bman on 2013-01-22
*BUMP

Is it possible my ATI drivers crashed, and just have not started up again. Is there a command that allows me to restart, start etc AMD Drivers.

Gnome Classic (without effects) seems to work, not smoothly, but it loads everything normally.

---

### Post by bman on 2013-01-23
So I was looking through the Synaptic Package Manager and searched for AMD, and this is what I see.

I am going to assume that someone who has an AMD driver installed has more then what I have installed?

I originally on this install of Ubuntu 12.04 installed the latest AMD drivers, 13.1.

Assuming that is true, then it's like my drivers were randomly removed from the system, correct?

I am going to try and re-install them through the downloaded .run file, if it does not give an error then that means they are removed.

How would this be possible? I seriously didn't do anything when this happened.

**the installation did come up and say there is a previous version...so baH!

---

### Post by bman on 2013-01-23
**BUMP On page 4

I think many of my issues, such as this, is because of my old and dieing hardware, but I know it is able to run Unity 3D just fine, so it really makes no logical sense for it to randomly fail, and not let me back in.

Someone out there must have an idea... :(

---

### Post by monkeybrain2012 on 2013-01-23
So you have updated your kernel. Did you try booting into the previous kernel and see if things work?

If you only have one OS (Ubuntu) hold down the shift key when boot, a menu should appear, choose "previous versions .." and boot.

---

### Post by bman on 2013-01-23
Well no, the kernel thing was from the previous install. I have re-installed since then as I said....and the same thing happened, after doing nothing.

---

### Post by monkeybrain2012 on 2013-01-23
So it worked for a while and then it stopped working, right? Do you remember what did you upgrade or install before it stopped working?

---

### Post by bman on 2013-01-23
Not sure why your not reading my posts, but..

As I said, I installed lmsensors and that was it. Nothing that could cause this problem. I have also since removed them just to test, no luck.

---

### Post by monkeybrain2012 on 2013-01-23
Did it not work with both the amd driver and the open source one?

---

### Post by bman on 2013-01-23
Did what not work?

All drivers work. Just at some point I reboot, and I am stuck in Unity 2D.

---

### Post by monkeybrain2012 on 2013-01-23
Do you have a laptop with a hybrid graphic card? Googling suggests that some people are experiencing similar problems.

---

### Post by bman on 2013-01-23
No.

---

