---
title: "Sound Dissapeared This Morning?"
date: 2005-10-16
forum: General Help
---

### Post by jpoe on 2005-10-16
Hi all,

I was just wondering if anyone else is experiencing problems with their sound?  I woke up this morning, did 4 upgrades that were waiting for me (i belive they were curl, wget, some ssl library, and something else) and I noticed that I have no sound.

The only other thing I can remember possibly doing since my sound poofed was installing totem-xine (before I was using totem-gstreamer).  I also tried going back to gstreamer and nothing (I'm not sure if this is even remotely relevant ... its just I installed the xine last night and wanted to be sure to let you know).

Also, its not like a normal sound card error because everything looks like its playing fine visually (ie, when I load up songs on rhythembox or amarok or beep-media-player, all of the equializers bounce around happily with no errors) .. almost as if my speakers just became unplugged (grin, I checked, their not .. PCM and Master etc volumes all up as well, and nothing muted .. ) .. 

Any ideas great gods of ubuntu knowledge?

Thnx...

Oh yeah, not sure if this helps, but just in case, I have an NFORCE4 AMD64 and some proc output:

```

jpoe@samara:~$ cat /proc/asound/cards
0 [CK804          ]: NFORCE - NVidia CK804
                     NVidia CK804 with ALC850 at 0xd2003000, irq 22
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 10
jpoe@samara:~$ cat /proc/asound/pcm
00-00: Intel ICH : NVidia CK804 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : NVidia CK804 - MIC ADC : capture 1
00-02: Intel ICH - IEC958 : NVidia CK804 - IEC958 : playback 1
jpoe@samara:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.9 (Sun May 29 07:31:02 2005 UTC).

```

---

### Post by nuopus on 2005-10-16
[quote=jpoe]Hi all,

I was just wondering if anyone else is experiencing problems with their sound? I woke up this morning, did 4 upgrades that were waiting for me (i belive they were curl, wget, some ssl library, and something else) and I noticed that I have no sound.

The only other thing I can remember possibly doing since my sound poofed was installing totem-xine (before I was using totem-gstreamer). I also tried going back to gstreamer and nothing (I'm not sure if this is even remotely relevant ... its just I installed the xine last night and wanted to be sure to let you know).

Also, its not like a normal sound card error because everything looks like its playing fine visually (ie, when I load up songs on rhythembox or amarok or beep-media-player, all of the equializers bounce around happily with no errors) .. almost as if my speakers just became unplugged (grin, I checked, their not .. PCM and Master etc volumes all up as well, and nothing muted .. ) .. 

Any ideas great gods of ubuntu knowledge?

Thnx...[/quote]

A friend of mine had an issue where he was trying out some new applications and one of them changed the PCM volume by default and the tray applet controls master volume. The master volume only controls volume relative to PCM, so you must make sure PCM is up. I would check this first. Right-click on the volume control applet and click Open Volume Control.

---

### Post by jpoe on 2005-10-16
Yeah, I have often had that problem; so that was one of the first things I checked... Its not the culpret this time.  Thanks for the response though,

James

---

### Post by jpoe on 2005-10-16
Hey guys,

Just wanted to update you on what the problem was....

Apparently, even with tripwire, firewall, closed services, Nessus testing, etc, etc .... My system wasn't totally secure ...

...My @#*()@# cat chewed through my speaker wire .. =) .. I checked both ends before I posted earlier, but apparently somewhere behind my machine he had chewed all the way through it ...

Ugh .. I wonder if I can still file a bug report?  .. ;)  .. Anyone want a cat?

Sorry for the time,

James

---

