---
title: "Boot lockup after nVida video driver upgrade."
date: 2013-12-22
forum: General Help
---

### Post by skitter on 2013-12-22
I'm running Ubuntu 12.04.3  The 'good' and 'bad' drivers are in the additional drivers applet. Tried recovery console, but safex is locking up. Fortunatly (I think) I am able to boot and access and write to the troubled hard drive using a live CD. I'm hoping there's a file or two that tells my PC to use the older driver.  Can someone help me make some config changes using the live CD to bring the machine back to life?

---

### Post by Bucky Ball on 2013-12-22
*Thread moved to **General Help**.*

... until we can work out what the actual question is. 

Ambiguous. Good and bad drivers? Safex? Troubled hard drive?

What is the actual problem? The thread title indicates you have upgraded your graphics driver and now have problems, but you don't tell us from what driver to what driver you have upgraded and a troubled hard drive appears. I, for one, do not follow. ;)

Boot lock up? When you switch on the machine could you tell us exactly what is happening, at what point during the boot (how far do you get), any error message(s), what you've tried at that point to remedy.

Do you get to a menu list where you can pick a kernel to boot before any of this happens?

---

### Post by skitter on 2013-12-22
Sorry about the confusing post.  It was very late when I wrote that.  Hopefully this attempt will make a bit more sense. 

I upgraded the nVidia video drivers.  I don't recall the versions at the moment. I do know that I selected the most recent drivers with updates, and used the 'additional drivers' application in 'system settings'. I have a gtx 275 video card if that helps.

After rebooting with the new driver installed, the system freezes. The last line is 'stoping sending an event to indicate plymouth is up.'  Here's a screen shot- [http://imgur.com/T1BGIzK](http://imgur.com/T1BGIzK).

I can get into the boot menu, it looks like this- [http://imgur.com/u7WxgjK](http://imgur.com/u7WxgjK) I can then choose failsafex- [http://imgur.com/2etOVVP](http://imgur.com/2etOVVP)  but then I end up with a blank screen with nothing other than a flashing cursor in the top left corner.

I did find that I can boot from the live CD, and access the drive that is no longer booting. I'm hoping there's some way to roll back the driver change I made using the live CD.

---

### Post by egeezer on 2013-12-22
A number of us have had similar problems - you might take a look at this long thread:

  	 	 	 	   [http://ubuntuforums.org/showthread.php?t=2194584](http://ubuntuforums.org/showthread.php?t=2194584)

or this even longer one:

  	 	 	 	   
[http://ubuntuforums.org/showthread.php?t=2193029](http://ubuntuforums.org/showthread.php?t=2193029)

---

### Post by skitter on 2013-12-22
Thanks egeezer.  That got me to the point where I can back up my home folder to a USB drive, so I can reinstall if all else fails.  For the life of me I can't figure out how to switch back to the old video driver / use a generic driver- it seems that the fixes in those threads require at least being able to boot to the command line (or I'm missing something). If there are any other ideas, I'd really appericate it as reinstalling all of my apps isn't something I'm looking forward to.


edit- poked around the log files and found this, in case it helps.

kern.log
Dec 22 11:26:00 blocky kernel: [   15.483551] NVRM: API mismatch: the client has the version 319.32, but
Dec 22 11:26:00 blocky kernel: [   15.483551] NVRM: this kernel module has the version 304.108.  Please
Dec 22 11:26:00 blocky kernel: [   15.483551] NVRM: make sure that this kernel module and all NVIDIA driver
Dec 22 11:26:00 blocky kernel: [   15.483551] NVRM: components have the same version.
Dec 22 11:26:00 blocky kernel: [   15.785471] NVRM: API mismatch: the client has the version 319.32, but
Dec 22 11:26:00 blocky kernel: [   15.785471] NVRM: this kernel module has the version 304.108.  Please
Dec 22 11:26:00 blocky kernel: [   15.785471] NVRM: make sure that this kernel module and all NVIDIA driver
Dec 22 11:26:00 blocky kernel: [   15.785471] NVRM: components have the same version.

Xorg.0.log
    "Default Screen Section" for depth/fbbpp 24/32
[    15.316] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    15.316] (==) NVIDIA(0): RGB weight 888
[    15.316] (==) NVIDIA(0): Default visual is TrueColor
[    15.316] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.316] (**) NVIDIA(0): Option "NoLogo" "True"
[    15.316] (**) NVIDIA(0): Enabling 2D acceleration
[    15.338] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    15.338] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    15.338] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    15.338] (EE) NVIDIA(0):  *** Aborting ***
[    15.338] (EE) NVIDIA(0): Failing initialization of X screen 0
[    15.338] (II) UnloadModule: "nvidia"
[    15.338] (II) UnloadSubModule: "shadow"
[    15.338] (II) UnloadSubModule: "wfb"
[    15.338] (II) UnloadSubModule: "fb"
[    15.338] (EE) Screen(s) found, but none have a usable configuration.

---

### Post by egeezer on 2013-12-22
On the last page of the second link above, in post #115, I gave the commands I ran to get my system back in shape.  At the bottom of your boot menu screen, it should give you the option "press c for a command line", where you can do the jockey-text trick.

---

### Post by skitter on 2013-12-22
Thanks again. Still running into a wall though.  From the grub boot menu, I can press c to go to command line. It brings me to a grub prompt. The problem for me now is the jockey command isn't recognized. If I press [tab] on a blank line, I'm show a (brief) list of all available commands- jockey isn't in the list (or anything that starts with j for that matter).  Is there a way to install jockey, or make it available from the grub prompt?

---

### Post by steeldriver on 2013-12-22
You need to be able to boot at least to the "recovery mode" of the actual OS (not grub) in order to run the jockey-text command - if you can't boot into recovery mode then it *may* help to press 'e' (rather than 'c') and edit the boot command to add the 'nomodeset' option - see the instructions here --> [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) - scroll down to **How to temporarily set kernel boot options on an installed OS (not wubi)**

---

### Post by skitter on 2013-12-22
Thanks for the suggestion, but still no luck. Doing the 'nomodeset' trick gets me back to a locked up system with the 'stoping sending an event to indicate plymouth is up.'  It's starting to look like I'm  not going to be able to recover the system with out reinstalling the OS :(

---

### Post by steeldriver on 2013-12-22
what happens at that screen if you press the Ctrl-Alt-F2 combo? does *that* get you to a command line login prompt?

---

### Post by skitter on 2013-12-22
Ctrl-Alt-F2 does nothing. The machine doesn't seem to respond to the keybord at all.

edit- I'm reinstalling Ubuntu now. If anyone has a suggestion regarding how to avoid this in the future (short of never upgrading nVida video drivers) I'd love to know what I can do to safeguard against such a disaster.

---

### Post by Bucky Ball on 2013-12-23
Try this:

* When you boot and get to the list of kernels, select your kernel and type 'e' to edit it;
* At the end of the kernel line that ends in 'quiet splash', or just one of those words, leave one space and type 'nomodset' (without apostrophes);
* Follow instructions at the bottom of the screen to save that change and proceed with boot.

That may by-pass the nvidia driver and get you into a desktop with low-res graphics so you can change the driver. 

Good luck. ;)

* Oh, just noticed you are reinstalling! Drastic, and you may have the same issue's all over again, but I guess you'll need to experiment.

---

### Post by travis-falkenberg on 2013-12-23
I had a similar problem with 12.04 but I could at least boot to the recovery console to fix it. 

Do not upgrade to the NVidia 319 driver in 12.04 unless you upgrade to kernel 3.8 which is available in the normal 12.04 repository.

---

### Post by skitter on 2014-01-01
So... it's been over a week after the reinstall, and the PC is running like a champ. The application reinstall wasn't all that bad since I did it after restoring the home folder.  Now I see that in my rush to get a working system back, I 'steped in it' again- I installed 32 bit instead of 64. I'm not going to even think about in-place upgrade from 32 to 64, so any toughts if it's worth the ~4 hours to reinstall the 64 bit version?  I have an Intel i5 with 16 GB RAM if that matters.

---

