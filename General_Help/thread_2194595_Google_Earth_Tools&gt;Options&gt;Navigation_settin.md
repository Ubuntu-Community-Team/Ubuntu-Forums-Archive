---
title: "Google Earth Tools&gt;Options&gt;Navigation setting not saved"
date: 2013-12-19
forum: General Help
---

### Post by Handssolow on 2013-12-19
In Google Earth I want save the option "Do not automatically tilt while zooming", instead it defaults to "Automatically tilt and enter ground level view". Is there a way to save this option. I haven't found a config file either, if there was perhaps I could modify it.

By the way I'm still waiting for Google to come up with a fix for the missing Panoramio pictures.
amirpli on a Google Earth Forum shed some light on the problem and it's also discussed here-

[http://ubuntuforums.org/showthread.php?t=2162443](http://ubuntuforums.org/showthread.php?t=2162443)

Ubuntu 12.04 LTS 32 bit here running Google Earth 7.1.1.1871

---

### Post by Handssolow on 2014-01-11
Effectively problem solved after I revisited this today.

First go, I edited in Home >.config>Google> the GoogleEarthPlus.conf file and changed GroundLevelAutoTransition=true to false. This got the result I was after. Incidentally if you edit this file, it automatically creates a backup conf~ file which I subsequently deleted.

Second go, I realised that the Tools menu box extended too low and the Apply and OK options were hidden. This was revealed with full screen Google Earth (F11). I am though still unable to get to the lower edge to resize the window but at least I can save my options now.

---

