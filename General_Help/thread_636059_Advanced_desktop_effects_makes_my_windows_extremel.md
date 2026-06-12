---
title: "Advanced desktop effects makes my windows extremely choppy..."
date: 2007-12-09
forum: General Help
---

### Post by Nick11 on 2007-12-09
Here we go again =/. Alright so I figured I would try compiz+fusion, by getting the advanced desktop effects. Before this everything was running smooth, everything was "A-OK." But, when I installed advanced desktop effect to get the rotating cube, more effects, etc, my desktop becomes extremely choppy. It looks like I am going to have to reinstall (This is like my 15th time doing a reinstall within a week). 

So, I said "maybe its the drivers" so I installed the i850 intel drivers (and boy that was a headache), but I managed to get it working. Still, I had the same result with the same choppy desktop. Even before this I tried reverting to "normal effects" and even "basic effects" still, no luck. My windows are choppy, I can't even scroll down a page without severe tearing and flickering. 

I really need help guys =/. I am going to do a fresh install and I will only install advanced desktop effects to eliminate any variables. But, I am sure the problem will persist. I have an Intel 950GMA chipset and I was wondering if anyone has a similar problem and has a solution addressing this issue. Thanks in advance.

---

### Post by Brucevdk on 2007-12-09
> **Nick11 said:**
> But, when I installed advanced desktop effect to get the rotating cube, more effects, etc, my desktop becomes extremely choppy. It looks like I am going to have to reinstall (This is like my 15th time doing a reinstall within a week).

Why would you reinstall? Why not just remove or disable the package, you can always login into a virtual terminal (CTRL + ALT + F1) and execute *sudo apt-get remove --auto-remove compiz*.

> **Nick11 said:**
> So, I said "maybe its the drivers" so I installed the i850 intel drivers (and boy that was a headache), but I managed to get it working.

I thought installing the Intel drivers (i850 included) was as simple as executing *sudo apt-get install xserver-xorg-video-intel* and changing the Driver option under the according Device in your Xorg config (/etc/X11/xorg.conf). It's not?

```
xserver-xorg-video-intel - X.Org X server -- Intel i8xx, i9xx display driver
```

> **Nick11 said:**
> Still, I had the same result with the same choppy desktop. Even before this I tried reverting to "normal effects" and even "basic effects" still, no luck. My windows are choppy, I can't even scroll down a page without severe tearing and flickering.

Try reinstalling the driver as described above and setting the default depth to 16 under the Screen section (DefaultDepth	16).

---

### Post by oodledoodle on 2007-12-09
its a vsync issue. whats happening is video is being sent to your monitor quicker than your monitor can handle. try downloading the compiz config manager and going into system > preferences > advanced desktop effects settings. click on 'general options' at the top, then go to display settings. check the 'sync to vblank' option. this should sort it. if not, you'll need to enable vsync via the intel drivers, im not sure how to do that. try looking in the intel settings menu if there is one. 
hope this helps.

---

### Post by UK-Wobbie on 2007-12-09
> **Nick11 said:**
> Here we go again =/. Alright so I figured I would try compiz+fusion, by getting the advanced desktop effects. Before this everything was running smooth, everything was "A-OK." But, when I installed advanced desktop effect to get the rotating cube, more effects, etc, my desktop becomes extremely choppy. It looks like I am going to have to reinstall (This is like my 15th time doing a reinstall within a week). 

So, I said "maybe its the drivers" so I installed the i850 intel drivers (and boy that was a headache), but I managed to get it working. Still, I had the same result with the same choppy desktop. Even before this I tried reverting to "normal effects" and even "basic effects" still, no luck. My windows are choppy, I can't even scroll down a page without severe tearing and flickering. 

I really need help guys =/. I am going to do a fresh install and I will only install advanced desktop effects to eliminate any variables. But, I am sure the problem will persist. I have an Intel 950GMA chipset and I was wondering if anyone has a similar problem and has a solution addressing this issue. Thanks in advance.

What is your Video Card?
Some Video Cards will not work on Ubuntu!

---

### Post by Nick11 on 2007-12-09
Well, I fixed the problem by simply reinstalling Ubuntu. The problem was that the version or effects I was using messed up my display. As the user posted above that may have been the problem. Anyway, everything is back to being "A-OK" =]. I now can cntrl+alt and drag into the cube with reflections, which is pretty impressive I must say.

> **Brucevdk said:**
> Why would you reinstall? Why not just remove or disable the package, you can always login into a virtual terminal (CTRL + ALT + F1) and execute *sudo apt-get remove --auto-remove compiz*.



I thought installing the Intel drivers (i850 included) was as simple as executing *sudo apt-get install xserver-xorg-video-intel* and changing the Driver option under the according Device in your Xorg config (/etc/X11/xorg.conf). It's not?

```
xserver-xorg-video-intel - X.Org X server -- Intel i8xx, i9xx display driver
```



Try reinstalling the driver as described above and setting the default depth to 16 under the Screen section (DefaultDepth	16).

Well, I had to reconfigure xorg (in recovery mode), because the i850 drivers simply did not install properly, which stopped Unbuntu from running. So, I had to use the above command and change the "i850" to "Intel", in the configuration text, which still did not work. So, I had to, like I said, reconfigure xorg through a series of menus. It may have been easy, but it sure as hell was frustrating. Anyway, even with i850 installed I had the same effect. Currently, I am using the default Intel drivers, that were installed with the installation of the OS. So, the reinstall worked- anyway I can finally let out a sigh of relief.

---

### Post by UK-Wobbie on 2007-12-09
> **Nick11 said:**
> Well, I fixed the problem by simply reinstalling Ubuntu. The problem was that the version or effects I was using messed up my display. As the user posted above that may have been the problem. Anyway, everything is back to being "A-OK" =].

Thats good to know ;)

---

