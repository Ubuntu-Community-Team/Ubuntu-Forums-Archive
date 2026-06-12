---
title: "Gutsy+fglrx+xvideo+kaffeine=X server crash"
date: 2007-10-23
forum: General Help
---

### Post by Thares on 2007-10-23
As the title suggests, I'm having a problem with the XVideo extension with fglrx.

First of all, I'ev noticed that xv didn't work at all with gutsy's default restricted drivers, so I've installed the 8.40.4 version according to this howto [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.40.4_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.40.4_Driver_Manually)

Now XVideo works, but only partially - it supports only YV12 and I420.
Actually, 'xine-check' shows the following, curious diagnosis:


```
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to do color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         http://www.linuxvideo.org/gatos/
         press <enter> to continue...

[ good ] Xv ports:  YV12 I420

```
...which is probably due to the fact that it checks for YUY2 which isn't there. Oh well.

When I start kaffeine (which uses the xv driver) the X server crashes leaving the following backtrace:

```
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c9581]
1: [0xffffe420]
2: /usr/lib/xorg/modules//glesx.so [0xb6699966]
3: /usr/lib/xorg/modules//glesx.so [0xb666de91]
4: /usr/lib/xorg/modules//glesx.so [0xb6651643]
5: /usr/lib/xorg/modules//glesx.so [0xb664cead]
6: /usr/lib/xorg/modules//glesx.so [0xb660fa8f]
7: /usr/lib/xorg/modules//glesx.so [0xb660b4d6]
8: /usr/lib/xorg/modules//glesx.so [0xb66076b0]
9: /usr/lib/xorg/modules//glesx.so [0xb6606105]
10: /usr/bin/X [0x80dd9ef]
11: /usr/lib/xorg/modules/extensions//libextmod.so(XvdiPutImage+0x174) [0xb7c8c4c4]
12: /usr/lib/xorg/modules/extensions//libextmod.so [0xb7c8f488]
13: /usr/bin/X [0x815754e]
14: /usr/bin/X(Dispatch+0x1aa) [0x808f47a]
15: /usr/bin/X(main+0x495) [0x8076f05]
16: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7dac050]
17: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8076241]

```

Seemingly, a problem in the glesx.so file, so I've recompiled the xserver-xorg-fglrx package (with the 8.40.4 version of course) but to no avail. 
Any ideas?

---

### Post by Thares on 2007-10-24
After sitting at this for hours, I've decided to at least stop the X crashes by disabling the xv and xvmc extensions in the xorg.conf:

```

Section "Module"
        Load            "dbe"
        Load            "dri"
        Load           "extmod"
        Load           "glx"
        Load           "GLcore"
        Load    "freetype"
        Load    "int10"
        Load    "vbe"
   SubSection "extmod"
        Option "omit xvideo"
        Option "omit xvideo-motioncompensation"
   EndSubSection
EndSection

```

Obviously, this is just a temporary fix since XVideo is necessary; right now I'm running movies at about 80% CPU usage (AMD64 3200+).
So, if anyone has come across at a XVideo solution with gutsy and fglrx, please let me know.

---

### Post by alonso on 2007-12-03
I'm having exactly the same problem with fglrx in Gutsy. xvideo has stopped working with xine ever since xvinfo started reporting this in the title:

"ATI Radeon AVIVO Video"

With some old drivers, it used to report something like "ATI Radeon Video Overlay" - the same as with the open source "radeon" driver.

The problem is that once the AVIVO video overlay is used, the video quality sucks and kaffeine crashes time to time.

My HW is HP nx 8220 with Radeon X600 graphics.

Anybody know how to get the old XV with the newer drivers? Or is there a way to use the old 8.34.8 fglrx drivers with Gutsy.

---

### Post by imrazor on 2007-12-09
> **Thares said:**
> After sitting at this for hours, I've decided to at least stop the X crashes by disabling the xv and xvmc extensions in the xorg.conf:

```

Section "Module"
        Load            "dbe"
        Load            "dri"
        Load           "extmod"
        Load           "glx"
        Load           "GLcore"
        Load    "freetype"
        Load    "int10"
        Load    "vbe"
   SubSection "extmod"
        Option "omit xvideo"
        Option "omit xvideo-motioncompensation"
   EndSubSection
EndSection

```Obviously, this is just a temporary fix since XVideo is necessary; right now I'm running movies at about 80% CPU usage (AMD64 3200+).
So, if anyone has come across at a XVideo solution with gutsy and fglrx, please let me know.

I tried disabling xv and xvmc, and had no luck. kaffeine still crashed the X server when using xvideo. I tried using xshm for a while, but it this caused kaffeine to crash after a short period. Finally I tried VLC, and found that xvideo still caused problems. I switched the output module to "X11 video output" and so far neither VLC nor the X server has crashed. Unscaled, processor usage is minimal - at less than 10%. However scaling the video up to full screen causes processor usage to spike to 50%. Also, scaled video using that "output module" causes heavy pixelation when the video is scaled up. There's absolutely no anti-aliasing. A solution that's far from perfect, but better than no video at all.

---

### Post by scotty64 on 2007-12-09
> **Thares said:**
> After sitting at this for hours, I've decided to at least stop the X crashes by disabling the xv and xvmc extensions in the xorg.conf:

Obviously, this is just a temporary fix since XVideo is necessary; right now I'm running movies at about 80% CPU usage (AMD64 3200+).
So, if anyone has come across at a XVideo solution with gutsy and fglrx, please let me know.

Thanks for that! I had similar problems with fglrx and dapper for ages, got no answer to my posts and could not watch movies properly. Now I can even use my WinTV USB2 video capture adapter again - although good old XawTV seems to be the only telly that works as all the others (kdetv, tvtime) want xvideo.

---

### Post by imrazor on 2007-12-11
After further research and a bit of brainstorming I came up with another partial fix. Installing Xgl will allow you to run xvideo without crashing, but there's a heavy cpu hit. To install Xgl, do the following
```

sudo apt-get install xserver-xgl

```
After installing Xgl, you'll need to restart your X server (rebooting is simplest.) Curiously, it seems necessary to enable desktop effects, otherwise CPU usage is through the roof. Even with the desktop effects on, CPU usage is very high on anything larger than 320x240. And you can forget full screen playback.

---

