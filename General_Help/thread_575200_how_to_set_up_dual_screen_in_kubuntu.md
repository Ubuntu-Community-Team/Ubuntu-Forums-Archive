---
title: "how to set up dual screen in kubuntu"
date: 2007-10-13
forum: General Help
---

### Post by holyct on 2007-10-13
I have 2 screen of different resolution. how do I set dual screen horizontal span mode for them? in kubuntu 7.04, I am using nvidia geforce 8800 with nVidia's proprietary driver installed by envy.

---

### Post by aJayRoo on 2007-10-13
Have you tired Nvidia's configuration program? If not type:
```
kdesu nvidia-settings
```
into a terminal to launch it. This tool should allow you to configure multiple screens. Be aware that if you use Beryl/Compiz and have edited your xorg.conf file then those changes are likely to be lost (but can be added back in easily enough) when you allow the Nvidia tool to write a new configuration file. As always make sure you back up you xorg.conf file before using the Nvidia tool just in case anything should go wrong. Hope that helps.

---

### Post by holyct on 2007-10-13
in nvidia-settings if I enable one monitor it will disable the other i don't know why

---

### Post by aJayRoo on 2007-10-13
Oh really, that sounds like pretty strange behaviour. I'm afraid I don't know anything about configuring dual screens manually as I always use the Nvidia tool. Good luck solving your problem, sorry I couldn't be of any help!

---

### Post by holyct on 2007-10-13
ah, well I just tried again and it works, thanks so much.

---

### Post by aJayRoo on 2007-10-13
Oh well that is good! I couldn't think of a reason for nvidia-setting to behave as you described so it is good to know it is sorted now. Enjoy your large desktop :)

---

