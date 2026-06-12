---
title: "Microphone problem"
date: 2007-09-19
forum: General Help
---

### Post by acheton on 2007-09-19
Hi all,

I'm still a bit of a newbie to Ubuntu and I'm having a problem with my microphone. As far as I can tell  the microphone isn't working at all. When I open up *System->Preferences->Sounds* and press the Test button against *Sound Capture* I get an error message:

[INDENT]gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.
[/INDENT]

Which doesn't seem to be good. Double clicking on the Volume control in the system tray shows only playback rather than any input (see attached jpg). The mic is definitely in the right socket and the same hardware works ok in Windows. 

I've tried to follow various guide to get things working on the web but my problem seems to be more fundamental. Can anyone help?

Thanks,

ach

---

### Post by linuxwizard on 2007-09-19
Have you tried this
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by acheton on 2007-09-19
Great, thanks for the help wizard. I'm making progress now. I've enabled all the options under sound, unmuted and turned up the volume on each of the options on the Recording tab of volume control. Running 

[INDENT]vumeter -r &[/INDENT]

shows that some sound is coming thru the mic, however it is very low, So I'm just trying to work on that - using the links you gave.

Ach

PS pressing the Test button I used before seems to work now.

---

### Post by bunny rabbit on 2007-09-30
> **linuxwizard said:**
> Have you tried this
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

Those links worked really well. Good stuff. Thanks mr. Wizard!

---

### Post by linuxwizard on 2007-09-30
You're Welcome bunny rabbit.  Glad they worked for you.

---

