---
title: "pysol sound server"
date: 2005-06-29
forum: General Help
---

### Post by ewlabonte on 2005-06-29
Pysol is a cool solitaire suite written in python. There is a sound server which goes along with it and which is available through apt-get. It plays music while your playing solitaire. I can't get pysol-sound-server to work with pysol. Even after it is installed the sound option is grayed out. Has anyone had any luck with this?

---

### Post by itsfuntu on 2005-06-29
Same problem here, I have every thing installed but no sound.

---

### Post by abstauber on 2006-01-05
Hi,

```
sudo modprobe snd-seq
``` did it for me.

I also added that module in /etc/modules.

---

