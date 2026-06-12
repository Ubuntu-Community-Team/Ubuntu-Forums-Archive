---
title: "Problem with mplayer"
date: 2005-09-26
forum: General Help
---

### Post by Midget on 2005-09-26
I have tried to install mplayer using the following guide: [http://ubuntuguide.org/#mplayer]("http://ubuntuguide.org/#mplayer")

Everything worked fine during the installation, but whenever I try to play a movie/song, mplayer stops:

```

midget@strip:~/mp3/postgirobygget/melis$ mplayer 01-Postgirobygget-Bohemen_leve.mp3
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Intel Pentium M Banias (Family: 6, Stepping: 5)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Ikke tilgang
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : Ingen slik fil eller filkatalog
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: Ingen slik fil eller filkatalog
Failed to open LIRC support.
You will not be able to use your remote control.
Playing 01-Postgirobygget-Bohemen_leve.mp3.
Cache fill:  0,00% (0 bytes)    Audio file detected.
Clip info:
 Title: Bohemen leve
 Artist: Postgirobygget
 Album: Melis
 Year:
 Comment:
 Track: 1
 Genre: Unknown
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, 16 bit (0x10), ratio: 16000->176400 (128,0 kbit)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
Checking audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 44100 hz, little endian signed int
AF_pre: 44100Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default

```

Does anyone have a solution to this problem?
If it's any help: I have a fresh installation of Ubuntu Hoary.

---

### Post by KingBahamut on 2005-09-26
just a thought (Im pretty close to brain dead right now), you may wish to add that line to /etc/rc.local (the echo 1024 > /pro...), i believe the profile
is trying to modify a system setting with your user access rights, using the
rc local script should do the modification using the system permissions..........

---

