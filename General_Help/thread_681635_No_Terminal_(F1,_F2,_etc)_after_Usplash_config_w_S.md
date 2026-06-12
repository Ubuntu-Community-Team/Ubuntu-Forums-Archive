---
title: "No Terminal (F1, F2, etc) after Usplash config w/ StartupManager"
date: 2008-01-29
forum: General Help
---

### Post by rrohde on 2008-01-29
No Terminal (F1, F2, etc) after Usplash config w/ StartupManager

Hi all, 

this is interesting: 

I downloaded a tarball with the Ubuntu usplash-theme source, changed the images within to suit my needs and ran "make" to compile my new *.so file to inject it with "StartupManager" into my system. Upon reboot, all is well: I got my custom usplash theme working just fine. 

However, when I try to switch to my Terminals (Ctrl+Alt+F1, etc), all I get is a black screen with a blinking cursor in the top left. 

When I set the kernel params to include "nosplash", I (obviously) don't get a usplash theme, but after GDM is available, I can get to my Terminals just fine. 

So my question is: 
What causes the Terminal to break with my StartupManager injected usplash theme and how can I fix it?


Attempted fixes so far: 
- kernel-params vga=xxx, where xxx is all known numbers that I came across - same issue
- dumping my custom usplash theme, going with the default one from the source, using StartupManager to inject it - same issue.

It seems as long as my usplash attempts are injected using "StartupManager", my Terminals are shot. However, I have not tried to inject the *.so file into the system "by hand", so to say, as I am not sure how that's done if if that would make a difference... 

So, it seems that it's either no splash or my custom-splash without Terminals for the time being, but I really would like to use those custom splash screens.


Any help solving this is greatly appreciated.

I am using Gutsy, patched to the latest greatest... :) 


Cheers, 
Rainer

---

### Post by rrohde on 2008-01-30
Guess I found a rather simple solution for this: 

I removed all "vga=xxx" references from the menu.lst and voila - the splash screen defaults to *some* resolution and, when GDM is available, my terminals work just fine! ;)

---

