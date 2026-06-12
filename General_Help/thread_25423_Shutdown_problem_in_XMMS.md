---
title: "Shutdown problem in XMMS"
date: 2005-04-10
forum: General Help
---

### Post by sinbad782 on 2005-04-10
Hi,
  I have a problem that crops up when clicking on XMMS in order to close it after playing an internet radio stream (shoutcast etc...). The app just seems to hang and doesn't disappear from the desktop. 

I have to open a terminal window and issue a 'killall xmms' in order to get rid of it. 

Anyone else having this problem?

PJS

---

### Post by clparker on 2005-04-10
I used to use XMMS until hoary's Rythymbox's upgrade made more sense.

---

### Post by sinbad782 on 2005-04-10
Update - I changed the sound driver in XMMS to esound and it now seems to be working fine. Strange that ALSA doesn't seem to work.....

---

### Post by lordlinux on 2005-04-11
Yeah.. that worked perfect for me 2!! Thanks a lot!

---

### Post by dusu on 2005-04-11
[QUOTE=sinbad782]Update - I changed the sound driver in XMMS to esound and it now seems to be working fine. Strange that ALSA doesn't seem to work.....[/QUOTE]

If you want ALSA to work, you should prevent esound to be run on startup (ie you have to disable the sound server on startup in the sound options in Gnome), and then it will work.

---

### Post by sinbad782 on 2005-04-11
cool - I'm actally using KDE, but I installed Gnome first and so things are probably all mixed together. I will try setting sound server to not load at startup in the KDE control center and see if that works too.

---

