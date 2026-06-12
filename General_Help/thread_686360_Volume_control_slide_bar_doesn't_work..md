---
title: "Volume control slide bar doesn't work."
date: 2008-02-03
forum: General Help
---

### Post by geo909 on 2008-02-03
Hello everybody,  
 I have an M-AUDIO audiophile 24/96 sound card and  the volume control slide bar on the upper panel doesn't work. In the pregerences, in the "select the device and track to control field" I've choosen 
"M Audio Audiophile 24/96 (Alsa Mixer)". However, when I mute or control the slidebar  there's no change in the volume.

 I have read several similar posts but couldn't find an answer. Could anyone help, please?!

---

### Post by happyhamster on 2008-02-03
> **geo909 said:**
> In the pregerences, in the "select the device and track to control field" I've choosen 
"M Audio Audiophile 24/96 (Alsa Mixer)". However, when I mute or control the slidebar  there's no change in the volume.
In that same menu, under that option, should be a list of available tracks. The one you select (master, headphone, pcm, etc) will be the one which volume will change when using the slider. 

If you don't know which one to use, double-click the volume bar (instead of right-clicking it), and choose Edit-->Preferences. Tick every option to enable all sliders, and find the one you want to use.

So yes, the preferences menu you get when right- or double clicking is different (which is pretty confusing IMHO).

---

### Post by geo909 on 2008-02-03
Thanks a lot! 
 Yes, that did the job. It took me lots of time because my soundcard gets a bit complicated when it comes to its channels.

 There is just one thing: 
 When I move up and down the slider, the change **rate** is very low, until a certain point where a small change in the slider almost mutes completely the sound.
  For anyone who knows what I mean, the change rate is obviously linear when it should be logarithmic, like any volume adjusting tool...

 Does anyone has the same problem?

---

### Post by happyhamster on 2008-02-03
I have no experience with it myself, but you could try the package alsa-tools-gui (using apt-get or synaptic). Description is:

GUI based ALSA utilities for specific hardware
A collection of GUI based ALSA utilities for specific sound hardware:

 echomixer - control tool for Echoaudio soundcards
 envy24control - control tool for Envy24 (ice1712) based soundcards
 hdspconf - GUI program to control the Hammerfall HDSP Alsa Settings.
 hdspmixer - tool to control the advanced routing features of the
             RME Hammerfall DSP.
 rmedigicontrol - control tool for RME Digi32 and RME Digi96 soundcards


The envy24control part should be applicable for your soundcard.

---

### Post by happyhamster on 2008-02-03
Err, and check first if you have an ICE1712 (Envy24) card using:

aplay -l

---

### Post by polmir on 2008-02-03
> **geo909 said:**
> 
There is just one thing: 
 When I move up and down the slider, the change **rate** is very low, until a certain point where a small change in the slider almost mutes completely the sound.
  For anyone who knows what I mean, the change rate is obviously linear when it should be logarithmic, like any volume adjusting tool...

Type in terminal 
```
alsamixer
``` 
help for it
```
man alsamixer
alsamixer -h
```

---

### Post by geo909 on 2008-02-03
> **happyhamster said:**
> I have no experience with it myself, but you could try the package alsa-tools-gui (using apt-get or synaptic). Description is:

GUI based ALSA utilities for specific hardware
A collection of GUI based ALSA utilities for specific sound hardware:

 echomixer - control tool for Echoaudio soundcards
 envy24control - control tool for Envy24 (ice1712) based soundcards
 hdspconf - GUI program to control the Hammerfall HDSP Alsa Settings.
 hdspmixer - tool to control the advanced routing features of the
             RME Hammerfall DSP.
 rmedigicontrol - control tool for RME Digi32 and RME Digi96 soundcards


The envy24control part should be applicable for your soundcard.

Yes, Indeeed I have an ICE1712 card.

 Well, that gui is almost exactly the same with the mixer interface that comes with my soundcard (windows)! Thanks! I have a very clearer idea of every slidebar now but the problem is that I don't  have any "Master" slidebar to control the volume (BTW the controlling that I achieved before was completely wrong, I didn't even have stereo)...

 See how it is:
[[IMG]http://www.imageshack.gr/files/7ipwg6n21w31fuupvx8b.png[/IMG]](http://www.imageshack.gr/view.php?file=7ipwg6n21w31fuupvx8b.png)

No master control... :(
I can't find a way to control the master volume by adjusting only one bar..

@Polmir: Thanks for the info, I just can't see what I should do with it. A gui is always  easier to handle..

---

