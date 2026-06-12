---
title: "Garbled video w/NVidia GeForce 6150"
date: 2008-04-27
forum: General Help
---

### Post by tomcat2007 on 2008-04-27
Since installing Hardy (both the 32 and 64 bit versions) and enabling the restricted video driver, the video, when shutting down or returning from screen saver is garbled.  Sometimes it is distorted just enough to discern what the output is intended to be, other times it's just some gray on black vertical smudges.

Didn't have this problem in Gutsy.  

Have an NVidia GeForce 6150 Go (product C51) driving a 1440x900x16&24 bit laptop monitor.  Am NOT using Compiz this time around.

Not sure what other information is necessary for someone to make an educated guess as to what is wrong or propose a solution.  Assistance is greatly appreciated.

---

### Post by arisystems on 2008-04-27
I installed 8.04 64-bit on an E-machine AMD 64 with the GeForce 6100 chipset and had a similar problem. The system installed and booted fine, but when I went to activate the restricted drivers, I ended up with badly distorted screen.  When I went to uninstall the drivers, I received an abort error (2 I think) that these drivers would not uninstall.  After reading the forums on this problem, it was suggested to open synaptic and search "envy" and choose the top two drivers and install.  I did this after another fresh install (I had the time) and then when I enabled the driver, it still downloaded yet another driver, but then it worked perfectly.  I admit, I never did this under previous releases, but in the future, I will simply download the top two "envy" drivers first and, then enable the restricted drivers in the panel.  Not sure if that helps you, but I know that the restricted driver will work properly for the 6100 series chipset.

---

### Post by foosean010 on 2008-04-27
I have seen this issue on many forums, and I know what the fix is... we have to use the 100.19.*.* drivers from Nvidia.  My problem is, I just don't know how to do that in Ubuntu. 

I have an HP dv9000 with the GeForce Go 6150 video drivers as well.  If you try to switch to one of the virtual terminals (<ctrl><alt><f1-f6>) you get the same output.  This is when I use the *new* drivers in the package manager in Kubuntu. If I use the middle one, not the *new* or *legacy* drivers, I do not get those problems except when booting up, but I cannot use any compiz fusion effects, and it does not let me see what drivers I have installed.

Any ideas?

---

### Post by tomcat2007 on 2008-04-28
Something else I have noticed (with infuriation and chagrin), touchpad tapping is now permanently on, the touchpad tab on the mouse applet is gone, and the MaxTapTime option has no effect.  This occurred after uninstalling the new NVidia GLX which also had the effect of permanently downgrading my display from 1440x900 to 1024x768.  I'm reinstalling Gutsy for the time being.

---

### Post by tomcat2007 on 2008-04-29
Just an FYI, after installing Gutsy, all the features that were having issues are back to working just fine.  Guess Hardy just needs some burn-in time in production to get the kinks out.

---

### Post by Kleiton.ps on 2008-05-02
Hi Friends, I have a same problem in my computer with same video card, after installing the driver of video on the screen he is all distorted. 	
I did the procedures informed the topic, but not satisfied.

I am already using the Ubuntu 8.04

Someone could help me?

Kleiton Santos 
Brasil RS,

---

### Post by foosean010 on 2008-05-04
Yea, same issue with any version of Linux that I have installed on my laptop.  The only fix for the issue that I have found was to install the 100.14.*.* version of the Nvidia drivers.  The *new* version is 169.*.* version that DOES NOT WORK with the GeForce Go 6150 graphics card.  My only problem is that I do not know how to properly install the 100.14.*.* version of the drivers properly in Ubuntu/Kubuntu.  I found this out installing and running through the forums at Sabayon.

If anyone has any ideas or any moderator sees this, please help!!

---

### Post by cvanes on 2008-05-14
I had the same problem with Hardy and my GeForce Go 6100 where the screen was garbled resuming from the screensaver or by switching between virtual terminals and the desktop. You can install the older nvidia driver (nvidia-glx) through synaptic or by running 

```
sudo apt-get install nvidia-glx
```

Either way the package manager will uninstall the newer driver automatically. After doing this I still have my 1440x900 resolution and 3d acceleration and compiz both work as they did with Gutsy. Just make sure not to enable the newer driver again through the restricted drivers manager.

---

### Post by foosean010 on 2008-05-15
Have you had any luck getting to any of the TTy's  (ctrl + alt + [f1 - f6])????

---

### Post by cvanes on 2008-05-16
Yeh, I can access them all fine, everything seems to be working as it should. Can you not access them?

---

