---
title: "[SOLVED] Twinview and where is the love"
date: 2008-05-07
forum: General Help
---

### Post by ktechman on 2008-05-07
I need help setting up my xorg file with my current sceens are there any takers out there brave enough to dive into the deep end of the pool. Need some advice please.
             Regards

Linux-x86_64 Driver 169.12
GeForce 7600 GS
Acer P191W (DFP-0)
Vizio 32 (VIZ VX32L HDTV10A (CRT-0))
AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
2.6.22-14-generic

---

### Post by feest on 2008-05-07
well if you're lucky you don't need to modify your xorg.conf it seems your having an nvida card so you can do these steps to get some result:

install the nvidia-setttings package
plug in both your screens
run sudo nvidia-settings
set up your screens in twinview mode
save to xorg.conf
restart xserver

does this work?

---

### Post by Bakon Jarser on 2008-05-07
I think nvidia-settings is installed by default when you install the restricted driver.  Look under system > administration > nvidia x server settings.  be sure you click the save to x button when you have things the way you want them.

---

### Post by ktechman on 2008-05-08
Thank you for the reply.  I have tried to use the nvidia settings and it wants to uninclude the 1440x900 metamode and that is what my primary screen runs with (16:9) and it also changes my primary screen to the 32" Visio, which to say the least is very confusing. Also, my xorg file dosen't show half of the info that I've seen on other posts and the linux explanation given by nvidia on setup is over my head ( [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-g.html](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-g.html)). Most every post I've seen deals with metamodes and pretty specific info about their card and screen resolutions.  Please forgive me for taking so long to reply after banging my head against the wall for a week on this issue I'm pretty much burned out and sometimes you have to walk away.  I probably have something messed up because everyone else has had a resolution. The reason I suspect this is because I was booting with the 32" visio and now it just goes black. The only thing left for me to do is to start removing software and start over If I have to reload ubuntu I will (already done it 3 or 4 times) my wife hates it but I can't please everyone. But I don't have any idea where to start.

---

### Post by Bakon Jarser on 2008-05-08
I'll start off by saying that if you do another reinstall you can save yourself a little time.  If you enable viewing hidden folders in Nautilus you will see a lot of folders labeled .(program name).  If you back these up then paste them into your home folder you won't lose any settings you had for those programs.  I personally have my home folder on a seperate partition so that when I do a reinstall all of my configuration files for my programs are already there.  That can be a big time saver and maybe not make your wife so mad.

As for your problem I probably won't be able to help you but others who may will probably need more information.  It's unclear what exactly you are trying to do.  Are you trying to do an extended desktop, two seperate desktops, or twinview?  It would probably also help to post the contents of your xorg.conf file.

---

### Post by ktechman on 2008-05-08
I solved the problem earlier today and forgot to update thank you for your help this thing had me going for a while.

---

