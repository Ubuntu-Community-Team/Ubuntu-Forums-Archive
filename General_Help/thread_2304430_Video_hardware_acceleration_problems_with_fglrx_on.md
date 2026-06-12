---
title: "Video hardware acceleration problems with fglrx on Kubuntu 15.10"
date: 2015-11-26
forum: General Help
---

### Post by El Zoido on 2015-11-26
Hello!

Due to the Kernel issues with fglrx on (K)ubuntu 15.10, I had till a few days ago used radeonsi.
With the release of fixes and a new fglrx version by AMD, I had decided to switch to fglrx due to better performance in games.
However, I noticed that suddenly youtube videos were completely green whenever I switched to hd (720p+).
I suspected an issue with hardware acceleration and checked if I had the necessary packages installed, but vainfo output looked normal.
Nevertheless I decided to switch to fglrx-updates from the repositories and after rebooting video output seemed fine at first.
Unfortunately now CPU usage was relatively high, so I checked vainfo again:
```
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```

I switched to fglrx (sans -updates), but it had no effect. Reinstalling various packages related to va-api didn't help either.
For some reason it seems that fglrx(-updates) from the official repositories has no working hardware acceleration for video playback, at least for me.

Some infos about my system:
```
System:    Host: xxxxx-desktop Kernel: 4.2.0-18-generic x86_64 (64 bit) Desktop: KDE 5
           Distro: Ubuntu 15.10 wily
Machine:   Mobo: Gigabyte model: GA-870A-UD3 v: x.x Bios: Award v: F5 date: 08/01/2011
CPU:       Quad core AMD Phenom II X4 965 (-MCP-) cache: 2048 KB 
           clock speeds: max: 3400 MHz 1: 800 MHz 2: 2200 MHz 3: 2200 MHz 4: 3400 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP]
           Display Server: X.Org 1.17.2 drivers: ati,fglrx (unloaded: fbdev,vesa,radeon)
           Resolution: 1680x1050@59.88hz
           GLX Renderer: AMD Radeon HD 7800 Series GLX Version: 4.5.13399 - CPC 15.201.1151

```

---

### Post by ajgreeny on 2015-11-26
The default version of fglrx in 15.10 is a big problem at present, as mentioned in the release notes for wily
[https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes#Graphics_and_Display](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes#Graphics_and_Display)
and also in the open bug for the problem.
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888)

It is possible, as you see from the launchpad bug, to use the fglrx version from proposed repos, assuming things have not changed very recently, by enabling those proposed repos, installing just fglrx then disabling the repos again so as to avoid other potential problems from as yet untested packages.

---

### Post by El Zoido on 2015-11-26
You seem to be referring to the "old" problem where fglrx wouldn't play nicely with 4.x kernels.
It would prevent the OS from booting. 
However, it seems this issue was fixed as I can boot just fine - it's the hardware acceleration for videos (e.g. from youtube) which isn't working right for me.

Edit: scrolling through the linked bug report there is a report from one user who seems to have a similar issue. Hmmmm.

---

### Post by El Zoido on 2015-11-27
I've now reinstalled the fglrx packages from AMD, but while vainfo-output now looks good to me:

```
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva info: Found init function __vaDriverInit_0_33
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.38 (libva 1.6.0)
vainfo: Driver version: AMD MMD 1.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileMPEG4Simple            : VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    : VAEntrypointVLD
      VAProfileMPEG4Main              : VAEntrypointVLD
      VAProfileH264Baseline           : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Simple              : VAEntrypointVLD
      VAProfileVC1Main                : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD

```

and youtube-videos in HD aren't just green anymore, I suspect that hardware acceleration is still not working correctly, as CPU usage remains rather high.
Is there any sure-fire way to check whether everything works as intended?

---

### Post by El Zoido on 2015-11-27
I've now reinstalled the fglrx packages from AMD, but while vainfo-output now looks good to me:

```
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva info: Found init function __vaDriverInit_0_33
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.38 (libva 1.6.0)
vainfo: Driver version: AMD MMD 1.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileMPEG4Simple            : VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    : VAEntrypointVLD
      VAProfileMPEG4Main              : VAEntrypointVLD
      VAProfileH264Baseline           : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Simple              : VAEntrypointVLD
      VAProfileVC1Main                : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD

```

and youtube-videos in HD aren't just green anymore, I suspect that hardware acceleration is still not working correctly, as CPU usage remains rather high.
The "use hardware acceleration when available" flag in Firefox is checked.
Is there any sure-fire way to check whether everything works as intended?

---

