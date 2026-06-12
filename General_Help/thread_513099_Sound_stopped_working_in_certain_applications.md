---
title: "Sound stopped working in certain applications"
date: 2007-07-30
forum: General Help
---

### Post by Famicommie on 2007-07-30
Running Feisty, soundcard is an Audigy 2 Value

Several days ago, after about 3 weeks of uptime, my sound just plain stopped working. It was systemwideI tried killall esd and restarting esd. I tried reloading the also module. I tried restarting alsa-utils. I screwed around with alsamixer muting and unmuting every permutation of channels I could think of. No luck on anything. So, I trusted to my Windows roots and simply rebooted the machine. Login bells - check. Audacious working - check. Cool, everything seemed alright.

Later that day I went to play Unreal Tournament in wine, and there was no sound. Hm. Popped open MPlayer - sound working. Viewed a flash video - sound working. ZSNES - sound working. Tried wine again, but this time issued the command "killall esd && esd && aoss wine UnrealTournament.exe". Still no sound. I figured: "Hey, maybe it is just some problem with wine. So I ran winecfg and tried every possible permutation of using ALSA and OSS, both with and without driver emulation. Still no sound.

I happen to have a copy of the linux version of Tribes II - no sound. I also have the linux game Uplink - no sound. So of course, at this point I started to get a little frustrated. Opened up Fallout with wine - no sound. Opened up Fallout with Cedega and there was sound! UnrealTournament had sound in Cedega as well!

The only thing I can think of is that I muted or unmuted something in alsamixer that has thrown my sound topsy-turvy. But, for the life of me, I can't remember what it was, and now I'm worried that I'll lose ALL sound if I fire up alsamixer again and try playing with settings. Does anyone have any idea what it could be that is keeping sound from working in some apps but not giving any problems with other apps?

---

### Post by Paul S on 2007-07-30
Whenever I run into the problem you're describing, I always hunt around and eventually find some volume control is reduced.  For example, in addition to alsamixer, I also have kmix running in my system tray (in KDE).  When I run realplayer, it has it's own volume control, so I have to remember to set it up too.  Also, my speakers have volume too.  And, lastly, my keyboard has shortcuts to raise / lower volume.  So, there's a lot to check on my system when sound stops, and I always eventually find something is throttled.  I don't run wine or games like you, but if you check the docs you may find some keyboard shortcut is cutting the volume back or off.

regards,

---

### Post by Famicommie on 2007-08-04
Thanks Paul S. I checked all of my volume controls and everything was alright.

I lost power the other day, which (of course) turned of my computer. When I brought it back up, sound was working all across the spectrum.

IIRC, I lost sound last time when I opened up Cave Story in Wine while Audacious was running. Even after closing Audacious, killing esd, and restarting alsa-utils the sound didn't come back, which is a tad perplexing. But at least I think I have the problem narrowed down to Audacious conflicting with other applications. I haven't tried to recreate it yet so I'm not sure which channel is responsible, but at least I have a workaround.

My guess would have to be that OSS drivers are responsible. After all, Wine and Tribes 2 use the OSS drivers and they were two of the applications giving me trouble. Not sure about Uplink as it is a more recent game, but OSS could verily be the culprit.

---

