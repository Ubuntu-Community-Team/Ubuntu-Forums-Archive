---
title: "Celestia don't work"
date: 2005-04-14
forum: General Help
---

### Post by WillyTP on 2005-04-14
Hi, I'm using Kubuntu 5.04.
I installed Celestia 1.3.0-1, but when I try to start it I got the following error:

Unable to resolve Xmu symbols - please check your Xmu library installation.
celestia: ERROR: Communication problem with celestia, it probably crashed.

I checked, I have libxmu6 6.8.2-10 plus libxmuu1 6.8.2-10 installed.
I have a ATi Radeon 9800Pro card with the ATi drivers installed like in this topic is shown:

[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

Some suggestions? Thanks

---

### Post by kleeman on 2005-04-14
I have regular ubuntu hoary installed and the packages mentioned. My celestia runs perfectly. I have an nvidia card. I assume that glxgears shows a respectable framerate for you meaning your graphical drivers are installed properly.... Which celestia packages did you install? If you do a sudo /sbin/ldconfig -v do you pick up libraries in /usr/X11R6/lib/ (thats where the xmu libraries are) You should have /usr/X11R6/lib in /etc/ld.so.conf

---

