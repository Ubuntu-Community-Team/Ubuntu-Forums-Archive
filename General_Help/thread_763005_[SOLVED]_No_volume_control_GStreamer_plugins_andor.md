---
title: "[SOLVED] No volume control GStreamer plugins and/or devices found."
date: 2008-04-22
forum: General Help
---

### Post by jakupl on 2008-04-22
Suddently all sound dissapeared. when I press the sound icon on the panel, i get this "No volume control GStreamer plugins and/or devices found."

the only soundrelated stuff i've done is this. I did it yesterday.
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly
```



another thing that could be related to this problem, is the fact that, ubuntu yesterday suddently seemed to have forgotten my password.

for more information, read [this.](http://ubuntuforums.org/showthread.php?t=762575)

any Ideas?

---

### Post by jakupl on 2008-04-22
by the way, when I boot, I can hear the login drums.

---

### Post by jakupl on 2008-04-22
Sorry if I waisted your time. I found the solution.

When my password stopped working, i had to delete my user, and add it again.

this has taken my permissions to access the audio device(s) away.

I found the solution to this thread *[here](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)*

---

