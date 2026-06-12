---
title: "How to switch default volume control application"
date: 2016-04-05
forum: General Help
---

### Post by rchr on 2016-04-05
Hi,
I`m using Ubuntu 14.04.4 with MATE 1.8 and after some update long time ago, every time I click "Volume Control"/"Sound Settings" on panel`s sound icon/applet (or Settings > MATE Volume Control) it opens this super fugly tool:

[IMG]http://i.imgur.com/65i7xOV.png[/IMG]

Checked 3 other Ubuntu installs, same version, same MATE, same repo, mostly same config... and 1 of them also have this issue (the oldest one), but remaining 2 use this much nicer, GNOME-like tool:

[IMG]http://wiki.audacityteam.org/w/images/d/d9/Gnome_volume_control_Inputs.png[/IMG]


Plus I checked and on all 4 machines it`s this same default command to bring it up "mate-volume-control".
Is there a way to set it back to old solution ? Or maybe even step further and set it to ultra-cool "pavucontrol" ?

Best Regards!

---

### Post by rchr on 2016-04-11
Hehe, found a solution somewhere else and it turned out to be extremely easy xD
> sudo apt-get install mate-media-pulse

---

