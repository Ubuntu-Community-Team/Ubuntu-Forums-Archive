---
title: "broken sound"
date: 2005-06-06
forum: General Help
---

### Post by soonindallas on 2005-06-06
ok.  I was trying to deal with a sound sound problem concerning esd.  I have had a few difficulties with this, i wanted to work around having to killall esd before launching a game.

I looked at this post: [http://ubuntuforums.org/showpost.php?p=192179&postcount=1](http://ubuntuforums.org/showpost.php?p=192179&postcount=1) , followed the instructions and now I have no sound at all. I tried rolling back to the backups, but no joy.  Then I looked at the Unoffical Guide and tried re-establishing the setup that worked.  Still no joy.

here is my /etc/sound/esd.conf:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

here is my /etc/asound.conf:

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

System > Preferences > Sound
shows sound server enabled at startup.

System > Preferences > Multimedia System Selector
gives me no sound when testing ALSA or ESD.  before I messed with it, these both worked.

Q1: how do I get sound back ?
Q2: what are all these files for ?  how do they work together.  In other words, why did my sound get busted ?

Thanks

Peter

EDIT: I poked around and found that the PCM source was set to zero (double clicking on the volume control applet brings up a gnome-controlled ?? alsa-mixer).  Increasing this setting fixed my problem.

---

