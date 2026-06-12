---
title: "I've done all the research, need help with the script, please!"
date: 2008-01-10
forum: General Help
---

### Post by Kache on 2008-01-10
I need a script that runs at startup as a daemon that makes my Fn mute key on my laptop work.

I've found a forum about mapping such a key to running a script:
[http://ubuntuforums.org/showthread.php?t=434520](http://ubuntuforums.org/showthread.php?t=434520)

I'll use the System>Preferences>Sessions to start it.

And I've found the exact things the script should do. Now all I need is the script.

I imagine it would be small, and I was hoping if someone could throw one together really quick. I shall pseudocode to prove my point. 

The script should do this when run:

Run:
```
amixer -c 0 cget numid=16,iface=MIXER,name='PCM Playback Volume'
```
expected output to stout is:
```
numid=16,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=255,step=0
  : values=**X**,**Y**
  | dBscale-min=-51.00dB,step=0.20dB,mute=0
```

OR

Run:
```
amixer -c 0 sget PCM
```
where expected output would be:
```
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback **X** [*x*%] [*x_*dB]
  Front Right: Playback **Y** [*y*%] [*y_*dB]
```


where the the bolded **X** and **Y** are integers between 0 and 225. (ignore the italicized *x*, *y*, *x_*, and *y_* values)

```
if (X != 0 && Y != 0) // not currently muted
  runInTerminal("amixer -q -c 0 sset PCM playback 0") // mute
else // it's muted
  runInTerminal("amixer -q -c 0 sset PCM playback 255") // unmute
```
and that's it.

If someone could *please* just spit something out for me, I'd imagine many Sony VAIO TZ users to be very thankful for your help.

(Ideally, I would save the volume levels so that unmute-ing brings the volume back to its last position, rather than just 100%, but beggers can't be choosers.)

---

### Post by geirha on 2008-01-10
Try with this perhaps:
```
#!/bin/sh
amixer -q -c 0 set PCM playback toggle

```

---

### Post by Kache on 2008-01-11
both
```
amixer -c 0 set PCM playback toggle
amixer -c 0 sset PCM playback toggle
```
give
```
amixer: Invalid command!
```
=\

-q option works though!

---

### Post by geirha on 2008-01-11
hm, what version of amixer do you have? ```
amixer --version
``` (I have 1.0.14 on my gutsy-box)

Also, try with ```
amixer -c 0 set PCM toggle
```

---

### Post by Kache on 2008-01-11
1.0.14 here too

Hm, it seems my problem has become more complicated, and I'm not sure if I need that script anymore. I'll be positing more detailed information about this in [Sony Vaio TZ Series: Quest for 100% Compatibility]("http://ubuntuforums.org/showthread.php?t=514292"), and perhaps later on in my own thread, [Multi-booting Vista/Gutsy on Sony Vaio TZ, VGN-TZ130N]("http://ubuntuforums.org/showthread.php?t=661809").

---

