---
title: "Multiple problems, need help please."
date: 2008-04-12
forum: General Help
---

### Post by pl4c3b0 on 2008-04-12
Below are the following problems I'm having with Kubuntu 7.10 and my computer. Please bear with me as I am new to Linux in general. Having just switched from XP to Kubuntu, I am feeling a bit lost. I do apologize if any of these questions have already been asked and answered in these forums; I would take the time to look them up, but I was thinking this way would be easier.

1. I cannot get my graphics card to work on any Linux distro. Every time I have tried to install any flavor of Linux, the installation process froze. The only way I could get Kubuntu installed was to go into BIOS and set my graphics settings to Onboard instead of Auto. My computer is a Dell Dimension 2350, which I have heard is very problematic with ATI video cards and Linux. I currently have an ATI Radeo x1300 video card which I would like to use, however when I switch back to Auto in BIOS and plug my monitor into the video card port, Kubuntu freezes on start up. Is there any way/fix to get my video card working properly so that I can enjoy all the visual bells and whistles that the KDE environment has?

2. My login screen is totally messed up. The font size is so tiny that it is impossible to read. Also, I once tried to install a new KDM theme, but that failed, and now I have some sort of error message that pops up right before the login screen (which of course I cannot read thanks to the small font). Is there any way to make the font at the login screen bigger so that I can read it?

So far those are the biggest two. If anyone can answer any of these questions, I'd greatly appreciate it.

---

### Post by kyphi on 2008-04-12
The driver you need for your ATI video card is in the repositories accessible via Synaptic.  It is called " xorg-driver-fglrx".

Your two problems are related and the new driver should fix them both.  After installing the driver you will have to go back into the BIOS to reset the graphics setting.

Good Luck.

---

