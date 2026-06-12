---
title: "Master Volume"
date: 2006-08-16
forum: General Help
---

### Post by Lunar_Lamp on 2006-08-16
The volume keys on my laptop keyboard automatically worked in dapper.  Great.  However, they don't control the volume that I want it to.  They control the master volume, not the PCM, which is probably what most people want it to control (but maybe it was a concious usage decision to put it the way it is now, so I will not complain).

I have found that the commands I want are:

amixer sset PCM mute
amixer sset PCM 1+ unmute
amixer sset PCM 1- unmute

What is the most simple way to change the volume keys function?  I tried to do it using xbindkeys, but the volume key combination ("FN+up arrow" for example) does not give any reading when I try to tell it to use that combo.

---

### Post by Lunar_Lamp on 2006-08-24
I cannot believe that nobody knows how to do this.  All I want to do in effect it to replace the current volume key mapping with a new command set, whilst keeping the volume animation if possible.  If I knew where the current volume keys were assigned, I could change the command that they executed, but I don't know where the default keys are located.

---

### Post by stryderjzw on 2006-09-24
If you're still looking, here's a good thread:
[http://www.ubuntuforums.org/showthread.php?p=1535110](http://www.ubuntuforums.org/showthread.php?p=1535110)

---

