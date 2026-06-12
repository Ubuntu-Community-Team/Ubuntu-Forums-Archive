---
title: "New Ubuntu Intall: Volume always at MAX"
date: 2015-05-06
forum: General Help
---

### Post by neu5eeCh on 2015-05-06
That pretty much describes the problem. The volume is always at MAX _no matter what_. I've Googled & tried various solutions, but they all seem outdated. Any suggestions?

---

### Post by neu5eeCh on 2015-05-07
**Update:** I can control the volume by starting alsamixer and adjusting the PCM slider. However, if I try to adjust the volume via the fn keys or via the Pulseaudio Icon in the panel, the volume immediately reverts to 100%. Ideas?

---

### Post by dino99 on 2015-05-07
maybe reconfigure pulseaudio
pavucontrol is a good place to change sound settings
do you have some non trusted packages installed ? (ppa...)

---

### Post by neu5eeCh on 2015-05-07
Hey! That's helped! Now I've got to change the rate of Volume increase. It goes from 0-100% in 3 clicks. I remember doing this a long time ago, but can't remember now. I'll start Googling. Please suggest if you remember.

**Edit: **Found what I needed here:

[http://askubuntu.com/questions/507230/finer-volume-control-in-14-04](http://askubuntu.com/questions/507230/finer-volume-control-in-14-04)

---

