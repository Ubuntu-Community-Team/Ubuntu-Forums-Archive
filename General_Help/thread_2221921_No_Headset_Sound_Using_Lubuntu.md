---
title: "No Headset Sound Using Lubuntu"
date: 2014-05-04
forum: General Help
---

### Post by dennis17 on 2014-05-04
Kernel Linux 3.13.0-24-generic (i686)
Distribution: Ubuntu 14.04LTS

I can't seem to get my Logitech USB headset to work. In "alsamixer" v1.0.27.2 after hitting F6 I can scroll down and pick out the headset and it seems to recognize the card. However no matter what I do I can't get any sound out of my headset even if I leave alamixer volume control settings open. If I close alamixer it reverts back to the default sound card. My laptop speakers work fine. Greatly appreciate any help....NEWBIE so go easy...lol.

---

### Post by grier-devon on 2014-05-04
The only thing I could find on the issue is 
```
  sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
  sudo apt-get update; sudo apt-get dist-upgrade -y


```

Tell me if that works.

---

### Post by dennis17 on 2014-05-04
Hey grier
Added what you told me via the terminal but still notta.

---

