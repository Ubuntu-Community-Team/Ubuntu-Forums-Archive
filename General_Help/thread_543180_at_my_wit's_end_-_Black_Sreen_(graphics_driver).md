---
title: "at my wit's end - Black Sreen (graphics driver?)"
date: 2007-09-04
forum: General Help
---

### Post by dingo8baby on 2007-09-04
Ok, first, let me give you my entire system specs:
Gigabyte M55SLI-S4 motherboard
AMD 64 X2 3800 dual core cpu
2 GB OCZ platinum series DDR2 800 RAM
2x Asus EN7600GS Silent 256MB PCI-E graphics cards in SLI 
ATI TV Wonder 650 pci
Samsung Syncmaster 941BW
Buffalo WLI-TX4-G54HP Ethernet converter (connected to onboard ethernet port)

also HDDs and optical drives

I started by trying to install linuxmce, which i gave up on due to black screen problems i could not solve. I figured i could install ubuntu, get the right graphic setup, then install kde to run kubuntu, then install linuxmce from there. Alas, i can not figure out or solve this black screen issue.
The symptoms: the gdm shows only a black screen, when the gdm starts, i can hear the startup sound, so i know it's loading, just not displaying. same thing with kde when i had kubuntu installed.
what i've done:
I had to install ubuntu with the alternative text cd, because the live cd gave me the same black screen and i was unable to install that way.
i stopped gdm from the command line, reconfigured xserver-xorg, tried switching to vesa, didn't work-still have black screen after restarting gdm.
i ran apt-get to update, upgrade, dist-upgrade, and also install nvidia-glx
i then tried configuring xorg to nvidia(now available after install nvidia-glx), and now, when i restart gdm, i get a black screen AND i can't get to the command line by pressing alt-ctrl-F1. I've tried everything i've seen and now have no idea where to go from here. please help! 
thanks!

---

### Post by dingo8baby on 2007-09-04
anyone have any ideas?

---

### Post by dingo8baby on 2007-09-05
can anyone tell me if this will help my situation?
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)
if i download and install this driver, will it hurt or help my situation? i want to try this out, but i'm afraid i might make things worse. plus, the instructions are made for someone with considerably more knowledge of linux than i have, so i'm afraid i'll screw something up. any advice would be welcome.

---

### Post by srunni on 2007-09-05
If you have Windows as well on your box, you can try installing an ext3 driver for it ( [http://www.fs-driver.org/](http://www.fs-driver.org/) ) and looking through the logs to see exactly what the error is, or try the same from a Linux Live CD. Sorry I can't help you more, but hopefully this is a starting point.

---

### Post by maharbA on 2007-09-05
I think you need a fresh (un-updated) install of Kubuntu 7.04 to install LinuxMCE onto.

Was your first attempt to install LinuxMCE from the DVD or the 2 CDs?

If it WAS the DVD install, try installing Kubuntu 7.04, then LinuxMCE (without updating anything). I wouldn't bother trying to install Ubuntu, then KDE, then LinuxMCE -- let alone trying to fix Ubuntu in order to install KDE and LinuxMCE.

So ... download a Kubuntu 7.04 ISO file, then immediately install LinuxMCE ... that's my advice, for what it's worth.

PS: ATI video cards are a PAIN, I know. That tutorial seems to be for Fedora Core, rather than Ubuntu. I'm not sure about Kubuntu, but Ubuntu 7.04 comes with a restricted-driver-management tool that should get things working. But with ATI, you may have to accept less that terrific graphics in LinuxMCE -- check their support site/forums/wiki to see how they deal with ATI video cards.

I hope this helps, dingo

---

### Post by dingo8baby on 2007-09-05
thanks for the replies!
When i installed linuxmce, i used the dvd. i didn't have ubuntu installed prior to that. i did do a fresh install of ubuntu, first i tried the live cd, and when i got the black screen errors there, keeping me from installing it, i downloaded the alternate text install cd and installed that way. i still had no luck, the black screen still thwarted me. so i'm not sure how a fresh install of kubuntu would help.. isn't the core the same as ubuntu, only with kde instead of gnome? and seeing as how i had the same problem with kde when i tried linuxmce, i think i'm just going to run into the same problems. 
btw, the ati card isn't my graphics card, it's just my hdtv tuner. i have the two 7600gs' in sli, which i have a hunch might be the problem, but i've read that linux supports sli, even though there's little need for it.

---

### Post by dingo8baby on 2007-09-05
> **srunni said:**
> If you have Windows as well on your box, you can try installing an ext3 driver for it ( [http://www.fs-driver.org/](http://www.fs-driver.org/) ) and looking through the logs to see exactly what the error is, or try the same from a Linux Live CD. Sorry I can't help you more, but hopefully this is a starting point.

i can look at the logs using nano from the command line, if i know what the log files are named. any advice? then maybe i can post any error messages and that could help you guys figure out what is wrong.

---

### Post by dingo8baby on 2007-09-05
ok, i solved it! it was due to the sli.. sorta. somehow, when ubuntu installs, x is set up with the wrong bus number for my graphics card. i suppose since there are two, it choses the lower number by default? anyway, it was set up with 4 as the bus number, when it needed to be 5. changing that in xorg completely fixed the issue! i'm now going back to the linuxmce install dvd and applying what i know to it. thanks for your help guys!

---

