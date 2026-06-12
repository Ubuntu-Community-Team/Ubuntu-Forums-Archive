---
title: "I have no sound"
date: 2007-06-12
forum: General Help
---

### Post by kingvik on 2007-06-12
I cant hear anything, there is no sound

---

### Post by nerdman978 on 2007-06-12
1) Is everything plugged in (unplug and replug)
2) Do you have a sound card? (is that plugged in correctly?)
3) Go to System > Preferences > Sound, and then make sure all your sound devices are selected.

---

### Post by kingvik on 2007-06-12
it's a laptop and my sound works fine in XP but not in Ubuntu. In the system<sound menu when I click on "test" the menu goes away and nothing else happens.

---

### Post by kingvik on 2007-06-12
By the way, when I start-up Ubuntu I can hear the start-up noise but I tried playing a video on youtube or any other site, or internet radio there is no sound.

---

### Post by Patrick K on 2007-06-12
Try right clicking on the speaker icon and make sure the mixer is unmuted (IIRC, by default it is muted). Type > alsamixer < in a terminal and make sure all is unmuted.

---

### Post by DagMan on 2007-06-12
Is it a toshiba
If so, this worked for mine but search for toshiba sound and there's other things others have done for their particular hardware.
[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

---

### Post by kingvik on 2007-06-12
when i type "alsamixer" into the terminal i get a graph with

Headphone 0<>0                 MM
PCM              0<>0                 
Front             100<>100         00
Front Mi        28<>28             MM
Line               0<>0                 MM
CD                  0<>0                MM
Mic                 0<>0                 MM
PC Speak     28<>28             MM

Card: HDA Intel
Chip: Realtek ALC260
View: [Playback]  Capture All
Item: Headphone [dB gain=-4064.00, -4064.00]

---

### Post by kingvik on 2007-06-12
Is it a toshiba
If so, this worked for mine but search for toshiba sound and there's other things others have done for their particular hardware.
[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

No, it's a Sony,
 do u think it still might work.

---

### Post by Patrick K on 2007-06-12
MM means muted (one M for each stereo channel). I don't use that mixer but IIRC either ctrl m or just m should toggle muting. Type "man alsamixer" in a term for the man page. It gives the various options.

---

### Post by kingvik on 2007-06-12
i have unmuted everything i turned it up all the way but still no sound

---

### Post by nickoli_02 on 2007-06-12
I think "m" mutes/unmutes in alsamixer. just unmute all the channels and turn them up. That's the simple solution...

---

### Post by kingvik on 2007-06-12
thanks for all the help, sound is now working.
the Dagman solution worked for me, so i think i will work for others not just Toshiba's

---

