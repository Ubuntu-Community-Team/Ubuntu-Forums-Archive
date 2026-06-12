---
title: "alsa + gstreamer + cmedia onboard sound card"
date: 2005-05-06
forum: General Help
---

### Post by Fab on 2005-05-06
okay, i followed the alsa + esd sound howto on the forums here, installed libesd-alsa and did all the steps there, but i cant change my default source in gstreamer-properties to alsa, it says "Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'"
alsa as sink and esd as source works
ive tried to disable and kill esd, and reboot, still no dice
"lsmod | grep alsa" doesnt return anything, i dont know if that is normal?

any help would be gratefully accepted ;)

regards

---

### Post by Karlos on 2005-05-06
did you come across [this]("http://www.ubuntuforums.org/showthread.php?t=26567")

I found it helpful

---

### Post by Fab on 2005-05-06
[QUOTE=Karlos]did you come across [this]("http://www.ubuntuforums.org/showthread.php?t=26567")

I found it helpful[/QUOTE]
 thats the one i followed, but i just saw that i maybe forgot to include alsa in my services, ill try when im at my box and report back then :)

---

