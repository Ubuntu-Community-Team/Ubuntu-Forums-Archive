---
title: "Ubuntu 14.04 -&gt; No sound from internal speakers"
date: 2015-07-24
forum: General Help
---

### Post by micp2091 on 2015-07-24
Hello everyone,

after spending several hours on this topic I have no choice but to ask for your help. I am a complete beginner with Linux. As I mentioned in the topic there's no sound coming from my speakers at all. There's no problem with headphones but I cant get speakers to work. Some information that may be helpful: [http://www.alsa-project.org/db/?f=c20dbb38b25c088867761829dcab70a15e04a510](http://www.alsa-project.org/db/?f=c20dbb38b25c088867761829dcab70a15e04a510)    There's nothing muted in Alsamixer, it detects chip as Realtek ALC668. Not sure whether it matters, but i have additional monitor connected to laptop via HDMI - disconnecting it doesn't make any change. Any help would be much appreciated [IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG] Thanks a lot
Cheers !

---

### Post by SeijiSensei on 2015-07-24
Try installing **pavucontrol** from the repositories.  It will allow you to choose among the various input and output options as well as manage volumes.

---

### Post by micp2091 on 2015-07-30
Pavucontrol and adding several lines did the job but in the end due to other reasons i did reinstall linux. Sound was working like a charm after that :)

---

### Post by malay3 on 2015-10-27
Yeah. That helped me too.

---

