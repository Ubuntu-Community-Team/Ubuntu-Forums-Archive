---
title: "How do I prevent my drivers from being pooched by kernel updates?"
date: 2007-02-11
forum: General Help
---

### Post by murraysw on 2007-02-11
Hi community,

I just upgraded to the .11 kernel to find that all my drivers had been boned.  When I first tried to boot, I didn´t even realize a kernel update had taken place.  Booting to X not starting is never cool.  So I did some poking and noticed that there was a kernel update and thats why my Nvidia drivers werent loading - I tried to update my restricted-modules and linux-headers-generic or whatever.  I hear that fixes the problem.  Although, my ETHERNET drivers are also gone.  So I´m back to sqaure 1.  No internet.  No drivers.

I booted back into the .10 kernel, everythings working fine.  What I want to do is just make a CD  with all of the drivers and stuff updated for the .11 kernel, just pop it in and let them install. 


My question is this:

Is there a way to do kernel updates without having to reinstall drivers all the time OR is there a script or method of making it very trivial for driver updates every kernel update? 

thanks

scott

---

### Post by Ramses de Norre on 2007-02-11
Drivers are built against a kernel and when the kernel changes you need new drivers, that's all and there is no alternative..

However kernel upgrades don't occur often and when they do a normal update isn't enough, a dist-upgrade is required. I think that this is a more than appropriate warning to get your attention.

For the restricted drivers stuff: you should never install only the linux-image, instead you need to install the linux package which contains the image, the restricted-modules and the headers and thus fore comes a lot of trouble.
So I suggest you install linux-386 or linux-generic according to which kernel you're using and all problems should be solved.

EDIT: seems like I was a bit too fast and there are problems with the 2.6.17-11 kernel and some wifi drivers reported, search the forums if your wireless problems aren't solved after installing the restricted drivers.

---

