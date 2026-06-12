---
title: "Ubuntu Software Center lists Chromium as not installed even though it is."
date: 2017-11-18
forum: General Help
---

### Post by isolatedvertex on 2017-11-18
Right after installing Chromium on a newly installed Ubuntu 17.10, I realized that I would rather have Chrome for Amazon videos to work. So when I tried removing Chromium from Ubuntu Software, it does not list Chromium as an installed application.

I also tried removing the application using Terminal and it did not find the package either. Unless "chromium-browser" is no longer the package in this build. I ran "apt list --installed" in Terminal and it did not list Chromium as well.

So I decided to reboot the system. Doing so, allows Ubuntu Software to "refresh" and it found Chromium as an installed application where I'm able to remove it.

My questions are: 
1 - Is this a normal behavior in Ubuntu where the system has to be rebooted for Ubuntu Software to determine that an application is installed?
2 - If I installed an application via Ubuntu Software, should it be listed in the result of "apt list"? 
3 - If I install a .deb file, should it be in "apt list"? Or is there another command that will give me a list of ALL installed applications including those outside of Ubuntu Software?

Any help is greatly appreciated as I learn this new OS.

---

