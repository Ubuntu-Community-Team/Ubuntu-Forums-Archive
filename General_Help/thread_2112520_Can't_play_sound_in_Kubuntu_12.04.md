---
title: "Can't play sound in Kubuntu 12.04"
date: 2013-02-05
forum: General Help
---

### Post by jhilp on 2013-02-05
I just installed Kubuntu 12.04 on my computer, and I can't play sound when viewing YouTube videos. Any suggestions? Thanks!

---

### Post by mörgæs on 2013-02-05
[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

---

### Post by SeijiSensei on 2013-02-05
Sometimes the playback device is muted by default.  (I never understand why that would be, but it does seem to happen sometimes on Kubuntu.)  To fix this problem, you need to run "sudo apt-get install pavucontrol" then run the pavucontrol program from a terminal or by pressing Alt-F2 and typing "pavucontrol" in the box that appears.  Look through the tabs and see if either the input or output device is muted.  You can tell by whether the little mute icon appears depressed or not.

Hope that helps.

---

### Post by jhilp on 2013-02-05
> **SeijiSensei said:**
> Sometimes the playback device is muted by default.  (I never understand why that would be, but it does seem to happen sometimes on Kubuntu.)  To fix this problem, you need to run "sudo apt-get install pavucontrol" then run the pavucontrol program from a terminal or by pressing Alt-F2 and typing "pavucontrol" in the box that appears.  Look through the tabs and see if either the input or output device is muted.  You can tell by whether the little mute icon appears depressed or not.

Hope that helps.
That worked! I went to the "playback" tab, and changed the ALSA plug setting from Built-in Audio Analog Stereo to SB Audigy Analog Stereo.  Thanks!

---

### Post by SeijiSensei on 2013-02-05
If that was the issue, and not muting, you should look at System Settings > Multimedia > Phonon.  That lets you select the audio device to be used for a variety of different situations.

---

### Post by linux_nub on 2013-02-23
> **SeijiSensei said:**
> Sometimes the playback device is muted by default.  (I never understand why that would be, but it does seem to happen sometimes on Kubuntu.)  To fix this problem, you need to run "sudo apt-get install pavucontrol" then run the pavucontrol program from a terminal or by pressing Alt-F2 and typing "pavucontrol" in the box that appears.  Look through the tabs and see if either the input or output device is muted.  You can tell by whether the little mute icon appears depressed or not.

Hope that helps.

Divine intervention! Thankyou sejisensei. Now i can listen to youtube videos again for the first time in 2 weeks :p

---

### Post by tommysmith2 on 2013-10-28
I have trouble with sound too, I'm install Kubuntu 13.10 and all working fine, I also play video with sound ok untill today I playing video withouth have sound :confused: I had install pavucontrol and see the "taskbar" running sound but I can't hear anything, I had testing in Window 8 in dualboot and it's also play with sound ok, just Kubuntu I can't unserstand why it suddenlly can't play it !!??

---

