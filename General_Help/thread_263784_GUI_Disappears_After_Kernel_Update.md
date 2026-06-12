---
title: "GUI Disappears After Kernel Update"
date: 2006-09-23
forum: General Help
---

### Post by odelay on 2006-09-23
OK...I decided to install the new Linux SMP Kernel (.27 I think) that appeared in the auto-update section.  I mean, if Ubuntu starts up each time and bugs me to install something, it should be safe, right??  So I uncheck all the non-SMP and image kernel stuff (if you haven't realized it yet, I'm pretty new to Linux and I'm completely in over my head right now).

I *did not* check to install the new ATI drivers.  Sure enough, upon restarting, the bootloader now has the choice between Ubuntu .26, Ubuntu .27, and my WinXP partition.  I select .27....and BAM!  No longer any GUI.  It mentions something about going to wiki.x.org and says some other stuff that are way beyond me.  So I'm not stuck at a prompt and 30-something hair-pulling, overwhelmingly frustrating hours of work/customization seem to be down the drain.

I read around, and found a troubleshooting doc here ([http://psychocats.net/ubuntu/nox)](http://psychocats.net/ubuntu/nox)).  But come on...I can't do that.  I don't even understand what it does, and I guess I'd need to dig up or reburn another Dapper CD.

I've never been so frustrated in my life with a computer (hey, I grew up with Mac OS's...I'm used to things "just working").  I've spent soooo much time setting up Ubuntu, that reinstalling it is not an option.  What I'm the most frustrated about is why is something that could easily screw up your computer being advertised so forcefully in the auto-update menu??!!?  I mean, first of all, it's showing all these kernels I don't want (I'm on a dual core Dell e1505), along with some other stuff I probably don't want.  I mean, the auto-update section is for newbies, right??  So it shouldn't be too easy for me to screw everything up, right?! Ahh...sorry, I'm getting frustrated.

So, is there anything I can do, or is my bout with Ubuntu at an end?  Thanks for your help...I'm really in need of it now.  If you need more info, just ask.

---

### Post by Corp_Punisher on 2006-09-23
Hey Odelay.

I haven't updated the kernel yet. I did read this thread about problems and how to remedy them:

[http://ubuntuforums.org/showthread.php?t=213420](http://ubuntuforums.org/showthread.php?t=213420)

It's the first "Pinned" thread in the General Support section.

It's about 7 pages long, but about halfway through there is some helpful info in how to actually get into a Recovery Mode and login. I believe it's ctrl+alt+f3 (it should bring up a terminal even if the GUI crashed and allow you to login at a prompt).

Follow the advice for booting into your previous kernel, which will bring up your desktop. Then follow the advice about the Metapackages and or Video Drivers.

In your case, it may be a simple matter of reinstalling your Vid Drivers themselves, which you can do in the terminal in recovery mode.

I would try the Vid Driver solution first, then check your Metapackages.

---

### Post by Pelekophori on 2006-09-23
Odelay:  

I also lost my GUI this afternoon after installng the kernel update.  When I rebooted, I got an error message to the effect that the X-server was broken.

Running: ```
sudo dpkg-reconfigure xserver-xorg
``` from the shell fixed it.

---

### Post by odelay on 2006-09-23
OK.  I seem to have mostly fixed it (that is, I now have a GUI and everything looks fine).  

First thing first, it is ABSOLUTELY TERRIBLE that this was released as an auto-update.  As a Linux newbie, this makes me want to wash my hands of all this and never look back.  Honestly, that is what any rational person would do.  I just wasted 8 hours (on a day that I couldn't really aford to do so) on something that never should have happened.  I do have to thank everyone in the community who tried to help everyone through this.  Why is the update still posted available--hasn't it been weeks?!?!

Second, what did I do to fix it?  Assuming you can get to the prompt, follow the excellent instructions on the top of this page.  [http://ubuntuforums.org/showthread.php?t=241254&highlight=xorg-core](http://ubuntuforums.org/showthread.php?t=241254&highlight=xorg-core)

Once I did that, I still couldn't get x to start, so i reinstalled the ATI drivers.  I followed the top instructions here.  [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Problems_with_module-assistant](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Problems_with_module-assistant)

Restarted and it seemed to work.

My actual question now is what do I do with the .26 kernel?  I applied all this stuff to the new .27 kernel, but I still have the Bootloader options of choosing either Ubuntu with Linux .26 or Ubunti with Linux .26 (Recovery Mode)--in addition to the .27's.  
•Should I try uninstalling the 2.6.15-**26**.47 Linux kernel image now with Synaptic Package Manager?  
•What is the difference between the Linux Kernel and the Linux Kernel Image?  
•What are the Linux-headers?  
•Restricted-modules?
•Keep in mind my listed installed kernel is linux-686-smp 2.6.15.25

90% of these problems happen because people don't understand what (more importantly why) they are doing what they're doing.  People mostly say copy this code here, press enter, etc.

Anyway...thanks for any help.

---

### Post by jocko on 2006-09-24
Here's an answer from one newbie to another:
The **linux-image-2.6.15-x-y-NNN** (NNN = 386, k7, 686, k7-smp or 686-smp) is the actual kernel package. **linux-restricted-modules-2.6.15-x-y-NNN** contain proprietary kernel modules (like ati's fglrx driver).
**linux-headers-2.6.15-x-y-NNN** is needed if you want to compile programs or drivers yourself, i.e if you install ati's fglrx driver from ati.com instead of using the pre-compiled one from the repos.

There are also a few packages you need to make sure the above packages are always kept up to date.
**linux-NNN** makes sure you always have the latest version of the **packages linux-image-NNN** and **linux-restricted-modules-NNN** (and those two packages makes sure the packages linux-image-2.6.15-x-y-NNN and linux-restricted-modules-2.6.15-x-y-NNN are up to date).
If you need the kernel headers for your kernel the package **linux-headers-NNN** will keep it up to date.

I think there are a few things you can do to avoid things like this from happening in the future.

1. Make sure you have the package **linux-NNN** installed. When an upgrade to the kernel hits the repos, synaptic will keep it from being installed before the restricted-modules are available.

2. **Don't** install ati drivers from ati's website, use the ones in the repos instead (xorg-driver-fglrx). It will always have the correct fglrx-module built for your kernel in the restricted-modules package. If you install from ati's website, you will **always** loose the GUI and need to re-install the drivers for the new kernel. (I guess this would also be true for nvidia drivers).

3. Even if you have the linux-NNN package installed, the developers may sometimes make mistakes that makes a new kernel install without the corresponding restricted-modules (if I'm not mistaken I think this happened a few weeks ago). So every time you see there is a kernel upgrade waiting, check that there is also a restricted-modules package with the same version number before you allow it to install.

Also: It should be perfectly safe to uninstall the older kernel versions as well as the older restricted-modules and headers. But when a new kernel is installed, I think it is best to keep the old one until you know the new one is working.

Hope this helps.

---

### Post by odelay on 2006-09-24
Absolutely what I was looking for!!!  Thank you so much.

---

