---
title: "[SOLVED] Greenish glow, shadow or halo around windows after upgrade"
date: 2008-05-16
forum: General Help
---

### Post by ctrlf5 on 2008-05-16
After upgrading to Hardy from Gutsy, I now have a greenish glow around my windows. I had Compiz installed on Gutsy and there were no halos around my windows back then.

Anyone have the same problem and possibly a solution?

---

### Post by Thanoulis on 2008-05-16
Maybe its the *Reflection* plugin. Anyway, what video card are you using?

---

### Post by chris4585 on 2008-05-16
could possibly be emerald

---

### Post by ctrlf5 on 2008-05-19
I don't have Reflection enabled. I've got an nvidia MX 420.

---

### Post by Forlong on 2008-05-19
```
cd /usr/lib/xorg/modules && sudo mv libwfb.so libwfb.so.bak ; sudo ln -s /usr/lib/nvidia/libwfb.so.xserver-xorg-core libwfb.so
```
should fix this

---

### Post by ctrlf5 on 2008-05-19
Forlong, there's no xorg folder under lib. I'm using Hardy, btw.

---

### Post by Forlong on 2008-05-19
There is on my Hardy install.

How did you install the nvidia driver?

---

### Post by ctrlf5 on 2008-05-19
I followed [HowTo: Xubuntu 7.10 - nVidia - Compiz Fusion Desktop Effects for Newbies]("http://ubuntuforums.org/showthread.php?t=623752") when I was on Gutsy. Before using that method, I tried the method on what I am guessing is [your blog]("http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users") but couldn't get it to work for me.

I since upgraded to Hardy via the Update Manager and now have this glow issue that I previously did not have on Gutsy.

---

### Post by Forlong on 2008-05-19
Could you please run [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070") and post the output here?

---

### Post by ctrlf5 on 2008-05-19
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   Xfce
 Graphics chip:         nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by Forlong on 2008-05-19
And ```
ls /usr/lib/xorg/
``` as well as ```
dpkg -l | grep 'xorg-driver\|xorg-video'
```

Please use the forum's [noparse][code][/noparse] tag (# button)!

---

### Post by ctrlf5 on 2008-05-19
```
modules
```

```
ii  xserver-xorg-video-all                     1:7.3+10ubuntu10                                   the X.Org X server -- output driver metapackage
ii  xserver-xorg-video-amd                     2.8.0-7                                            AMD Geode GX/LX display driver (dummy transitional package)
ii  xserver-xorg-video-apm                     1:1.1.1-10                                         X.Org X server -- APM display driver
ii  xserver-xorg-video-ark                     1:0.6.0-9                                          X.Org X server -- ark display driver
ii  xserver-xorg-video-ati                     1:6.8.0-1                                          X.Org X server -- ATI display driver
ii  xserver-xorg-video-chips                   1:1.1.1-9                                          X.Org X server -- Chips display driver
ii  xserver-xorg-video-cirrus                  1:1.1.0-8                                          X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-cyrix                   1:1.1.0-8                                          X.Org X server -- Cyrix display driver
ii  xserver-xorg-video-dummy                   1:0.2.0-7                                          X.Org X server -- dummy display driver
ii  xserver-xorg-video-fbdev                   1:0.3.1-4                                          X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode                   2.8.0-7                                            X.org server -- AMD Geode GX/LX display driver
ii  xserver-xorg-video-glint                   1:1.1.1-8                                          X.Org X server -- Glint display driver
ii  xserver-xorg-video-i128                    1:1.2.1-4                                          X.Org X server -- i128 display driver
ii  xserver-xorg-video-i740                    1:1.1.0-7                                          X.Org X server -- i740 display driver
ii  xserver-xorg-video-i810                    2:1.7.4-0ubuntu7                                   X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-imstt                   1:1.1.0-7                                          X.Org X server -- IMSTT display driver
ii  xserver-xorg-video-intel                   2:2.2.1-1ubuntu13                                  X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mga                     1:1.4.8.dfsg.1-1                                   X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic                1:1.1.1-8                                          X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-newport                 1:0.2.1-4ubuntu1                                   X.Org X server -- Newport display driver
ii  xserver-xorg-video-nsc                     1:2.8.3-2                                          X.Org X server -- NSC display driver
ii  xserver-xorg-video-nv                      1:2.1.8-1ubuntu1                                   X.Org X server -- NV display driver
ii  xserver-xorg-video-openchrome              1:0.2.901-0ubuntu4                                 X.Org X server -- VIA display driver
ii  xserver-xorg-video-psb                     0.2.1-1ubuntu3                                     2D graphics driver for Poulsbo
ii  xserver-xorg-video-rendition               1:4.1.3.dfsg.1-4                                   X.Org X server -- Rendition display driver
ii  xserver-xorg-video-s3                      1:0.5.0-4                                          X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge                 1:1.9.1-7                                          X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-video-savage                  1:2.1.3-5                                          X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion           1:1.5.1-3                                          X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                     1:0.9.3-6                                          X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                  1:0.8.1-9                                          X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                    1:1.3.0-6                                          X.Org X server -- tdfx display driver
ii  xserver-xorg-video-tga                     1:1.1.0-9ubuntu1                                   X.Org X server -- TGA display driver
ii  xserver-xorg-video-trident                 1:1.2.4-1                                          X.Org X server -- Trident display driver
ii  xserver-xorg-video-tseng                   1:1.1.1-4                                          X.Org X server -- Tseng display driver
ii  xserver-xorg-video-v4l                     1:0.1.1-6ubuntu1                                   X.Org X server -- Video 4 Linux display driver
ii  xserver-xorg-video-vesa                    1:1.3.0-4ubuntu4                                   X.Org X server -- VESA display driver
ii  xserver-xorg-video-vga                     1:4.1.0-8                                          X.Org X server -- VGA display driver
ii  xserver-xorg-video-via                     1:0.2.2-5                                          X.Org X server -- VIA display driver
ii  xserver-xorg-video-vmware                  1:10.15.2-1ubuntu2                                 X.Org X server -- VMware display driver
ii  xserver-xorg-video-voodoo                  1:1.1.1-5                                          X.Org X server -- Voodoo display driver

```

---

### Post by Forlong on 2008-05-19
> **ctrlf5 said:**
> ```
modules
```
That means there **is** the directory on your system.
What made you think there wasn't?

---

### Post by ctrlf5 on 2008-05-19
Running the code in your first post (#5) gave me:

```
mv: cannot stat `libwfb.so': No such file or directory
```

Looking in the File System for the folder yields the same result. I have all hidden files shown as well.

---

### Post by Forlong on 2008-05-19
OK... but that does **not** mean, "there's no xorg folder under lib"

Anyway... now please post the output of
```
ls /usr/lib/xorg/modules
``` and ```
ls /usr/lib/nvidia
```

---

### Post by ctrlf5 on 2008-05-19
```
[COLOR="Blue"]drivers[/COLOR]     libcfb32.so  libmfb.so       libvbe.so     libxf8_16bpp.so
[COLOR="Blue"]extensions[/COLOR]  libcfb.so    libpcidata.so   libvgahw.so   libxf8_32bpp.so
[COLOR="Blue"]fonts[/COLOR]       libexa.so    libscanpci.so   libxaa.so     [COLOR="Blue"]linux[/COLOR]
[COLOR="Blue"]input[/COLOR]       libfb.so     libshadowfb.so  libxf1bpp.so  [COLOR="Blue"]multimedia[/COLOR]
libafb.so   libint10.so  libshadow.so    libxf4bpp.so

```

```
libGL.so.1.2.xlibmesa  libglx.so.xserver-xorg-core  [COLOR="SeaGreen"]tls_test[/COLOR]
[COLOR="Red"]libGL.so.1.xlibmesa[/COLOR]    libwfb.so.xserver-xorg-core  tls_test_dso.so

```

---

### Post by Forlong on 2008-05-19
Now try ```
sudo ln -s /usr/lib/nvidia/libwfb.so.xserver-xorg-core /usr/lib/xorg/modules/libwfb.so
``` afterwards restart X and see if it did you any good.

---

### Post by ctrlf5 on 2008-05-19
Worked! Thanks!

---

### Post by ctrlf5 on 2008-05-19
I did a reboot just in case and the problem resurfaced.

---

### Post by Forlong on 2008-05-19
Then it may be a problem with Emerald (I assume you're using Emerald, since you're on Xfce).

Try fiddling with the shadow options of your theme in *System &#8594; Properties &#8594; Emerald Theme Manager*

---

### Post by BlueSkyNIS on 2008-05-19
> **ctrlf5 said:**
> ```
[COLOR="Blue"]drivers[/COLOR]     libcfb32.so  libmfb.so       libvbe.so     libxf8_16bpp.so
[COLOR="Blue"]extensions[/COLOR]  libcfb.so    libpcidata.so   libvgahw.so   libxf8_32bpp.so
[COLOR="Blue"]fonts[/COLOR]       libexa.so    libscanpci.so   libxaa.so     [COLOR="Blue"]linux[/COLOR]
[COLOR="Blue"]input[/COLOR]       libfb.so     libshadowfb.so  libxf1bpp.so  [COLOR="Blue"]multimedia[/COLOR]
libafb.so   libint10.so  libshadow.so    libxf4bpp.so

```

```
libGL.so.1.2.xlibmesa  libglx.so.xserver-xorg-core  [COLOR="SeaGreen"]tls_test[/COLOR]
[COLOR="Red"]libGL.so.1.xlibmesa[/COLOR]    libwfb.so.xserver-xorg-core  tls_test_dso.so

```

I don't have any problems, but I have a question: what is about "libGL.so.1.xlibmesa" invalid link? Is that normal?

---

### Post by Forlong on 2008-05-19
BlueSkyNIS, if it bothers you, I'd recommend starting a separate thread about it, because very few people will read your question in a thread like this one.

---

### Post by ctrlf5 on 2008-05-20
Got rid of the glow by fiddling with some of the shadow settings in emerald as suggested by Forlong.

---

