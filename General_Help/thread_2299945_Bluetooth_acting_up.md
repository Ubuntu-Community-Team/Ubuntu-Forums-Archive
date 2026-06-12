---
title: "Bluetooth acting up"
date: 2015-10-22
forum: General Help
---

### Post by Evil Wayz on 2015-10-22
I switched from Linux Mint to Ubuntu because the latest flavor of Mint didn't recognize my dongle.  As of last night, my bluetooth audio (AD2P profile)  works for about fifteen minute, then the sound cuts off.  I then have to switch back and forth between bluetooth and built in audio a couple times before I can get any sound at all.  THen I pair the device again and it work sfine for about another 15 minutes.  I have three headsets, it does this with all of them.  THis also happened in three different video players, Totem/mplayer, VLC player, and SMPlayer. 

Is this a bluetooth issue, an audio issue, or both?  I've been watching a movie with built in audio for almost an hour with no problems, so I suspect there's a log I need to read to find out what the problem is.  I just don't know where to start. 

So that's where you good folk come in.  Little help, please?

---

### Post by Evil Wayz on 2015-10-23
Ok its not just bluetooth.  I bought a new dongle, and everything worked great until thirty seconds ago.  Youtube stopped working, and gnome mplayer and vlc won't play.  It's like everything audio is stuck at once.  I can still surf the web and such but pulseaudio has crapped the bed near as I can figure.  Switching back to "built in audio" gets me sound back.

---

### Post by Evil Wayz on 2015-10-23
I am not using the kernel that came with 14.04, I'm using a much higher stable.  Could this be the problem?

---

### Post by Evil Wayz on 2015-10-25
ANyone?  Getting to use Bluetooth for fifteen minutes at a time really sucks.

---

### Post by Evil Wayz on 2015-10-29
Turns out the problem was a failing USB hub, when the hub the dongle was attached to temporarily unmounted itself, the bluetooth connection was lost.

---

