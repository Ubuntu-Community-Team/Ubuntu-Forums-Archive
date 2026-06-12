---
title: "[SOLVED] Sound not working in Hardy"
date: 2008-05-31
forum: General Help
---

### Post by sparkguitar05 on 2008-05-31
My sound stopped working yesterday.  I don't know what caused it, but I turned on the machine and the sound just didn't work.  It works when I boot into Windows, so it's not a problem with the speakers.

Any ideas?

---

### Post by sparkguitar05 on 2008-05-31
*bump*

Anyone?  This is driving me nuts.

---

### Post by Zorael on 2008-05-31
Bumping after only ~40ish minutes is a little eager. :>

See [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) for a guide on how to troubleshoot.

---

### Post by xjgnsdof on 2008-05-31
Post your specs. If you're tired of posting them, then put your specs in your signature. Also, give a more precise description of your problem; "my sound doesn't work" tells us zippo.

---

### Post by niloy_gourh on 2008-05-31
Check for your sound card. If it is on broad u should not acheive any difficulties in 8.04 Hardy Heron. But if an external sound car dis installed in PCI slot then u may face some difficulties.
You should first check it out what u have.

---

### Post by sparkguitar05 on 2008-05-31
I don't really know a more accurate way to describe my problem.  I cannot hear anything out of my speakers.  I have tried playing audio from multiple music players and web browsers and I am not able to hear anything.  My speakers are on and attached to the computer, and they work fine in Windows.

How do I find the specs I need to post?

Also, the sound stopped working around the time I started fooling around with virtual machines and Virtualbox.  Could that have anything to do with the problem?

---

### Post by sparkguitar05 on 2008-05-31
My sound card is a Soundblaster Audigy.  I tried that troubleshooting guide and it didn't help.  I think I might have to switch back to Windows if I don't get this working soon.

---

### Post by mc4man on 2008-05-31
```
aplay -l 
``` 
will show what your device(s) is
it never hurts to post what release of ubuntu your using
a simple thing to try is go to system -> preferences -> sound and test. Doesn't hurt either to change from autodetect to something specific (alsa is usually a good bet)
Some audigy cards need analog/digital switch set on or off
some decent reading, advice here
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
pulse specific - [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by Rasitiln on 2008-05-31
I recently dropped creative as far as sound cards go. Went from a buggy incompatible X-fi card to this Turtle Beach Rivera sounds excellent and only cost about twenty five bucks. Given Creative's track record lately I don't expect their Linux support to get better. I'm not a huge audiophile but if your really interested in Linux and just have to have sound picking up a new sound card for twenty to thirty bucks is certainly an easy solution. 

I only recommend this after Googling Creative's Audigy card and Ubuntu, seems they don't get along so great and most the fixes don't seem to work for more than a few handful of people or only work for a little while.

---

### Post by sparkguitar05 on 2008-05-31
```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm using Ubuntu 8.04.  My sound was working for a few months and stopped working when I started fooling around with Virtualbox.

---

### Post by sparkguitar05 on 2008-05-31
I posted my specs.  Anyone have any solutions?  There's something that I need to do soon and I need my audio working.

---

### Post by sparkguitar05 on 2008-05-31
I figured it out.  I had to go to my volume control, click "switches", and uncheck IEC958.

---

