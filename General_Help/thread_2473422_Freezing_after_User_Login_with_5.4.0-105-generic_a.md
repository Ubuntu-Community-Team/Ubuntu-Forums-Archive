---
title: "Freezing after User Login with 5.4.0-105-generic and newer"
date: 2022-04-04
forum: General Help
---

### Post by ael-earlyup on 2022-04-04
Dear everyone,

starting with Ubuntu 20.04 5.4.0-105-generic, my laptop freezes some seconds after the user login from the login screen... the wallpaper appears, favorites bar appears and sometimes even one of the startup applications pops up but then freezes. The cursor is not moving, commands like Ctrl-Alt-F1/F7 or sending a bug report does obviously neither work. Unfortunately 5.4.0-107 did not fix this issue. I am currently selecting 5.4.0-104-generic in the boot manager, so that I can keep on working, yet it is already on last position there. If I continue updating with not working source packages, 5.4.0-104 will be gone for me, but sooner or later I have to update again to hopefully solve this problem.
Well ... not sure what to do now, why I write this post here. Is this a known problem or do you have any recommendations how to proceed? Sorry if I ask stupid questions!

Maybe some information about my laptop, accessed when using 5.4.0-104-generic :
Laptop: Asus
Processor: Intel® Core&#8482; i7-8550U CPU @ 1.80GHz × 8 
Graphics: NV138 / Mesa Intel® UHD Graphics 620 (KBL GT2)
OS Name: Ubuntu 20.04.4 LTS
OS Type: 64-bit
GNOME Version: 3.36.8
Windowing System: X11

Thanks in advance and best wishes!

---

### Post by xristos on 2022-04-04
Same problem here with Asus laptop
Any solutions ?

Also this is similar
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1965988](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1965988)

---

### Post by him610 on 2022-04-04
This won't fix it, but it should give you an idea as to where to start...
```

systemd-analyze time
systemd-analyze critical-chain
systemd-analyze blame

```

---

