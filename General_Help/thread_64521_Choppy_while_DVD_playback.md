---
title: "Choppy while DVD playback"
date: 2005-09-11
forum: General Help
---

### Post by Waqas on 2005-09-11
Im using Xine (or maybe Wine, not sure bcause Im at office) to play some DVD. It gets choppy and once a message appeared. Something like `Framerate dropped too much. Maybe your system is too slow or overloaded'. But I the playback is still acceptable and doesnt distract me very much. I also notice my mouse cursor gets choppy while playing DVD. 

My system is not that slow I guess:-

P42.8 Ghz (northwood)
Kingmax  512Mb DDR400
Geforce 4Ti 4200 128Mb 128bit
HD 120 GB, 25Gb running Ubuntu

Is this normal??

---

### Post by mlomker on 2005-09-11
Is DMA enabled on your drive?

```

root@mlomkernote:/ # hdparm -v /dev/dvd

/dev/dvd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)

```

---

### Post by Dolphin on 2005-09-11
open terminal

type xine-check

Post what it says.

---

### Post by Waqas on 2005-09-13
Thank you. 

I think DMA is already enabled. I followed the unofficial starter guide. Maybe it wasnt working or I missed some lines. But Ill check it anyway.

---

### Post by vr04 on 2005-09-13
i had this problem in totem. i installed totem-xine, enabled DMA and my problem was solved.

---

### Post by Waqas on 2005-09-16
Solved!!

Thank you, you're da man!!! You all are da man!! :-P

---

### Post by CPUFreak91 on 2005-12-10
[QUOTE=Dolphin]open terminal

type xine-check

Post what it says.[/QUOTE]



therat@DIrtyRat:~$ xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.12-9-386)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ hint ] multiple xine executables found in your PATH
         I have found more than one occurance of 'xine' in your PATH:
         /usr/bin/X11/xine
         /usr/bin/xine
         You have probably installed xine-ui more than once, or the directory
         where you have installed xine occurs more than once in your PATH.
         Technically, this is not really a problem, but it's probably
         somewhat confusing, as it's not obvious, which xine you're using.
         You should probably uninstall the copies that you don't use...
         Further tests assume, you're using /usr/bin/X11/xine
         press <enter> to continue...

[ hint ] several instances of xine-config found in your PATH
         xine-config executables have been found in these places:
         /usr/bin/X11/xine-config
         /usr/bin/xine-config
         This probably means you have several versions of xine-lib installed.
         It's probably best to uninstall all unused xine-libs.
         Further tests will use /usr/bin/X11/xine-config.
         press <enter> to continue...

[ good ] plugin directory /usr/lib/xine/plugins/1.0.1 exists.
[ good ] found unknown plugin: xineplug_flac.so
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/hdb
[ good ] /dev/dvd points to /dev/hdb
[ hint ] DMA is disabled for your DVD interface.
         This will probably result in a serious performance hit when
         playing DVDs. You can issue the command
         hdparm -d1 /dev/hdb
         as root to enable DMA. It would be wise to add this command to
         some script that is executed executed at boot time.
         Note that you probably have to set the DMA mode for your drive as well.         Most DVD-ROMs work fine with multiword DMA mode 2. You can use
         hdparm -d1 -X34 /dev/hdb
         (as root again) to set this mode. Maybe UDMA2 will give you even better         performance, but it only works well with some controllers. You'll
         probably need UDMA capable IDE cables for this mode. If you want
         to try: make backups of your important data and type (as root again)
         sync
         hdparm -d1 -X66 /dev/hdb
         If your System still works fine after this, you probably want to keep
         these settings (add them to some boot script).
         If your system hangs or behaves very strangely after a few minutes, you         should reboot immediately and never use this setting again on this
         machine. Good luck ;-)
         press <enter> to continue...

[ good ] found xvinfo: X-Video Extension version 2.2
[ hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to to color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         [http://www.linuxvideo.org/gatos/](http://www.linuxvideo.org/gatos/)
         press <enter> to continue...

[ hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to to color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         [http://www.linuxvideo.org/gatos/](http://www.linuxvideo.org/gatos/)
         press <enter> to continue...

[ hint ] Your X server doesn't have any XVideo support...
         XVideo is an X server extension introduced by XFree86 4.x. This
         extension provides access to hardware accelerated color space
         conversion and scaling, which gives a great performance boost.
         If you have a fast (>1GHz) machine, you may be able to watch all
         kinds of video, anyway. You will waste lots of CPU cycles, though...
         press <enter> to continue...

therat@DIrtyRat:~$

---

### Post by CPUFreak91 on 2005-12-10
Ok, I enabled DMA and it works a bit better (less chopiness) but it still is noticible.

What would you recomend?

Grr. glxgears won't print any output! But it is pitifully slow.
I run A AMD 3200 (1.58ghz) Sempron, 512 MB ram, 300 MB swap, DVD drive, ATI Xstasy (aka. Radeon) 9200SE w/ 128 mb.

Video Playback works great when reading off my hard drive but dvd's suck.


Here's even more (DMA) info:
root@DIrtyRat:/home/therat#  hdparm -d1 -X66 /dev/hdb

/dev/hdb:
 setting using_dma to 1 (on)
 setting xfermode to 66 (UltraDMA mode2)
 using_dma    =  1 (on)

---

### Post by mlomker on 2005-12-10
[QUOTE=CPUFreak91]Grr. glxgears won't print any output! But it is pitifully slow.
[/quote]

glxgears -printfps

---

### Post by CPUFreak91 on 2005-12-10
2515 frames in 5.0 seconds = 502.918 FPS
3157 frames in 5.0 seconds = 631.305 FPS
3161 frames in 5.0 seconds = 632.053 FPS
2987 frames in 5.0 seconds = 597.346 FPS
2544 frames in 5.0 seconds = 508.799 FPS
3052 frames in 5.0 seconds = 610.386 FPS

Ouch! How do I improve this (and DVD playback?)

---

### Post by mlomker on 2005-12-10
[QUOTE=CPUFreak91]Ouch! How do I improve this (and DVD playback?)[/QUOTE]

I've written a couple how-to's for ATI drivers, but they don't always improve DVD playback.  

The ATI fglrx drivers are 3D drivers and DVD playback is mostly a 2D process.  It'll definitely improve games and screensavers, though.  [Here is the link]("http://ubuntuforums.org/showthread.php?p=408111").

---

### Post by CPUFreak91 on 2005-12-24
thanks. I'll look at it.

EDIT> I've already done that!!! But at least it enabled opengl so I can play a few games.

---

### Post by laurenth on 2005-12-25
I get the following error when trying to enable my DMA setting:

dot@ubuntu:~$ sudo hdparm -d1 /dev/hda
/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

This is the info on my drive:

 Model=HL-DT-ST DVDRAM GSA-4163B, FwRev=A103, SerialNo=K4352I63933
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode


I'm a real beginner at all this so I have no idea what the problem could be. The only things I found on the net was that is was somehow related to kernel stuff (I'm running 5.04). I hope its something else. 

Anybody knows whats happening?

---

