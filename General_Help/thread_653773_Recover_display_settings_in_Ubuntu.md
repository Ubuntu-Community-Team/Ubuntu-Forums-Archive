---
title: "Recover display settings in Ubuntu?"
date: 2007-12-30
forum: General Help
---

### Post by dnordell on 2007-12-30
**Hi!**

Tried to watch a movie with my TV and plugged in the s-video cable to my laptop and changed my display settings to two monitors and when i reebooted Ubuntu starts up in terminal mode... 

usplash: setting mode failed...
...
kinit: No resume image, doing normal boot.

How can i restore my display settings from the terminal? I'm a newbie to Linux and Terminal and therefore stuck and cant' use my computer... :(

Thankful for any help provided!

---

### Post by nick_h on 2007-12-30
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Aryding on 2008-01-10
I did the same thing and the command doesn't change anything for me

---

