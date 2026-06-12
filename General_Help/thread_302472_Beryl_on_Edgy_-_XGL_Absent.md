---
title: "Beryl on Edgy - XGL Absent"
date: 2006-11-18
forum: General Help
---

### Post by Garrett on 2006-11-18
I've spent a few hours now following wikis and forum guides trying to fix this. Whenever I try to launch beryl (beryl-manager, beryl, or beryl-xgl) I get the following in the terminal followed by my windows losing their borders and the KDE panel disappearing.

> garrett@garrett-desktop:~$ beryl-manager
garrett@garrett-desktop:~$ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: Another composite manager is already running on screen: 0
beryl: No manageable screens found on display :0.0


The only thing I can think of is that I recently reinstalled Kubuntu but kept my /home partition from my last install (Ubuntu Dapper) where I was running XGL/COMPIZ, the novell way. Is it possible that Compiz is still around to haunt me somehow?

And yes, I've added all sorts of things to my xorg.conf as perscribed in the many posts trying to address this around the web.

Also, if I try to launch emerald independently, nothing happens. It is installed though...

-Garrett

---

