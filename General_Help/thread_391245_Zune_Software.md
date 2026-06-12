---
title: "Zune Software?"
date: 2007-03-22
forum: General Help
---

### Post by cmillican on 2007-03-22
I have Ubuntu 6.10, and I recently made the full switch. The only thing (that I've thought of) that I have left to get working is managing music on my Zune. I have downloaded the software, run winecfg and added it to applications under "global settings", and when I double click the installation file, I get a "Zune Setup" error message stating, 
"Fatal Startup Error:: Unable to load the initial page:
res://Z:\home\chris\Desktop\ZuneSetup.exe/zune.htm"

Any help is greatly appreciated. I won't be on much longer tonight, so I may not respond to your suggestions tomorrow, so if I don't get to tell you later, thank you in advance.

---

### Post by hikaricore on 2007-03-23
...I'm sorry but did you actually expect Microsoft's Zune software to run in linux even with wine?

Ok now that I've gotten that out of my system I'll try and be helpful.

I couldn't find any info for you on running it with wine, but here's some hope for you:

[http://zune-linux.com/](http://zune-linux.com/)

Until then I suggest running some version of Windows on a virtual system such as [vmware]("http://www.vmware.com/products/free_virtualization.html")

(this may or may not work, but it has a better chance than Wine)

Here's some howtos:

[http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware)
[http://ubuntuforums.org/showthread.php?t=84275&highlight=vmware](http://ubuntuforums.org/showthread.php?t=84275&highlight=vmware)
[http://ubuntuforums.org/showthread.php?t=342631&highlight=vmware](http://ubuntuforums.org/showthread.php?t=342631&highlight=vmware)

---

### Post by twistedneck on 2007-05-01
Running Zune sofware in feisty with VMware XP.  Can't get USB device to connect in VMWARE.

lsusb shows device.

---

### Post by airtonix on 2007-05-01
use virtualBox instead. usb intergration is much easier...but dont expect networking to be easy like in vmware

---

### Post by twistedneck on 2007-05-01
> **airtonix said:**
> use virtualBox instead. usb intergration is much easier...but dont expect networking to be easy like in vmware

I am so close its only a matter of USB connection! i have network support, the XP Pro is working great.. shares all setup, etc..

I would requre a new XP image for virtualBox since it wont read VMware images.

I can't get anything USB to connect under vmware player, even my usb1.1 micro card reader.  Last install at least that would detect right away.

Could the network file system type be an issue? VMware is NEC networked right now i believe - wont work with default.

---

### Post by twistedneck on 2007-05-01
Solved

:guitar: 


Got the USB working (zune device) mount usbfs to the file system used by vmware /proc/bus/usb.

mount -t usbfs /dev/bus/usb /proc/bus/usb

Dont forget to disable usb 2.0 in the bios.


[http://www.zuneboards.com/forums/general-talk/2772-zune-linux-progress.html](http://www.zuneboards.com/forums/general-talk/2772-zune-linux-progress.html)

---

### Post by fakie_flip on 2007-05-08
Microshit is probably trying their best to make sure zune software does not work on Wine. Proprietary crap! Don't buy a Zune! Go for something Linux compatible. They want everyone to buy Vista!!!!!!!!!

---

### Post by strabes on 2007-05-08
Hard drive players are on their way out anyway. I've had a 20gig ipod for a few years now and the next mp3 player i'm buying is going to be an 8gb flash one of some sort that doesn't require special software to put music on. Most likely it will end up being a sansa or an iaudio.

---

### Post by everdred on 2007-05-08
> **strabes said:**
> Hard drive players are on their way out anyway. 

Not until flash gets a lot cheaper. I have a flash player and a hard drive-based player, and I use them both for different things. Neither one is capable of replacing the other -- the flash one is great for podcasts, where permanent storage isn't necessary and library-based management just gets in the way... and the other is for carrying around my entire music collection, where the opposite is true. :D

---

