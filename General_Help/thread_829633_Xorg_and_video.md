---
title: "Xorg and video"
date: 2008-06-15
forum: General Help
---

### Post by hardysummer on 2008-06-15
Hi,

I am trying to install X minimally.  I was told to choose the proper video when installing it.

So my questions are:

What is the command to find out what my video is?

How do I specifically tell apt-get to install xorg with my corresponding video?

---

### Post by BandD on 2008-06-15
What exactly do you mean by video?  Video Card, perhaps?

If it is your video card try this command in a terminal (Applications--> Accessories--> Terminal):

```
lspci | grep Display
```

---

### Post by hardysummer on 2008-06-16
Nothing.  Because the video is onboard.

---

### Post by Zorael on 2008-06-16
```
$ lshw -C video
```
It should say stuff about your card. Its manufacturer, make, perhaps even currently used driver.

Available xserver-xorg-video packages:
```
$ dpkg -l xserver-xorg-video-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                 Version                              Description
+++-====================================-====================================-========================================================================================
un  xserver-xorg-video-1.0               <none>                               (no description available)
un  xserver-xorg-video-1.9               <none>                               (no description available)
un  xserver-xorg-video-2                 <none>                               (no description available)
ii  xserver-xorg-video-all               1:7.3+10ubuntu10.1                   the X.Org X server -- output driver metapackage
ii  xserver-xorg-video-amd               2.9.0-1ubuntu2.1                     AMD Geode GX/LX display driver (dummy transitional package)
ii  xserver-xorg-video-apm               1:1.1.1-10                           X.Org X server -- APM display driver
ii  xserver-xorg-video-ark               1:0.6.0-9                            X.Org X server -- ark display driver
ii  xserver-xorg-video-ati               1:6.8.0-1                            X.Org X server -- ATI display driver
un  xserver-xorg-video-atimisc           <none>                               (no description available)
ii  xserver-xorg-video-chips             1:1.1.1-9                            X.Org X server -- Chips display driver
ii  xserver-xorg-video-cirrus            1:1.1.0-8ubuntu1                     X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-cyrix             1:1.1.0-8                            X.Org X server -- Cyrix display driver
ii  xserver-xorg-video-dummy             1:0.2.0-7                            X.Org X server -- dummy display driver
ii  xserver-xorg-video-fbdev             1:0.3.1-4                            X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode             2.9.0-1ubuntu2.1                     X.org server -- AMD Geode GX/LX display driver
ii  xserver-xorg-video-glint             1:1.1.1-8                            X.Org X server -- Glint display driver
ii  xserver-xorg-video-i128              1:1.2.1-4                            X.Org X server -- i128 display driver
ii  xserver-xorg-video-i740              1:1.1.0-7                            X.Org X server -- i740 display driver
ii  xserver-xorg-video-i810              2:1.7.4-0ubuntu7                     X.Org X server -- Intel i8xx, i9xx display driver
un  xserver-xorg-video-i810-modesetting  <none>                               (no description available)
ii  xserver-xorg-video-imstt             1:1.1.0-7                            X.Org X server -- IMSTT display driver
ii  xserver-xorg-video-intel             2:2.2.1-1ubuntu13.4                  X.Org X server -- Intel i8xx, i9xx display driver
un  xserver-xorg-video-intel-modesetting <none>                               (no description available)
ii  xserver-xorg-video-mga               1:1.4.8.dfsg.1-1                     X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic          1:1.1.1-8                            X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-newport           1:0.2.1-4ubuntu1                     X.Org X server -- Newport display driver
ii  xserver-xorg-video-nsc               1:2.8.3-2                            X.Org X server -- NSC display driver
ii  xserver-xorg-video-nv                1:2.1.8-1ubuntu1                     X.Org X server -- NV display driver
ii  xserver-xorg-video-openchrome        1:0.2.901-0ubuntu4                   X.Org X server -- VIA display driver
ii  xserver-xorg-video-psb               0.2.1-1ubuntu3                       2D graphics driver for Poulsbo
ii  xserver-xorg-video-rendition         1:4.1.3.dfsg.1-4                     X.Org X server -- Rendition display driver
un  xserver-xorg-video-riva128           <none>                               (no description available)
ii  xserver-xorg-video-s3                1:0.5.0-4                            X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge           1:1.9.1-7                            X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-video-savage            1:2.1.3-5                            X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion     1:1.5.1-3                            X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis               1:0.9.3-6                            X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb            1:0.8.1-9                            X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx              1:1.3.0-6                            X.Org X server -- tdfx display driver
ii  xserver-xorg-video-tga               1:1.1.0-9ubuntu1                     X.Org X server -- TGA display driver
ii  xserver-xorg-video-trident           1:1.2.4-1                            X.Org X server -- Trident display driver
ii  xserver-xorg-video-tseng             1:1.1.1-4                            X.Org X server -- Tseng display driver
ii  xserver-xorg-video-v4l               1:0.1.1-6ubuntu1                     X.Org X server -- Video 4 Linux display driver
ii  xserver-xorg-video-vesa              1:1.3.0-4ubuntu4                     X.Org X server -- VESA display driver
ii  xserver-xorg-video-vga               1:4.1.0-8                            X.Org X server -- VGA display driver
ii  xserver-xorg-video-via               1:0.2.2-5                            X.Org X server -- VIA display driver
ii  xserver-xorg-video-vmware            1:10.15.2-1ubuntu2                   X.Org X server -- VMware display driver
ii  xserver-xorg-video-voodoo            1:1.1.1-5                            X.Org X server -- Voodoo display driver
```
So, if you have an Intel 865 chipset, you could just install **xserver-xorg-video-intel**. An Nvidia card, **xserver-xorg-video-nv**. Etc.

---

### Post by BandD on 2008-06-16
> **hardysummer said:**
> Nothing.  Because the video is onboard.


Mine is onboard as well and it shows up in lspci.  If you aren't getting anything with the grep Display pipe then try just lspci...if the system detects your card it should show something for graphics related stuff.

---

### Post by hardysummer on 2008-06-18
Nothing about "graphic" or "video" either.

lshw returned with:

"description: VGA compatible controller"
"product: VT8378 [S3 Unichrome] Integrated Video"
"Vendor: VIA Technologies, Inc."

The rest of the stuff does not look very useful.

So do I install the xserver*s3 or the xserver*via?  Or is there something more to it than the name?

If I use the wrong package, would it damage the chip or just get bad results visually?

---

### Post by hardysummer on 2008-06-21
Help?  I am still trying to install X.

I do not want to bloat up my system by installing all the videos and drivers.  Which is the correct and minimal package set I should install?

---

### Post by leetrefz on 2008-08-05
I'm not an expert but I use xserver-xorg-video-openchrome which is developed for unichrome with linux.

worst case scenario if it doesn't work is you need to select a working driver from command line.

---

