---
title: "Wondering if there is even a point to try"
date: 2014-04-04
forum: General Help
---

### Post by Zirts on 2014-04-04
Hi!

So I have installed Ubuntu on various laptops before and it has mostly been very ok. Things works, just got to tinker a bit here and there for things to be perfect for me.

Now yesterday I wanted to install Ubuntu 13.10 on my desktop computer. The computer is this:

CPU: Intel i5 4570
Mobo: Asus B85-Plus
GPU: GTX 760
Monitor: BenQ XL2411T 144 Hz monitor
Network adapter: TP-Link TL-WN821N adapter, V4 from the batch
HDD: a 7200 pm. 1 TB drive

So I started installing it on this system and got it installed successfully. I did the restart and got in my system. First thing I notice that new folder and all the applications that Ubuntu has with it at start, launch very slowly compared to laptop. Maybe it is becasue laptop has Ubuntu installed on SSD? But then still the performance hit this gives is ridiculous. Launching a simple application like system settings takes a good 4 seconds or so allready.

So the the next point. WIFI... At first wifi seems really fine, I can connect to my home network and update my system via Terminal without any problems. Infact I downloaded about 1 gb of data via Terminal before I even opened up my browser. Now when I opened up my browser, I was able to visit 2 webpages and then my internet was gone. It showed that I still had connection but nothing really loaded. Even ping google.com did not work in Terminal. I had to restart for this to be fixed. After restart, numerous crash reports appeared saying that ubuntu software center has crashed and what not. Can you belive it, allready stuff crashing after clean install?
So I thought maybe it's about the browser, I uninstall firefox and installed Chomium but still the same deal, I could surf the web in Terminal for ages but once you hit up the browser, connection is gone.

And now to the graphics. At first it was all okay, the Nouveau driver seemed to be really good for regular desktop use. I could see clearly that it was able run it on my 144 Hz monitor, eveything moved smoothly. Now because I wanted to take use of my GPU also, I installed the Nvidia proprietary drivers. I first added the xorg-edgers PPA and then installed the latest driver from there, Restarted and horror began.
First the Ubuntu boot splash is broken after a proprietary driver install. Is this normal? No!! Am I experiencing this alone? NO! Okay, so I get passed that to the desktop, open up a window and try to move it. 60 Hz all over me, things are slow and choppy, scrolling in a folder full of lot of files will cause graphical glitches that were not there before.
So I open up nvidia-settings as sudo and edit my refresh rate to 144 Hz from there. Apply it, save the xorg.conf and restart. Nothing changed, absolutly nothing. So installing a proprietary driver seems to make things even worse it seems?

I mean, I dont even know where I would start with fixing all this madness...  So I am asking you guys, is there any point to even try to do this with this kind of hardware? Or should I just pass and stick top laptops with Ubuntu?

---

### Post by mastablasta on 2014-04-04
> **Zirts said:**
>  Maybe it is becasue laptop has Ubuntu installed on SSD? 
Could be.

> 

Now because I wanted to take use of my GPU also, I installed the Nvidia proprietary drivers. I first added the xorg-edgers PPA and then installed the latest driver from there, Restarted and horror began.


xorg- edgers is opensource exeprimental/testing driver. this is not proprietary driver. i am not sure what you did here.

---

### Post by Zirts on 2014-04-04
So I should not install the driver from xorg-edgers? Instead from Nvidia's home page?

---

### Post by buzzingrobot on 2014-04-04
Installing on an SSD should make file operations faster, not slower.

The safest way to install a proprietary video driver is via the Additional Drivers facility in Ubuntu.  The xorg-edgers PPA, like all PPA's, is unoffical.  Also, installing the xorg-edgers PPA will also set you up to very likely have other core components replaced at the next update.  Proprietary video drivers have a history of being fickle about playing well with one kernel version of another.  It is not rare for a proprietary driver to be working just fine and then crash on the first reboot after a kernel upgrade.

Since you have several issues that may or may not be related, and there's little real info to go on, I'd suggest doing a clean reinstall of 13.10.  Then, update the system ("sudo apt-get update", "sudo apt-get upgrade", "sudo apt-get dist-upgrade").  Reboot.  Then tackle one issue at a time.

---

### Post by grahammechanical on 2014-04-04
If you have hybrid graphics, that is both an internal graphic adapter for low intensity graphic work and a more powerful discrete graphic adapter for high intensity graphic work then you need special video drivers. And companies like Nvidia have been very slow to make a driver available for its Optimus technology. Open source developers have a very hard time writing drivers for proprietary hardware because the companies are not keen to release details of the hardware and how it works. 

For many months the only support for Hybrid graphic setups that was available from the Bumblebee project

[http://bumblebee-project.org/](http://bumblebee-project.org/)

Finally, Nvidia started to produce a driver but they have not been in any hurry.

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

Regards.

---

### Post by Zirts on 2014-04-04
Do I have this hybrid graphics?  I have no idea actually... Seems like a really alpha thing on Linux tough..

---

### Post by buzzingrobot on 2014-04-04
> **Zirts said:**
> Do I have this hybrid graphics?  I have no idea actually... Seems like a really alpha thing on Linux tough..

If your motherboard has onboard Intel video and you have added that Nvidia card, check your BIOS setup to see if it tells you which one is enabled and, ideally, allows one or the other to be disabled. (Presumably, you want to use the Nvidia.)

If you use the "Additional Drivers" tool and it shows no available proprietary drivers are available, then the Nvidia card is very likely disabled.

Hybrid graphics are common in laptops.   Ideally, when the graphic demand peaks, those operations would switch to the discrete graphics card.  When demand declines, graphic operations move back to the onboard Intel graphic chip, to generate less heat and draw less current from the battery.  Apple uses hardware in their laptops to make this switching smooth and automatic.  Nvidia provides their "Optimus" software solution for Windows.  In Linux, there is "Bumblebee" (written without access to Nvidia source) and the driver people are waiting on Nvidia to deliver.

---

### Post by pqwoerituytrueiwoq on 2014-04-04
> **Zirts said:**
> So I should not install the driver from xorg-edgers? Instead from Nvidia's home page?given you are using such a new gpu i would, probably can't get a driver a easier way, you could use nvidia's blog and reinstall it after every kernel update if you prefer
the performance will improve significantly once you get a current official drive for that card working
i have a 650 ti boost without the nvidia driver i don't even have opengl 2 which is the min required for most opensource games that use opengl

---

