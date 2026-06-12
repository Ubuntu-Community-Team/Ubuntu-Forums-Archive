---
title: "Sound and MP3 problem"
date: 2004-11-18
forum: General Help
---

### Post by hitchhiker on 2004-11-18
Hi, I've upgraded ubuntu through synaptic to hoary level and followed the multimedia guide before upgrading.

I'm having trouble with my sound. Desktop sounds play fine. 
Rythmbox radio plays fine.  Gxine plays videos (AVI, WMV) and MP3's just fine, sound is good.

Mplayer won't play sound, either Mp3 or video. The video can be seen but no sound.
It gives the error - Could not open/initialize audio device -> no sound.

Rythmbox will not play MP3's, they appear greyed out in file listings within Rythmbox.

XMMS will allow me to add MP3's to the play list but when I hit play it freezes and I have to kill the application.

I've also installed UT2004 which plays fine except there's no sound.

Help!

HH.

---

### Post by sfw5000 on 2004-11-18
In terms of xmms and rythmbox you have to install the mp3 capability. It's left out by default because of lisencing issues. In synaptic search for rythmbox and xmms and there should be packages like xmms-mp3. In terms of mplayer... I don't know, does it have a volume slider that is turned down? sometimes you also need to disable system sounds for other sounds to work, because multiple programs have trouble playing sound simultaniously.

---

### Post by hitchhiker on 2004-11-18
As far as Rythmbox goes, I've installed gstreamer0.8 and gstreamer0.8-mad and various other gstreamer0.8 plugins.

HH.

---

### Post by rbrimhall on 2004-11-18
Set the Mplayer audio preferences to alsa or OSS... this worked for me.

---

### Post by hitchhiker on 2004-11-18
XMMS now works, hand't configured the ALSA driver properly.

Mplayer Audio driver list doesn't show an ALSA driver, not sure why.

Rythmbox still won't play MP3's.

HH.

---

