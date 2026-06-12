---
title: "Jack"
date: 2007-05-14
forum: General Help
---

### Post by xstevex on 2007-05-14
hey

i was running jack and it was working fine for a while, and yet after reboot it stopped working. it gives out this:

>  19:05:20.874 Patchbay deactivated.
19:05:20.887 Statistics reset.
19:05:20.908 MIDI connection graph change.
19:05:21.098 MIDI connection change.
19:05:28.546 Startup script...
19:05:28.546 artsshell -q terminate
sound server terminated
19:05:28.798 Startup script terminated successfully.
19:05:28.798 JACK is starting...
19:05:28.798 /usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Chw:0 -P/dev/dsp -i4
19:05:28.799 JACK was started with PID=10404 (0x28a4).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... /dev/dsp|hw:0|1024|2|44100|4|0|nomon|swmeter|-|32bit
ALSA lib control.c:910:(snd_ctl_open_noupdate) Invalid CTL /dev/dsp
control open "/dev/dsp" (No such file or directory)
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: cannot set channel count to 4 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
19:05:28.818 JACK was stopped successfully.
19:05:28.819 Post-shutdown script...
19:05:28.819 killall jackd
jackd: no process killed
19:05:29.027 Post-shutdown script terminated with exit status=256.
19:05:30.871 Could not connect to JACK server as client. Please check the messages window for more info. 

can anyone help me?

(i'm running ubuntu studio)

---

### Post by genbod on 2007-05-17
I am also running ubuntustudio.  I have and audigy LS Sound Blaster card.  Jack originally ran but I could get no audio from anything connected to it.  Now I can't the server to start at all.  Does anyone have pointers on some good Jack documentation and configurationg help for sound cards?  I have looked on their site, and the included documentation and there is nothing to seems to spell out the magic that is Jack.  Please Help!!!

---

