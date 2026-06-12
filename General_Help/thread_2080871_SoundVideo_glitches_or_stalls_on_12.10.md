---
title: "Sound/Video glitches or stalls on 12.10"
date: 2012-11-05
forum: General Help
---

### Post by slimaq007 on 2012-11-05
Hi, I am new in here. I've decided to give xubuntu 12.10 a try, but I am experiencing some problems right now. When I play music on Banshee or view streamed media in chromium I get problems with sound and video. It just stalls on the same short fragment for while and than move on.

I checked my drivers (I am using nvidia 8600M GT), and every configuration works more or less the same (the frequency of this situation is different).

Does anyone have the same problem?

EDIT: Actually problem shows also in VLC player and rhythmbox.

---

### Post by phil989 on 2012-11-09
>  It just stalls on the same short fragment for while and than move on.

We might be experiencing the same issue.  I had no problems until I upgraded from 12.04 to 12.10.  

However, I am using regular Ubuntu with Unity not Xubuntu.

Assuming it's an issue with the alsa driver since, like you, the problem occurs in all media players including flash player, and html5 video on youtube.

-

```
&#10140; dpkg -l | grep alsa
ii  alsa-base                                 1.0.25+dfsg-0ubuntu3                       all          ALSA driver configuration files
ii  alsa-utils                                1.0.25-3ubuntu2                            amd64        Utilities for configuring and using ALSA
ii  bluez-alsa:amd64                          4.101-0ubuntu6                             amd64        Bluetooth ALSA support
ii  bluez-alsa:i386                           4.101-0ubuntu6                             i386         Bluetooth ALSA support
ii  gstreamer0.10-alsa:amd64                  0.10.36-1ubuntu1                           amd64        GStreamer plugin for ALSA

```

---

