---
title: "X server error for wubi"
date: 2007-12-01
forum: General Help
---

### Post by tototime on 2007-12-01
Hello all im a complete newbie when it comes to linux so i tried wubi and it worked great it tried to boot and it almost did when this popped up with a blue screen and weird letters


Failed to start the x server (your graphical interface). It is likely that it is not setup correctly. Then it says to diagnose the problem click yes and a bunch of stuff about it comes up but no real help. When i say ok and then no. It brings be back to the boot menu and says 79.228000 bcm43xx:Error:Microcode bcm433xx_microcode.fw not available or has failed.  Then it keeps repeating this and it wont let me boot any ideas?

---

### Post by ago on 2007-12-03
ctrl+alt+f2
sudo dpkg-reconfigure xserver-xorg

select vesa for the time being

---

### Post by syn4k on 2008-02-14
No, sorry. That does not work. It may work for you but it most certainly does not work for this.

I have googled around for HOURS; in fact, days and have found 0 articles that give the information necessary to fix this issue. I have been to about 120 websites and have spent MUCH time looking and reading and testing and trying and trying and trying...and trying....and again and NOTHING works. 

I did find one day that I was able to perform del /f/q/s \*wubi* in the command line after using the Add/Remove application to remove wubi. This fixed it so that I could reinstall the application however, after rebooting I was met with the most annoying greeting; the error was back.

I have tried to install Ubuntu using the 4.0 regular, 4.0 alternate, 7.0 and 7.0 alternate CDs all of which error out because of some TTY FOOLISHNESS being turned off. I cannot tell you how PISSED I am.

---

### Post by syn4k on 2008-02-14
Oh and one more thing...ALL of the tutorials that I've found (probably around 60 or so that I've read and tried) to enable TTY job control are completely inaccurate and DO NOT WORK. :(( HOW ABSOLUTELY LAME

---

### Post by ago on 2008-02-15
The tty message you see is misleading, you can ignore that.

The important fact is that something fails BEFORE and you are down to a console. There may be several reasons for that. You need to boot in verbose mode and or look at the log. 

For instance if you use wubi 8.04 rev 420 with ISO as of today, you have to change the boot parameters manually (c/ubuntu/install/boot/grub/menu.lst) or you cannot boot as explained in the other thread, if you don't change the parameters, you will end up in a console. 

All that will stabilize with Alpha 5 release, so if you want an easier ride (as far as alphas go...) you might want to wait.

---

### Post by sbentjies on 2008-12-19
> **ago said:**
> The tty message you see is misleading, you can ignore that.

The important fact is that something fails BEFORE and you are down to a console. There may be several reasons for that. You need to boot in verbose mode and or look at the log. 

For instance if you use wubi 8.04 rev 420 with ISO as of today, you have to change the boot parameters manually (c/ubuntu/install/boot/grub/menu.lst) or you cannot boot as explained in the other thread, if you don't change the parameters, you will end up in a console. 

All that will stabilize with Alpha 5 release, so if you want an easier ride (as far as alphas go...) you might want to wait.
I have had similar problems with a "legacy" nvidia card and Wubi. Is there any real difference between Wubi and a fully partitioned version? I have tried reconfiguring X using different parameters in the xorg.conf and still nothing above 800x600 on an unknown monitor. This is frustrating. The card is an nvidia TNT2. The release with Wubi is 8.10, Intrepid Ibex

Thanks,

---

