---
title: "Xfinity and Linux?"
date: 2017-01-07
forum: General Help
---

### Post by Autodave on 2017-01-07
Trying to get my Xfinity to play TV on my Linux machine. Does anyone have any way of getting this to work?  I saw someone that posted about using WINE, but exactly how do you do it that way. I tried WINE and installing IE8, but had all kinds of errors and couldn't get it to work.

Any help would be greatly appreciated.

---

### Post by efflandt on 2017-01-10
Do you know what they use to play the video? For example Netflix used to require antiquated Microsoft Silverlight and the only thing that worked for that was a Netflix app someone put together using wine and gecko (mozilla) browser as an Internet Explorer substitute. Fortunately Neflix does HTML5 now with works using Google Chrome without doing anything special. Hulu just used flash, but then implemented a DRM which Linux Chrome could not do, and Firefox would if an obsolete program called hal was installed (not sure if hal is still required or if Firefox or flash now handle the DRM).

But I have never gotten pipelight (which uses wine) to work in Firefox for anything that required MS Silverlight.

---

### Post by Autodave on 2017-01-10
When I try to use either Firefox or Chrome, it tells me that I have an outdated Flash version. However, when I go to Adobe's sight and check, I have the most current flash installed.

---

### Post by oldfred on 2017-01-10
I have never gotten it to work with Firefox or Chromium.
The Linux flash version is current but too old. And new one just updated for Linux mentions it will not support the DRM or restrictions vendors want to prevent copying of downloaded videos.

I gave up and installed a small Windows 8 now 10 system. But sometimes it works and others it seems Windows 10 goes off to run some task and system hangs for 20 or 30 sec. 
My early model Amazon fire stick with not much real hardware as it all is in a tiny stick works without issue on Amazon videos in HD, so not my Wi-Fi.

---

### Post by Autodave on 2017-01-10
I wonder if anyone has been able to get it to work through WINE?  I tried the other day, but couldn't even get IE8 to work in WINE.

---

### Post by QIII on 2017-01-10
I see people who claim to have gotten it to work.  I never have and somewhat doubt the veracity of those claims.

Like oldfred, I just set up a Windows machine.

---

### Post by Autodave on 2017-01-19
OK: good news!!!  Gonna answer my own question here so that others can get Xfinity TV and Linux to play nice together.  After much Googling and putting different things together, I got it to work on 2 different machines.

Install WINE and then install Play On Linux. Open Play On Linux and click on INTERNET programs. Choose Firefox and let Play On Linux find and install it. When you are either doing this or going into Firefox, you will be asked whether you want to install *Flash *and *Shockwave. *Do _**NOT **_install Shockwave: just install Flash! When that is complete, exit Play On Linux. You should now have a Firefox icon on your screen that wasn't there before. Just click on the icon, Play On Linux will open Firefox for you. Go the the Xfinity website and log in.

Sometimes, on one machine, I still will get that message about newer version of Flash is needed, but that message disappears in a few seconds and all is well.

Enjoy!

---

### Post by Dennis N on 2017-01-19
Yes, this worked for me too. Thanks for the tip. Several tries in the past had failed - I could install Firefox for Windows, but the flash player install always failed with an unspecified error. 

Comment:
I don't think one needs to install Wine first, since this installation of Firefox through Play on Linux installed a newer version of Wine in another folder. I had version 1.6.2 installed already from the Ubuntu repository, and the P.O.L. installation added version 1.7.22. 

We'll see how this goes in the long term - through updates and such. Right now, it is the current version of Firefox and Flash Player.

---

### Post by ramakin on 2017-03-12
I've had issues when xfinity updated to the latest flash but now xfinity adverts is does not support linux os or any flavor there of. so no tv or movies but everything else works.

---

### Post by somehockeyguy on 2017-10-18
Hi, is anyone out there able to get xfinity working on linux?  I tried play on linux, but for some reason firefox crashes and it gives an error. I've tried a number of other things, but it seems that the biggest issue is that they still use flash player to actually stream the videos.  They can obviously stream them without flash player bc I can stream them from the xfinity app on my phone.  Is anyone using xfinity and kodi?  I really don't want to have to run windows, but that is looking like the easiest solution for this.  Then again, I watch very little on xfinity to begin with.

---

### Post by Autodave on 2017-10-18
I had not tried it for quite awhile since this machine dual boots with Win10.  I just tried re-installing it and since Firefox no longer supports Flash, I had no luck getting it to work either.

---

