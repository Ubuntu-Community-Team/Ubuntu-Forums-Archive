---
title: "xubuntu not remembering application settings"
date: 2015-04-26
forum: General Help
---

### Post by chellrose on 2015-04-26
I'm running 64-bit Xubuntu 15.04 (dual-booted with Win7).  It isn't properly remembering certain settings for certain applications.  The two biggest offenders thus far are AMD Catalyst (for my graphics card, an AMD R7 240) and Firefox.

1. Catalyst:  I use 2 monitors in an extended display.  When I reboot the computer, the desktop is cloned on both monitors.  I go into the Catalyst control center and it shows that it is configured for extended display, however, the desktop is cloned instead.  I have to go into Catalyst upon every boot and click "Apply" to make the desktop extended.

2. Firefox plugin settings:  I have Adobe Flash in Firefox set to "Always Ask"; however, Flash videos on websites play automatically when the site is opened.  In my Firefox preferences, it continues to show the proper settings (Always Ask), but I can't seem to stop it from just playing automatically.  It worked properly in the past, but Xubuntu has installed several updates since then (both Firefox and native Xubuntu OS applications).  It works properly on my Firefox in Windows 7, however.  I'm using Firefox 37.0.2 at present.

I had these problems on Xubuntu 14.10 as well.

---

### Post by kerry_s on 2015-04-26
1) Catalyst is not xfce, have you tried setting the same setting in settings manager-> display

2) flash is on it's way out, so i would guess the sites still showing video could be using html5 video. suggest looking for a extension to help with stopping playing of media

---

### Post by chellrose on 2015-04-26
Thanks, kerry_s.

1.  Yes, I tried xfce's display manager first.  That one was even worse; I couldn't get it to accept my (physical) monitor configuration and every time I tried to change the monitor setup, it jacked up the resolution on one of the monitors.  This is what prompted me to install Catalyst in the first place.

2.  I've confirmed that the videos are flash; when I visit the same sites in Windows, the video shows that I have to activate Adobe Flash in order to play it.

---

### Post by kerry_s on 2015-04-27
well there are still a few bugs in 15, but if we wanted stable we'd be running 14lts 

not, sure what else to try, dual monitors work perfectly for me, but my vid card is intel

flash is flash, unpredictable on all browsers & platforms. lol

---

### Post by chellrose on 2015-04-27
Lol.  Well, hopefully the bugs will get fixed soon.  Thanks for your suggestions.

---

