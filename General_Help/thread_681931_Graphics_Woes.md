---
title: "Graphics Woes"
date: 2008-01-29
forum: General Help
---

### Post by jsprung on 2008-01-29
Hello all,

I'm a relatively new Ubuntu user. For the most part, things are working great. However, I am having some problems with my graphics setup. My card is a ATI x800 xl. Right now, I am using the RADEON driver. My display looks good and compiz is running well, but I can't configure my dual monitors or run more graphically intense programs. For example, when I use the screen saver browser, many of the more complex ones will crash me to the login screen. I am also trying to play games via Wine, but these crash to desktop after the loading screen. I feel like I should be using the proprietary drivers if I want my graphics card to work correctly, but they make things much worse. When I switch to the fglrx driver, my screen turns weird colors and resolutions, and when I reboot Ubuntu runs in Low Graphics Mode. I have tried installing the driver directly from the website, but that also failed. Any help would be greatly appreciated; my windows boot just conked out on me, and now I have no way to play games...its hard.
Thanks a mil.

---

### Post by jsprung on 2008-01-30
hmmmmm?

---

### Post by cags on 2008-02-08
Ah, it appears we're in exactly the same boat. I just got using Ubuntu last night after watching my girlfriend using it for a long time. I have the exact same graphic card as you and am unable to properly install the driver. I might even just switch over to my old Nvidia, but I'll have another crack tonight and see what I can do.

I'll let you know if it's successful.

---

### Post by kesman on 2008-02-08
Try installing the ATI driver with Envy, it does it automagically.

---

### Post by danwood76 on 2008-02-08
Have you tried installing the fglrx driver through the restricted drivers manager?
this should give you better openGL performance and dual monitors etc.

---

### Post by jsprung on 2008-02-12
What is "Envy"? Automagic sounds like what I need...I did try the restricted drivers manager, to no avail...Any luck, cags?

---

### Post by apetresc on 2008-02-12
> **jsprung said:**
> What is "Envy"? Automagic sounds like what I need...I did try the restricted drivers manager, to no avail...Any luck, cags?
I highly reccomend Envy as well. It is a script written by an Ubuntu developer that takes care of downloading and installing the very latest drivers for ATi and NVidia cards. It solves a *lot* of problems.

You can find the .deb here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)  It's super-easy to use and I recommend it more than the repository's fglrx driver.

---

### Post by jsprung on 2008-02-12
Welll i tried Envy with all three versions of the ATI driver, and no luck--exact same problems. Is it hopeless?

---

### Post by jsprung on 2008-02-16
Some interesting developements:
I unplugged my second monitor(which was only working as a mirror anyway) and tried again to install the proprietary drivers via Envy. At the end of Envy, I think I accidentally clicked to not have it automatically configure my xorg.conf. When I restarted, my computer amazingly did not start in low graphics mode. I opened the restricted drivers manager, and it said the ATI drivers were in use, but the 'enabled' option was not checked. In the Screens and Graphics manager,  it says I am using the Radeon open source driver.
Now when I try to run Compiz, my screen turns white, and games still don't run...I am going to try enabling or switching to fglrx in the manager. We'll see what happens.

---

### Post by jsprung on 2008-02-16
SO I accidentally enabled compiz permanently, so now when i log in the screen goes white...can anyone tell me how to disable it in the recovery mode command prompt?

---

