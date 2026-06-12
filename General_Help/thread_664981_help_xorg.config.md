---
title: "help xorg.config"
date: 2008-01-11
forum: General Help
---

### Post by n0greenfx on 2008-01-11
hey, im trying to run a dual monitor setup. i have and onboard S3 UniChrome-based cards with 3D support. and an nvidia geforce 2 mx400/400 installed. i want to run one screen of the nvidia card and the other of the onboard card. what i was told to try is turn the primary video section in my bios to integrated then change the name of my xorg.config file to something else. i cannot change the name of my xorg.config file it say access denied any ideas??

---

### Post by taurus on 2008-01-11
```
**sudo** mv /etc/X11/xorg.conf /etc/X11/*something_else*
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by n0greenfx on 2008-01-11
do u think this will work for dual monitors does this make sense???

---

