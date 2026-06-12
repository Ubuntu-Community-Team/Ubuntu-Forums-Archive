---
title: "jackd....my head aches"
date: 2005-10-30
forum: General Help
---

### Post by kaiowas on 2005-10-30
Hi,

This is my first post here, but i've been reading the forum for about 2 weeks (since i move from windows).

The real problem is that i can get jack server to work, but clients won't connect (ardour, hydrogen, etc).

```
kaio@kaiowas:~$ sudo jackd -d alsa -d
Password:
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
Note: audio device hw:0 doesn't support a 32bit sample format so JACK will try a 24bit format instead
Note: audio device hw:0 doesn't support a 24bit sample format so JACK will try a 16bit format instead
nperiods = 2 for capture
Note: audio device hw:0 doesn't support a 32bit sample format so JACK will try a 24bit format instead
Note: audio device hw:0 doesn't support a 24bit sample format so JACK will try a 16bit format instead
nperiods = 2 for playback

```

so, everything "seems" to be fine (after a lot of errors and reading, i got it to this point), but, clients won't connect. If i start jack with QjackCtl it gives me an error just when it starts, it says "Could not open ALSA sequencer as a client, MIDI patchbay will not be avaible" 

```
13:26:17.304 Patchbay deactivated.
13:26:17.625 Statistics reset.
13:26:17.629 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```

And i got this when i run it from the frontend

```
13:35:36.551 Startup script...
13:35:36.552 artsshell -q terminate
13:35:36.897 Startup script terminated with exit status=256.
13:35:36.917 JACK is starting...
13:35:36.921 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
13:35:36.938 JACK was started with PID=9837 (0x266d).
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
Note: audio device hw:0 doesn't support a 32bit sample format so JACK will try a 24bit format instead
Note: audio device hw:0 doesn't support a 24bit sample format so JACK will try a 16bit format instead
nperiods = 2 for capture
Note: audio device hw:0 doesn't support a 32bit sample format so JACK will try a 24bit format instead
Note: audio device hw:0 doesn't support a 24bit sample format so JACK will try a 16bit format instead
nperiods = 2 for playback
13:35:39.007 Could not connect to JACK server as client.
```

So, i need some advices with this, but i don't want to change to another distro (i've read about others distro designed for audio or media purposes, but i too close to achieve it to give up....at least, it seems so).

Thanks in advance for your attention, from Colombia.

KaIoWaS

---

### Post by kaiowas on 2005-10-31
nobody?

---

### Post by jmcnaught on 2005-10-31
hi,

the reason no clients can connect when you start jackd with sudo is because jackd is running as the root user.  if you were to also run the clients with sudo, they should be able to connect.  note that running your audio programs as the root user might not be a good idea, because any potential bugs will have write access to your entire system, not just your home folder.

what kind of a sound card do you have?  mine is the intel kind that comes integrated on the centrino (i855GM) chipset, and i get the same error about MIDI not being available when i use qjackctl.

i've never tried windows on this laptop, so i don't know if there's no MIDI because a. the card just doesn't have MIDI, b. MIDI is not implemented by the ALSA driver, c. there is a driver/configuration problem or d. something else entirely.

i just ran "jackd -d alsa" from the terminal, and it does exactly the same thing that happens when i do "sudo jackd -d alsa".

have you used MIDI with that soundcard in windows or a different distro/OS?

---

### Post by kaiowas on 2005-11-01
hi jmcnaught!

firts of all, thanks for your reply.

when i run jackd as sudo and the client as well, the client won't recognize the jack server. It's the same if i start ir in the shell or with QjackCtl. My sound card is also an integrated card, the board is uses 845 intel chipset (if i remember well). Curious thing about that midi problem of yours, thats the part i've got right (haven't try it), when i start QjackCtl i can see from the midi connection tab the clients and the midi through, but i've got nothing on the audio tab.

QjackCtl, keeps searching for a client as long as it's opened, but never finds anything.

About your question, my sound card doenst have any midi/serial/midi-sync port, but i've worked with midi using the serial port of the mother-board, but in windows...

I wish i could help more.

Any ideas of how can i make jack work for me?

KaIoWaS

---

### Post by olaf-g on 2005-11-02
I also had problems with jack. Unfortunately ubuntu is not very well tailored to support realtime audio. First you need to 'sudo modprobe snd-seq-oss' to get the sequencer device running. But the main problem is that the realtime features of the kernel require super user rights. So in qjackctrl -> setup I unchecked the options 'realtime' and 'memory lock', that fixed it for me. Of cause jack is not running in realtime now and the sequencers let it feel you :( 

If you run everything (qjackctrl and jack apps) under root, you can leave the options on. But I don't want to let them run under root.

Otherwise you have to setup the kernel's realtime support and assign access rights to the audio group, But I haven't done this yet. There are guides for doing this on the net.

[http://fort.xdas.com/~kor/oss2jack/install.html](http://fort.xdas.com/~kor/oss2jack/install.html)

I have lots of fun with Rosegarden, Hydrogen, Qsynth, ZynAddSubFX but still missing something like reason or at least rebirth.

Good luck

---

### Post by kaiowas on 2005-11-04
Well,

I haven't been able to make jack run smooth, any other suggestion before trying dynebolic or some distro designed for this?....i really don't want to have ubuntu and dynebolic, i just want to make jack work in ubuntu.

Any help is appreaciated

---

### Post by johannes on 2005-11-06
I'm currently writing a document with some guidelines to get jack working in realtime mode. As soon as it's ready I'll probably post it in the Customization category. It will probably be finished in a week. 

[QUOTE=olaf-g]I have lots of fun with Rosegarden, Hydrogen, Qsynth, ZynAddSubFX but still missing something like reason or at least rebirth.[/QUOTE]
Take a look at [Reborn]("http://www.ossh.com/reborn/")

[IMG]http://www.hubbo.se/files/_thb_reborn.jpg[/IMG]

Sadly, the developement of this program was apperantly stopped some years ago because the author was close to getting sued by Propellerheads (the developers of Reson and Rebirth) for making the interface too much like their programs. It works nice in ubuntu, uses the OSS sound driver, is quite undemanding to the system, and you can export your song to wav. It's not as advanced as Reason though...

---

### Post by dolson on 2005-11-13
[QUOTE=johannes]I'm currently writing a document with some guidelines to get jack working in realtime mode. As soon as it's ready I'll probably post it in the Customization category. It will probably be finished in a week. 


Take a look at [Reborn]("http://www.ossh.com/reborn/")

[IMG]http://www.hubbo.se/files/_thb_reborn.jpg[/IMG]

Sadly, the developement of this program was apperantly stopped some years ago because the author was close to getting sued by Propellerheads (the developers of Reson and Rebirth) for making the interface too much like their programs. It works nice in ubuntu, uses the OSS sound driver, is quite undemanding to the system, and you can export your song to wav. It's not as advanced as Reason though...[/QUOTE]


Thanks for that! I made a deb of it and it works great as you said. :)

I don't think I'll use it for my music because I use a lot of hardware and have a Yamaha RM1x to handle more than just drums and bass, but this is still a neat little toy to have.

---

### Post by johannes on 2005-11-19
[QUOTE=dolson]Thanks for that! I made a deb of it and it works great as you said. :)

I don't think I'll use it for my music because I use a lot of hardware and have a Yamaha RM1x to handle more than just drums and bass, but this is still a neat little toy to have.[/QUOTE]

Yeah, it's basically a toy, but I have enjoyed it quite a bit. :) Some of the demo songs included in it are quite amazing. I have tried Rebirth for windows, and I must say that Reborn has even better interface and features.

I read that Rebirth has been released free for downloading by Propellerheads. I really hope this means that the authors of Reborn will be able to continue with the developement. But probably they won't...

---

