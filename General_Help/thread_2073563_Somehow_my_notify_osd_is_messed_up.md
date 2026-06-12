---
title: "Somehow my notify osd is messed up"
date: 2012-10-19
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-10-19
well technically i have the wrong one
i installed and configured compiz and suddenly i noticed my notifications look like they did on ubuntu 10.04
i turned compiz off and they are not back :(
i want my xfce 4.10 style notifications that stack on the screen and i can click to close
could someone please tell me how i managed to do that so i can undo it
these are the only packages that are on the system with my problem that are not on my system that is not
for the record i am using kernel 3.6.2 on both systems
based on output of [FONT=Courier New]dpkg --get-selections
[/FONT] 
[LIST]
[*] ethtool
[*] libavcodec53:amd64
[*] libavutil51:amd64
[*] [s]linux-generic
[*] linux-headers-3.5.0-17
[*] linux-headers-3.5.0-17-generic
[*] linux-headers-generic
[*] linux-image-3.5.0-17-generic
[*] linux-image-extra-3.5.0-17-generic
[*] linux-image-generic[/s]
[*] lm-sensors
[/LIST]
i purged everything compiz and no change

i attached a list of ever package i installed (includes purged compiz)
i made it with
[FONT=Courier New]ls /var/cache/apt/archives/*.deb[/FONT]

---

### Post by pqwoerituytrueiwoq on 2012-10-20
finally figured it out after 4 reinstalls
notify-osd need to be removed/purged
i could have swore that /usr/bin/notify-send came from that package

---

