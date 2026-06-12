---
title: "Vector NTI, SuperPro dongle"
date: 2007-01-09
forum: General Help
---

### Post by misha680 on 2007-01-09
Just a quick question. I have helped two people in my lab (molecular biology) install Ubuntu on their computers, and would like to eventually be able to use Ubuntu on all the lab computers, but I have run into two major software hurdles that I cannot seem to overcome and would appreciate any input my fellow forumers might have. Specifically, these are the two problems:

1) Vector NTI is a program that we would require to use should we have Ubuntu on our lab computers. It is available for free download for non-commercial use here: [http://download.invitrogen.com/evergreen/Vector%20NTI%20Advance%2010.exe](http://download.invitrogen.com/evergreen/Vector%20NTI%20Advance%2010.exe)
I tried and tried but I can't even install the thing under wine (tried winetools, CVS version of wine, posted a Wine bug, etc.). If anyone has had any luck with running Vector NTI other than in VMWared Windows I would appreciate any input.

2) We have a Kodak GelLogic imaging system with the Kodak Molecular Imaging software. It seems to install and run fine under wine, but the dongle it uses for copy protection, it's a SuperPro (I think it's "Sentinel SuperPro" but anyway it's the first thing that comes up if you google superpro) and the wined Kodak doesn't seem to see it. They have an RPM on the SuperPro site for some version of Red Hat Enterprise, and I have tried aliening it, installing it, and even tweaking with the scripts to start the usbdriver, but as far as I can tell either the usbdriver isn't doing anything (the program is running, but I don't know how to see if it is really doing anything) or it is not interacting properly with the wine'd Kodak Molecular Imaging software (although I read somewhere that the dongle software communicates through TCP/IP so in theory it should work). I know this dongle is used for a lot of other programs (just do a google search for it), so I wonder if anyone has a solution.

Thanks on both fronts. I am stumped right now, although quite impressed with what wine _can_ do.

Misha

p.s. I know there are some Vector NTI-like suites for linux, like EMBOSS, but from my experience playing around with EMBOSS none are quite as user-friendly as Vector NTI, although if someone knows a nice GUI-based one that I could try I would be open to that on that front.

---

### Post by misha680 on 2007-01-26
Alright, solved the Vector NTI installation problem. Vector NTI seems to work great with Wine. See [here]("http://www.ubuntuforums.org/showthread.php?t=347095") for more info and the script.

Misha

---

### Post by nanonils on 2008-04-27
> **misha680 said:**
> Alright, solved the Vector NTI installation problem. Vector NTI seems to work great with Wine. See [here]("http://www.ubuntuforums.org/showthread.php?t=347095") for more info and the script.

Misha

O my god! Vector NTI is now free and can be run with Wine!? That's incredible! You have just deprived me of the last reason not to install Ubuntu!

I am still in shock about how great Ubuntu 8.04 is and how easily things can be troubleshot thanks to the linux forums and excellent documentation. I tried it out on my wife’s Compaq Presario V3000 after I decided to kill XP because all the bloatware snug up again ("Vongo", etc), even the lightest antivirus, anti-spyware and firewall programs really slowed the system down and Gnome is now blazingly fast! I can’t believe that most the maintenance tasks and flaws we are concerned with as Windows users are essentially intentionally left in place to maintain business: none of them are needed under Linux!

Figure that: I bought a $2200 Lenovo T61 with Vista Ultimate and it seems that I'm back to the old Win95 times: key system services just won't run despite my desperate attempts for months (e.g. event log service). As a result Lenovo programs won't run either (DiskKeeper). I continue to get the blue screen of death (BSOD), the computer slows down after repeat suspend till it BSODs on me, the wireless network manager crashes after each suspend and cannot be restarted meaning that I have to reboot each time I stop something for a few hours. Office 2007 looks good and the new interface is actually nice (once you get used to it) but it too, crashes inexplicably! This has wrecked havoc with my PhD thesis, a 350 page document with a ton of big graphics. When I run it on my wife's laptop in OpenOffice it is as fast as if I were scrolling an ASCII text with 2 pages! It is ridiculous! Office 2007 also has a problem with the screen refresh when I scroll even only moderately large documents. It fills the screen with horizontal stripes of the text I was looking at and won’t refresh or go away.
I figure if it takes me that much effort to get my most basic stuff done, then I can as well switch a totally new operating system.

My only concerns are now to find Linux replacement for:
iTunes (I’ve got an iPhone) – perhaps Wine will make it work.
Endnote – perhaps Wine or just using their online subscription version? No good Linux replacement that I know of.

- Posted from my Lenovo T61 running Wubi Hardy!

---

