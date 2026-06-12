---
title: "Firefox is extremely sluggish and flash notworking"
date: 2016-05-16
forum: General Help
---

### Post by philinux on 2016-05-16
Some might say flash not working is good lol. But I need it for the odd site. Tried uninstalling etc etc.
This is 16.04 version ubuntu mate clean install.

Firefox, well, unbelievable lag. Clean install of this too. i.e.new profile.

Machine is a sempron 1.2 gig with about 1.2 gig memory. Other stuff runs fine like libre office.

Any ideas.

---

### Post by vasa1 on 2016-05-16
Have you set Flash as click-to-play (or something equivalent)?

In my *about:config*, I have```
plugins.click_to_play;true
```

---

### Post by cbraxton on 2016-05-16
Unfortunately the only way to get decent flash support on Linux is to use one of the Google Chrome family of browsers.  Chromium is available in the Ubuntu repositories. I've been using Slimjet, which is based on Chromium but includes more privacy and security options such as being able to easily disable WebRTC. It also includes a built-in ad blocker which seems to work pretty well.

[http://www.slimjet.com/](http://www.slimjet.com/)

The only problem I've had is that Slimjet will occasionally bomb out on startup out saying it can't open its local database. The "fix" is to delete the file *"~/.config/slimjet/Default/Web Data"* when this happens. I have a command for this set up up as an alias in ~/.bashrc. 

```

alias sjfix='rm ~/.config/slimjet/Default/Web\ Data'

```

Also since Slimjet is not in the repositories, or available in a PPA as far as I know, you need to manually install updates.

I still prefer Firefox overall but it's stuck with an ancient version of Flash that never worked all that well on Linux. (Firefox is also agonizingly slow initializing add-ons. Slimjet is much faster.)

---

### Post by bapoumba on 2016-05-16
Well, I had not tried playing flash content yet since I installed ubuntu-mate. I have ubuntu-restricted-extras installed.

For ex [http://www.bfmtv.com/mediaplayer/live-video/](http://www.bfmtv.com/mediaplayer/live-video/) wont play, I have a white triangle "Play video" over a black background that does not do a thing. To note, [https://helpx.adobe.com/flash-player.html](https://helpx.adobe.com/flash-player.html) shows the animation. The latest shown here is the one I got : [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) Shockwave Flash 11.2 r202.
I've read some content (such as the one I tried above, ie some content from French TV) require pipelight but I cannot be too bothered about it, youtube and dailymotion work although the fans quickly start blowing up. This VM had 3GB mem, 2 cores and 128MB video mem with 3D acceleration (max possible mem).

Which site cannot play for you for ex ?

Edit : once again I'm hit by my devils, search and experiment with an open tab that I do not reload before posting, sorry :)

---

### Post by $yl9pAR%t on 2016-05-16
Check your CPU flags:

```
inxi -f
```

SSE2 is needed for Flash.

---

### Post by vasa1 on 2016-05-16
Even if Firefox doesn't play nice with some Flash sites, that doesn't explain the overall sluggishness unless it's with specific reference to those Flash sites :confused:

---

### Post by bapoumba on 2016-05-16
> **mefisto888 said:**
> Check your CPU flags:

```
inxi -f
```

SSE2 is needed for Flash.

sse2 here. As I said, some TV web sites here are known to require Microsoft plugins, which I wont get into :)

---

### Post by philinux on 2016-05-16
Ok progress on Firefox. From [https://sites.google.com/site/easylinuxtipsproject/firefox](https://sites.google.com/site/easylinuxtipsproject/firefox)
Section 8. 
Not at machine now to try flash suggestions.
Thanks for replies

---

### Post by $yl9pAR%t on 2016-05-16
When it comes to "extremely sluggish" you can try to switch from Marco Software Compositor (by default in Ubuntu MATE) to No Compositor.

---

### Post by QLee on 2016-05-16
When I go to the Adobe site with firefox 46.0 I see, "You have version 21,0,0,242 installed."

I can see the Flash on at least one of the sites that bapoumba mentioned. (I only checked one.)

Running Ubuntu 16.04.  This is what I installed for flash.

> 
@Atlas-Ubu16:~$ apt show adobe-flash-properties-gtk
Package: adobe-flash-properties-gtk
Version: 1:20160512.1-0ubuntu0.16.04.1
Priority: optional
Section: web
Source: adobe-flashplugin
Maintainer: DL-Flash Player Ubuntu <FlashPlayerUbuntu@adobe.com>
Installed-Size: 492 kB
Provides: adobe-flash-properties
Depends: adobe-flashplugin (= 1:20160512.1-0ubuntu0.16.04.1), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.3), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.11.94), libfreetype6 (>= 2.2.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.14.0), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), libpangoft2-1.0-0 (>= 1.14.0)
Download-Size: 113 kB
APT-Manual-Installed: no
APT-Sources: [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner amd64 Packages
Description: GTK+ control panel for Adobe Flash Player plugin
 Adobe® Flash® Player is a cross-platform, browser-based application runtime
 that provides uncompromised viewing of expressive applications, content, and
 videos across browsers and operating systems.
 .
 This package provides the GTK+ control panel for the Flash plugin.

-------------

@Atlas-Ubu16:~$ apt show adobe-flashplugin
Package: adobe-flashplugin
Version: 1:20160512.1-0ubuntu0.16.04.1
Priority: optional
Section: web
Maintainer: DL-Flash Player Ubuntu <FlashPlayerUbuntu@adobe.com>
Installed-Size: 38.1 MB
Provides: flashplugin-nonfree
Depends: wget, fontconfig, libatk1.0-0 (>= 1.12.4), libc6 (>= 2.11), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.11.94), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:3.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.24.0), libnspr4 (>= 2:4.9-2~) | libnspr4-0d (>= 1.8.0.10), libnss3 (>= 2:3.13.4-2~) | libnss3-1d (>= 3.12.0~beta3), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), libpangoft2-1.0-0 (>= 1.14.0), libstdc++6 (>= 4.3), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxrender1, libxt6
Recommends: adobe-flash-properties-gtk (= 1:20160512.1-0ubuntu0.16.04.1) | adobe-flash-properties-kde (= 1:20160512.1-0ubuntu0.16.04.1)
Suggests: firefox | chromium-browser, x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5), libnspr4-0d, libnss3-1d
Conflicts: flashplayer-mozilla, flashplugin (<< 6), flashplugin-downloader, flashplugin-installer, xfs (<< 1:1.0.1-5)
Replaces: flashplugin (<< 6)
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash Plugin ([http://www.adobe.com](http://www.adobe.com))
Npp-Name: Adobe Flash Plugin
Download-Size: 10.3 MB
APT-Manual-Installed: yes
APT-Sources: [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner amd64 Packages
Description: Adobe Flash Player plugin
 Adobe® Flash® Player is a cross-platform, browser-based application runtime
 that provides uncompromised viewing of expressive applications, content, and
 videos across browsers and operating systems.
 .
 This package provides plugins compatible with both Chromium and Mozilla based
 web browsers

---------

@Atlas-Ubu16:~$ apt show browser-plugin-freshplayer-pepperflash
Package: browser-plugin-freshplayer-pepperflash
Version: 0.3.4-3
Priority: optional
Section: multiverse/web
Source: freshplayerplugin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Vincent Danjean <vdanjean@debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 1,138 kB
Depends: libasound2 (>= 1.0.18), libavcodec-ffmpeg56 (>= 7:2.4) | libavcodec-ffmpeg-extra56 (>= 7:2.4), libavutil-ffmpeg54 (>= 7:2.4), libc6 (>= 2.14), libcairo2 (>= 1.2.4), libevent-2.0-5 (>= 2.0.10-stable), libevent-pthreads-2.0-5 (>= 2.0.10-stable), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:3.0), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.31.18), libgtk2.0-0 (>= 2.24.0), libpango-1.0-0 (>= 1.22.0), libpangocairo-1.0-0 (>= 1.14.0), libpangoft2-1.0-0 (>= 1.14.0), libpulse0 (>= 0.99.1), libssl1.0.0 (>= 1.0.0), libstdc++6 (>= 5.2), libv4l-0 (>= 0.5.0), libva-x11-1 (>= 1.0.3), libva1 (>= 1.2.0), libvdpau1 (>= 0.2), libx11-6, libxcursor1 (>> 1.1.2), libxrandr2 (>= 2:1.2.0), libxrender1bapoumba
Recommends: pepperflashplugin-nonfree
Homepage: [https://github.com/i-rinat/freshplayerplugin](https://github.com/i-rinat/freshplayerplugin)
Download-Size: 339 kB
APT-Manual-Installed: yes
APT-Sources: [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 Packages
Description: PPAPI-host NPAPI-plugin adapter for pepperflash
 The main goal of the project is to get PPAPI (Chrome) plugins
 working in Firefox (and any other web-browser supporting NPAPI plugins).
 It implements a wrapper which behaves like
 browser to PPAPI plugin and implements NPAPI plugin interface
 for browser to use.
 .
 This particular implementation doesn't implement any sandboxing,
 which means any malicious code can break through plugin security
 as there are no additional barriers.  This is the same level of security as
 NPAPI Flash have.
 .
 Flash plugin for Linux provided by adobe stopped at version 11.2; for
 chrome/chromium users there is pepperflash plugin but it's not supported by
 firefox/iceweasel/other browsers.
 .
 This package allows one to use the Pepper Flash plugin from Chrome
 in NPAPI web browsers.

-----------

@Atlas-Ubu16:~$ apt show pepperflashplugin-nonfree
Package: pepperflashplugin-nonfree
Version: 1.8.2ubuntu1
Priority: optional
Section: multiverse/web
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Bart Martens <bartm@debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 42.0 kB
Pre-Depends: ca-certificates
Depends: debconf | debconf-2.0, wget, gnupg, libatk1.0-0, libcairo2, libfontconfig1, libfreetype6, libgcc1, libglib2.0-0, libgtk2.0-0 (>= 2.14), libnspr4, libnss3, libpango-1.0-0 | libpango1.0-0, libstdc++6, libx11-6, libxext6, libxt6, libcurl3-gnutls, binutils
Suggests: chromium-browser, ttf-mscorefonts-installer, ttf-dejavu, ttf-xfree86-nonfree
Conflicts: chromium-browser (<< 37.0.2062.120-4), libflash-mozplugin
Homepage: [http://wiki.debian.org/PepperFlashPlayer](http://wiki.debian.org/PepperFlashPlayer)
Download-Size: 11.2 kB
APT-Manual-Installed: no
APT-Sources: [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 Packages
Description: Pepper Flash Player - browser plugin
 This package will download Chrome from Google, and unpack it to make the
 included Pepper Flash Player available for use with Chromium.  The end user
 license agreement is available at Google.
 

HTH

---

### Post by philinux on 2016-05-20
> **mefisto888 said:**
> Check your CPU flags:

```
inxi -f
```

SSE2 is needed for Flash.

```
inxi -f
CPU:       Single core AMD Sempron 2200+ (-UP-) cache: 256 KB
           speed: 1505 MHz (max)
           CPU Flags: 3dnow 3dnowext 3dnowprefetch apic cmov cx8 de fpu fxsr
           mca mce mmx mmxext mp msr mtrr pae pat pge pse pse36 sep sse
           syscall tsc vme vmmcall

```
Got sse. flash was working before on this machine under 10.04.

---

### Post by $yl9pAR%t on 2016-05-20
The story about sse2 and support for linux flash version started 3 or 4 years ago if I remember right. The last working without sse2 version of flashplayer was probably 11.2.202.236. I used to use workaround but it was always a security risk and now after a few years this old flash, has probably also functional deficiencies.

---

### Post by mörgæs on 2016-05-21
Correct. There is a [Flash player]("http://ubuntuforums.org/showthread.php?t=2130640&p=12565189&viewfull=1#post12565189") available for computers older than SSE2 but consider the entire system breached if you install it.

---

