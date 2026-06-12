---
title: "Edgy hibernate/screensaver crash"
date: 2007-02-17
forum: General Help
---

### Post by steveandarchie on 2007-02-17
Hello all,

I'm new to linux but I have a P4 medion laptop that I have loaded Edgy on to for my elderly dad. His sight isn't so good and he's a bit spooked by computers so I thought an uncluttered ubuntu desktop with some large icons should do it. I'm nearly there with configuring the desktop (can't get aMSN to recognise the webcam - but that's for another thread) ......

BUT when the system is idle for a while, instead of the screen fading away it has small dotted red and blue lines in a random check pattern and the computer completely locks up - only a mains power off will close it down.

I have searched but it's an odd one - any ideas?

Many thanks

---

### Post by an.echte.trilingue on 2007-02-17
Betcha its your video card.  Hibernating is messing it up.

What is your video card?

To get rid of it in the mean time, turn suspend to ram and suspend to disk off.

Take care
-mat

---

### Post by steveandarchie on 2007-02-17
Thanks mat - that would make sense. I'm afraid I don't know what the card is and without windows working on the system at the mo' I don't know how to find out, though it will be an integrated one.

I'm afraid I don't know how to turn suspend to ram and suspend to disk off:confused: I'd be grateful if you could tell me - I seem to be reading forums/articles for hours on aMSN port forwarding/ndiswrapper and wpa_supplicant without getting anywhere with any of it - a quick steer would be really appreciated.

PS - had some Duvel yesterday - magnificent:) Maybe that explains half of my problems today

---

### Post by steveandarchie on 2007-02-18
I loaded "suspend2" on to the system with Synaptic. Nothing seemed to happen, can't find any application of that name on the system but the problem seems to have been solved:confused:

---

### Post by an.echte.trilingue on 2007-02-18
Getting suspend2 to work requires that you recompile your kernel... and then you have to recompile it again every time it gets updated.  It is pretty easy to do once you get the hang of it, but it will require that you go to your dad's place and physically do it every so often.  Probably that is too much of a pain for you.

The power management options are on the screensaver configuration option.  Desktop --> Preferences.

If you give me the output of the command "lspci" I can tell you what your video card is.

Sorry for the sometimes slow responses... I am probably in a different timezone than you, but I won't leave you hanging.

Take care
-mat
> PS - had some Duvel yesterday - magnificent 
You should try Chimay.  Although personally I prefer German beers.  Nothing can beat a Kloster Weltenburger dunkles; brewed by monks in the same monastery since 1050.

---

### Post by steveandarchie on 2007-02-19
Hi mat,

No probs about the response time, I'm grateful for your help. Similar time zone (UK).Here's lspci:

> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

And Suspend2 didn't do anything - I simply changed the power settings to 'never' which I suppose isn't ideal.

I had some Chimay blue and red last Christmas a a cheeky Kasteel (11% - yikes) but I like the sound of the Weltenberger - there's great outlet here called beersofeurope.co.uk - I'll check them out.

All the best
Steve

---

### Post by steveandarchie on 2007-02-21
Anybody else??

---

### Post by steveandarchie on 2007-02-21
...or does anybody want to talk about European beer instead??

---

