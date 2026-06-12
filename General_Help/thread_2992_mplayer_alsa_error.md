---
title: "mplayer alsa error"
date: 2004-11-02
forum: General Help
---

### Post by tanari on 2004-11-02
when I choose ALSA drivers in MPlayer preference and try to open video file I see error message
alsa-control: mixer attach /dev/mixer error: No such file or directory

---

### Post by claymore on 2004-11-05
I am getting the exact same problem.

I have switched my gstreamer setting from esd to alsa, and that didn't make a difference.

Is there any place in the MPlayer config file that would allow me to change the mixer device from /dev/mixer to whatever alsa is using?  Where would I even find that stuff?

---

### Post by tanari on 2004-11-11
can somebody help?
I have this problem also in SuSE 9.1 and Yoper 2.1 :(

---

### Post by sharingan on 2004-11-14
You can set the Mplayer preference audio driver to either **arts** if you run under kde or **esd** if run under gnome.

---

### Post by claymore on 2004-11-17
Yay!  I finally found a solution.  It was in a fedora forum, but it works like a charm in ubuntu.

Here is the original link: [http://www.fedoraforum.org/forum/showthread.php?t=26600](http://www.fedoraforum.org/forum/showthread.php?t=26600)

First, go into the .mplayer/gui.conf file and change the following lines:
ao_oss_mixer = "/dev/mixer"
ao_oss_device = "/dev/dsp"

to
ao_oss_mixer = "mixer"
ao_oss_device = "dsp"

Then create a file called /etc/asound.conf and enter the following:

ctl.mixer {
    type hw
    card 0
}

And that's it, Mplayer should work with alsa just fine.

---

### Post by zenwhen on 2004-11-17
Haha, thanks a lot claymore. I have this issue and hadn't thought to ask about it. :D

---

