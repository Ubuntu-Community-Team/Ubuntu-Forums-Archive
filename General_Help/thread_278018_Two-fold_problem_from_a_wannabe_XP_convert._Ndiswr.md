---
title: "Two-fold problem from a wannabe XP convert. Ndiswrapper, fglrx, etc."
date: 2006-10-15
forum: General Help
---

### Post by Pope7 on 2006-10-15
Just to get it out of the way, I am a complete newbie to ubuntu or anything besides windows XP. I've heard nothing but good about ubuntu lately, and i want to try something new, something that gives me some free freedom. Anyway, i've gotten ubuntu to install, but I have two problems. 

Problem #1: my ethernet port was smashed last year, so i have no wired route to internet. I have a wireless usb device, and i've tried to install the drivers for it following this 'guide/review:' [http://lxer.com/module/newswire/view/46385/index.html](http://lxer.com/module/newswire/view/46385/index.html) 
My problem is that ndiswrapper is not to be found in synaptic anywhere. i have all the repositories enabled, but it isn't there. So my question for #1 is: is there a way to download whatever i need to get ndiswrapper on my ubuntu machine from another computer without using internet or networking at all. Such as burning a CD? If so, please give me some detailed instructions on how to do it!

Problem #2 I am running a Radeon X850 xt, which from what i read is hell to support anyway. I've been following this tutorial: [http://ubuntuforums.org/showthread.php?t=190133&highlight=x850](http://ubuntuforums.org/showthread.php?t=190133&highlight=x850) and got to basically the same point as problem #1. I can find the xorg-driver-fglrx and fglrx-control in synaptic, but when i mark it for install, it gives me this error: 
fglrx-control:
Depends: libqt3-mt (.=3:3.3.6) but it is not installable
I have all the repositories enabled, what am i doing wrong! 
Any details would help!

Thank you guys! I look forward to helping in any way I can.

Oh, i installed using the 6.06 drapper liveCd. i'm running it on a dual-partitioned drive, athlon 3800 x2, 2 gigs of ram, etc. hope it helps?!

---

### Post by yatt on 2006-10-15
> **Pope7 said:**
> Just to get it out of the way, I am a complete newbie to ubuntu or anything besides windows XP. I've heard nothing but good about ubuntu lately, and i want to try something new, something that gives me some free freedom. Anyway, i've gotten ubuntu to install, but I have two problems. 

Problem #1: my ethernet port was smashed last year, so i have no wired route to internet. I have a wireless usb device, and i've tried to install the drivers for it following this 'guide/review:' [http://lxer.com/module/newswire/view/46385/index.html](http://lxer.com/module/newswire/view/46385/index.html) 
My problem is that ndiswrapper is not to be found in synaptic anywhere. i have all the repositories enabled, but it isn't there. So my question for #1 is: is there a way to download whatever i need to get ndiswrapper on my ubuntu machine from another computer without using internet or networking at all. Such as burning a CD? If so, please give me some detailed instructions on how to do it!

Problem #2 I am running a Radeon X850 xt, which from what i read is hell to support anyway. I've been following this tutorial: [http://ubuntuforums.org/showthread.php?t=190133&highlight=x850](http://ubuntuforums.org/showthread.php?t=190133&highlight=x850) and got to basically the same point as problem #1. I can find the xorg-driver-fglrx and fglrx-control in synaptic, but when i mark it for install, it gives me this error: 
fglrx-control:
Depends: libqt3-mt (.=3:3.3.6) but it is not installable
I have all the repositories enabled, what am i doing wrong! 
Any details would help!

Thank you guys! I look forward to helping in any way I can.

Oh, i installed using the 6.06 drapper liveCd. i'm running it on a dual-partitioned drive, athlon 3800 x2, 2 gigs of ram, etc. hope it helps?!
Either you did not enable all the repositaries, or you forgot to relaod them after adding them.

---

### Post by Pope7 on 2006-10-15
When i reload it gives me this message: "Could not download all repoitory indexes." Probably because i need internet, hence i need a way to move the ndiswrapper stuff from another computer to this one.

---

### Post by pjbgravely on 2006-10-21
ndiswrapper is a kernel module and should be in your stock Ubuntu kernel. You will probably want to install  ndiswrapper-utils and ndisgtk. I am not sure if they are on the disc but you can try. ndisgtk will give you a GUI installer for your xp driver. Once you have a network up you can install the ATI drivers. Ubuntu is a bare minimum Distro with the extra programs you may want being downloaded. 

Paul

---

