---
title: "Can't start Xgl session in GNOME"
date: 2007-01-27
forum: General Help
---

### Post by Kostya on 2007-01-27
Hello fellow Ubuntonians,

This is my first post on this forums. I have been using Ubuntu on and off for a few months now. Mostly I am just learning about it and trying to figure out if I can make it my primary OS. I am currently dual-booting with Win2K and have no desire to upgrade to XP or Vista if I can help it. So far, I've been able to figure most of everything out by reading the forums and other online resources, but today I am stuck trying to get Beryl to work.

My hardware: AMD Athlon 2500+, 512MB RAM, and an older ATI Radeon All-In-Wonder (I believe it is a Radeon 7200 chipset).

I am running Ubuntu 6.10. 

I followed some instructions to install beryl packages and tried to run it. It gives a warning about 3D driver not supporting visual 0x4b (whatever that is), complains about Xgl and Nvidia being absent. Then it displays the splashscreen and my desktop goes mostly white with window borders missing, both top and bottom panels being cut off and generally not looking very hot. (see attached screenshot)

I have the “default” ATI driver installed. Do I have to install the proprietary ATI driver? (glxinfo reports “direct rendering: Yes”)

Anyway, after reading a few more posts and howtos, I figured that I need to run Xgl session first. I followed the  instructions to install it and made a script to start Xgl session, however every attempt to start Xgl session fails. I either get an error (something about no display found) or it just kicks me back to login screen without any info. My startxgl.sh file is:

```

#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
exec gnome-session

```

I am not sure where to go from here and what to try. Any ideas would be greatly appreciated.

Thank you in advance.

---

### Post by jbayone on 2007-01-27
I'm pretty sure you have to install the proprietary driver.  I use Nvidia though, so I'm not sure.

---

### Post by igknighted on 2007-01-27
The error about not supporting 0x4B is normal.  This basically means the driver doesnt fully support beryl (which the open source driver doesnt), but all that *should* happen is that the rain plugin wont work.  Sounds more like a buggy Beryl than a vid-driver issue.  Try using a different version of beryl.

That said, if you want to try fglrx+XGL you will get better performance.  I went from 20-80 fps on my x800 w/ the open source driver to >500 fps w/ fglrx (as measured by the beryl benchmark blugin).  I suggest going to the sticky at the top of this forums, finding the proper category in the beryl thread and following those directions precisely.

One last note, that sounds like an old chipset, you may need to use the legacy drivers.  Make sure you get a version of fglrx that supports your card.

---

### Post by Kostya on 2007-01-27
Thank you for the ideas, guys. 

Apparently, my video card is so old that no proprietary ATI drivers are available for it (at least my card is not listed on their web site for Linux drivers). I tried it anyway (following this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)), just in case if it magically works but the driver could not find any devices to work with, so I reverted back to “ati” driver.

Shouldn't Xgl session work with any video driver? I mean everything else seems to works great with the “native” driver that I use now.

---

### Post by Kostya on 2007-01-28
After some more research into my issue I am now convinced that I don't need Xgl or the proprietary drivers. My chipset (Radeon 7200) appears to be fully supported by the open source ATI driver and should work with AIGLX. At least, this appears to be the claim that this article makes: [http://www.freesoftwaremagazine.com/node/1797](http://www.freesoftwaremagazine.com/node/1797). However, I am still experiencing white windows, missing borders and other strange effects when I run Beryl (see the screenshot attached to the first message). 

I've noticed that if I switch to a lower resolution (I normally run at 1600x1200) I get slightly better behavior when I run Beryl. For example, my panels don't get cut off but most of the other problems remain. I've tried everything I can think of but I am not making any progress...

---

### Post by Kostya on 2007-01-29
Just FYI: I've tried to run Compiz instead of Beryl and it produces pretty much the same results: white screen, missing borders and so on...

I am giving up on trying to get Beryl to work.

---

### Post by Waappu on 2007-01-29
Hi

I didn't get my ATI 9250 work with XGL. But open source driver and AiGLX works great.

I have make script for install beryl if you want try one more time
[http://ubuntuforums.org/showthread.php?t=338771](http://ubuntuforums.org/showthread.php?t=338771)

---

### Post by Kostya on 2007-02-03
Thank you Waappu.

I did not try your script since I have already installed Beryl. However, I was finally able to get Beryl to work by adding

	Option "AGPSize" "32"

to "Device" section of my xorg.conf

---

### Post by jeff419 on 2007-02-09
sudo apt-get install xserver-xgl

ctrl+alt+delete

In the bottom left hand corner it says options.  Click there, and click sessions.  Select xgl, and sign in.

---

