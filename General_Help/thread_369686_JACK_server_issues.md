---
title: "JACK server issues"
date: 2007-02-24
forum: General Help
---

### Post by Doovoo on 2007-02-24
Well, my Jack server won't start, which is really a problem, because I use lots of apps that need it. I first encountered the problem when Ardour, Jackrack, etc all gave me a "Could not connect to Jack server" error on startup. Then I tried to start it...

"jackstart" returns
```
jackstart: cannot get realtime capabilities, current capabilities are:
           =ep cap_setpcap-ep
    probably running under a kernel with capabilities disabled,
    a suitable kernel would have printed something like "=eip"

back from read, ret = 1 errno == Success
jackstart: could not give capabilities: Operation not permitted
```
then shows the jackd stuff.

I'm somewhat confused by this. Can someone help me out?

Thanks.

---

### Post by Doovoo on 2007-02-25
Alright, so jackstart is still broken, and I've read that it's just a broken command so I'm just using "jackd" and it's starting fine. Ardour now has no problem connecting to jack, but other applications like jackrack, jackeq, jack-dssi-host, still cannot.

Is there a way to set my jack settings to default or something?

---

### Post by christhemonkey on 2007-02-25
Try using qjackctl to control jack. Gives a nice graphical interface to configure all the options and connect various clients.

Also trying starting jackd like this and posting its output:
```
jackd -R -d alsa -d hw:0
```

---

### Post by Doovoo on 2007-02-25
When I start qjackctl it gives me this error

```
Could not open ALSA sequencer as a client.
Midi Patchbay will not be available.
```

And the jackd command returns 

```
$ jackd -R -d alsa -d hw:0
jackd 0.101.1
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

---

### Post by christhemonkey on 2007-02-25
The first error:
> Could not open ALSA sequencer as a client.
Midi Patchbay will not be available.
Just means that the alsa midi sequencer module has not been loaded into the kernel.
This should be a non-critical error (but you wont have midi in jack)
To stop it, just load the snd-seq module:
```
sudo modprobe snd-seq 
```

To make this happen at boot:
```
sudo echo snd-seq >> /etc/modules 
```


As for the jackd errors, these also should be non critical, they are just saying that your card doesnt support 32 or 24 bit playback or capture so it falls back to 16 bit playback and capture.
Try connecting clients (such as ardour and jack-rack) to jack through qjackctl.

---

### Post by Doovoo on 2007-02-25
Alright, everything seems to be working again, thanks.

---

### Post by Doovoo on 2007-02-25
Apparently everything's not working, or I screwed it up again. I followed the ladder half of [this guide]("https://help.ubuntu.com/community/UbuntuStudioPreparation") (ignoring the things they recommend installing, since I have most of them) and [this guide]("https://help.ubuntu.com/community/HowToSeq24Introduction"). They got my midi working and now I can create music more easily, but playback doesn't work in VLC, Totem, Exaile, Banshee, Firefox, just about everything.

None of the programs but totem give me an error when trying to start them, but totem returns
```

$ totem
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
Creating link /home/liam/.kde/socket-liam-linuxbox.
can't create mcop directory
```

so it seems to be an ALSA problem now. I followed the [Sound Troubleshooting Guide]("https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28configure%29%7C%28alsa%29") and "aplay -l" listed my soundcard, so I ran "sudo modprobe snd-intel8x0" and it entered fine, but didn't fix anything.

I checked out my "/etc/modules" and it looks like this...

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
snd-seq
```

which I don't think is right. Also, when I opened it, I got an error.
```

$ sudo gedit /etc/modules
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
```

Any help or ideas is appreciated.

---

### Post by Doovoo on 2007-02-25
Finally found [this thread]("http://www.ubuntuforums.org/showthread.php?t=286016") which solved my problem.

---

