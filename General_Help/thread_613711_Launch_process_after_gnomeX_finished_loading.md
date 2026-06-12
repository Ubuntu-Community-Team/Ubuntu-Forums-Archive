---
title: "Launch process after gnome/X finished loading"
date: 2007-11-15
forum: General Help
---

### Post by livingtarget on 2007-11-15
Heya,

Here's my problem:
I got a dual screen and at startup I want to launch a few processes automatically on my 2nd monitor. The command I use is just a simple 

DISPLAY=":0.1" emerald

I tried putting these commands in System -> Preferences -> Sessions, but I don't think it works. The 2nd display takes a while to load so I think it launches it prematurely when the display is not up yet. Is there a way I can launch a process say 30 seconds after loading gnome or something similar. I had a look at Cron, but I couldn't quite figure it out.

Thanks in advance.

---

### Post by taurus on 2007-11-15
You can put the "sleep 30" option in front of the command to delay it 30 seconds or whatever seconds you want to use.

```
sleep 30 && *command*
```

---

### Post by livingtarget on 2007-11-15
Thanks,

still learning most of the magic of shell scripts. I think I got it working now.

---

