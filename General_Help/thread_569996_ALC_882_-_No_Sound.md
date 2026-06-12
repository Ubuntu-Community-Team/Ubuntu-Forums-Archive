---
title: "ALC 882 - No Sound"
date: 2007-10-07
forum: General Help
---

### Post by ew16301 on 2007-10-07
Im using ubuntu gusty and I have a RealTek HD audio sound card (Alc882) on a Asus A7t. I have no sound but it seems to detect the sound card properly. Ive also tried in feisty and it didnt work either. Ive noticed alot of other people having trouble with sound but I havent found any answers in the forums or the bug trackers. Any idea where to start? Im willing to go from scratch because ive tried everything. Thanks in advance.

---

### Post by sizzam on 2007-11-16
I have an Asus A7T with the ALC882 codec as well.  

I am running Gutsy and using the alsa-base package that it installed (version 1.0.14-1ubuntu2).   Here's how I was able to get my sound to work:

First:
```
sudo gedit /etc/modprobe.d/snd-hda-intel.modprobe
```
(note - this file doesn't currently exist)

Enter the following and save:
```
options snd-hda-intel model=w2jc
```

Next:
```
sudo gedit /etc/modprobe.d/alsa-base
```

Add the same line to the end of this file and save:
```
options snd-hda-intel model=w2jc
```

After I made these two file changes and rebooted, I then had sound.   Hopefully it works for you, too :-)

---

### Post by ryanmillet on 2007-11-19
YES YES YES!!!!!!!!!!!

I Have Been Trying to get this working for the past 3 months!!! YOU FREAKING RULE!!

CONFIRMED WORKING 

ASUS A7T 



Thanks Again

---

