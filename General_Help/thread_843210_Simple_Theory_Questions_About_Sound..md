---
title: "Simple Theory Questions About Sound."
date: 2008-06-28
forum: General Help
---

### Post by mempman on 2008-06-28
Hello,
I just had a few questions, and was hoping to find some answers.


1)
When I open up my "Volume Control" menu in gnome, and click on File>Change Device, I have the following options for audio Playback:

1. ALSA mixer
2. OSS mixer
3. PulseAudio Mixer

Does the selection of 1 of these mean that the chose sound server is being used for current audio output?  For example, if I choose ALSA, I am using ALSA; if I choose PulseAudio, I am using PulseAudio?  


2) If the first question means that I can instantly change my sound server, this would mean that there are many sound servers loaded at any given time but only one is being used; then what happens when I switch from, say, ALSA to PulseAudio during mp3 playback, does the sound server change instantly?

---

### Post by sdennie on 2008-06-28
To answer "1)", Pulse Audio is essentially a level of indirection between an app and a sink.  For the vast majority of users, that sink will be ALSA so, essentially, Pulse Audio is completely superfluous (as configured in a default Hardy install).  You can look at this thread to attempt to make Pulse Audio to work; [http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse+audio](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse+audio) or, you can simply disable it and use ALSA instead.

---

