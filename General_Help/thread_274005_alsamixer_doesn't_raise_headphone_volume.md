---
title: "alsamixer doesn't raise headphone volume"
date: 2006-10-09
forum: General Help
---

### Post by melissawm on 2006-10-09
Hi guys,

Well I've got this ugly problem. I have a fresh installation of Kubuntu Dapper in a new computer and here "lspci | grep Audio" gives:

0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

Ok all goes well and this new PC has a front headphone jack that I would really like to use, since this is my work PC and I like to listen to music while working, but my colleague does not. So, installed amarok, I see the waves in the visualization and I do have sound coming out of the so called "front speakers" (which are actually behind the cpu), but not from the headphone jack. 

So after some research I tried alsamixer/amixer and the output for "amixer contents" for the headphone is this:

```
numid=19,iface=MIXER,name='Headphone Playback Switch'
  ; type=BOOLEAN,access=rw---,values=2
  : values=on,on
```Now, I tried increasing the volume from the command line, using the "amixer set" command and this is what I get:

```
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
```The thing is, for the Headphones, I only have "pswitch" in the Capabilities, whereas for the other devices (Front Speaker, etc) I have pswitch AND pvolume. In kmix, surely enough, I don't have a volume bar for the headphone, just a "toggle" button.

Any ideas how I could get the "pvolume" capability working for this? Sorry for the poor text but I'm confused myself... Thanks in advance.

---

