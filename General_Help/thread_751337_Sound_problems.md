---
title: "Sound problems"
date: 2008-04-10
forum: General Help
---

### Post by CShadowRun on 2008-04-10
Basically it seems like certain applications steal sounds from other applications, it's very annoying.
I did something with alsamixer, although i'm not exactly sure what i did, it fixes most of the problems, except xchat and flash.

Before i fiddled with alsamixer, i had intermittant problems. The only 100% one i could reproduce was running VLC and totem at the same time, this didn't work (And everyone else i've asked reports that it works for them.)

But since i've fiddled with alsamixer, that seems to work now. The remaining problems are...

If i have flash running, i can't use VLC to listen to music.
If i have VLC running, i can't hear flash.
xchat can't make any sounds at all.

I have an integrated intel ich5 sound card, using ALSA (According to the volume control dialog)

I'm using ubuntu 8, however i had exactly the same problem with ubuntu 7 (I was told upgrading would fix the problem, it didn't)

---

### Post by CShadowRun on 2008-04-10
if i can't get this to work i'm gonna have to go back to windows :(
It's really important that my sound works. I've been trying to get this to work for around 6 hours now.

---

### Post by CShadowRun on 2008-04-10
Fixed it, pulseaudio was actually causing all this trouble. I did killall pulseaudio. Sound magically fixed itself :D

Uninstalled pulseaudio, everything works now.

As for xchat, it can't play MP3's. I pointed it at a wav. It works now. :D

Yay, no more windows :)

---

