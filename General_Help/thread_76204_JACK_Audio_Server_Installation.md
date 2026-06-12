---
title: "JACK Audio Server Installation"
date: 2005-10-14
forum: General Help
---

### Post by unexpected on 2005-10-14
I'm trying to set up the JACK audio server to use Ardour. I've installed jackD and ALSA is installed as well. I'm trying to control JACK through the qJackCtl available from the Ubuntu repository.

When i fire up qJackCtl, i get the following error:

19:14:40.553 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
19:14:40.584 JACK was started with PID=9789 (0x263d).
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
19:14:40.967 JACK was stopped successfully.
19:14:42.702 Could not connect to JACK server as client.

Can anyone help me?

Thanks!

~un

---

### Post by unexpected on 2005-10-15
I think I've narrowed down the problem to the configuration of ALSA. When i google ALSA Though, other sites tell me to run the command

alsaconf...

yet when i try this in Ubuntu, it says "command not found"

Anyone know what's going on?

---

### Post by oblib on 2005-10-21
You need to mess around with the settings in qjack probably. Try running
```

jackd -d alsa -d hw:0
```
from a terminal. If that doesn't error out, then it's just a configuration problem within qjack. If it does, than read the errors and try to make sense of them.

---

### Post by unexpected on 2005-10-25
I tried doing the command you gave. This is the error i get:

```

user@userPC:~$ jackd -d alsa -d hw:0
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa

```

---

### Post by olaf-g on 2005-10-28
I also had problems with jack. Unfortunately ubuntu is not very well tailored to support realtime audio. First you need to 'modprobe snd-seq-oss' to get the sequencer device running. But the main problem is that the realtime features of the kernel require super user rights. So in qjackctrl -> setup I unchecked the options 'realtime' and 'memory lock', that fixed it for me. Of cause jack is not running in realtime now and the sequencers let it feel (hear) you :( 

if you run everything (qjackctrl and jack apps) under root, you can leave the options on. But I don't want to let them run under root.

Otherwise you have to setup the kernel's realtime support and assign access rights to the audio group, But I haven't done this yet. There are guides for doing this on the net.

[http://fort.xdas.com/~kor/oss2jack/install.html](http://fort.xdas.com/~kor/oss2jack/install.html)

Good luck

---

### Post by oblib on 2005-11-01
Looks like something with ALSA then. Mine gives the same results but is okay after "Couldn't open hw:0 for 24bit samples trying 16bit instead."  Perhaps look into changing the frame size or figure out why it can't open the capture channel (that would be an input, like mic-in or line-in). I don't know much about configuring ALSA.

Like olaf-g, I have realtime and No Memory Lock unchecked. In fact all of the parameters in qjack setup are unchecked. Try lowering Frames/Period and see if that does anything, and maybe try fiddling with the Input devices. Try Input Channels = 0.

---

### Post by jamil5454 on 2006-01-29
[QUOTE=oblib]Looks like something with ALSA then. Mine gives the same results but is okay after "Couldn't open hw:0 for 24bit samples trying 16bit instead."  Perhaps look into changing the frame size or figure out why it can't open the capture channel (that would be an input, like mic-in or line-in). I don't know much about configuring ALSA.

Like olaf-g, I have realtime and No Memory Lock unchecked. In fact all of the parameters in qjack setup are unchecked. Try lowering Frames/Period and see if that does anything, and maybe try fiddling with the Input devices. Try Input Channels = 0.[/QUOTE]
Whew that fixed it. Open up qjackctl, click on Setup, and change your frames/period. 512 worked for me.

I've got a Hercules Fortissimo III sound card hooked up through optical out.

---

### Post by guitaristz on 2006-04-22
Well I got the app to start up: Jack audio connector but I'm not having much luck with the rest of it. I did everything as told above but ran into a bit of a snag with that DOS like window suggested by the other site with the Realism module stuff. I hoping to use this a studio machine and would like to get the sound driver fine tuned.
I'm at like day 2 here with Unbutu, so thanks, E

PS is it possible to get this Crazy Badger-thing release preconfigured for audio heavyweights?

---

### Post by FarEast on 2006-05-04
Hi;) ,

For those who want to use jack, it is worth visiting the wiki below.
[http://ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation](http://ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation)

And there is a good gui for jack audio server called 'qjackctl' which
you can install with APT.

---

