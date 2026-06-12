---
title: "How to diagnose unresponsive desktop?"
date: 2012-12-07
forum: General Help
---

### Post by MoebusNet on 2012-12-07
This morning, while addressing Christmas cards, I had several applications running. At some point during the session, my desktop environment (Unity 3D) became unreponsive for several minutes at a time. My trackpad pointer would move, I could click on applications or Dash Home in Launcher, could attempt to minimize an application but no response at all until a minute or two passed.

I had GRAMPS, Rhythmbox and Firefox (maybe 2 tabs open) running when this occurred. I suppose Update Manager could have run in the background, but I had already manually updated earlier.

Would anyone have any ideas where I could look to attempt to diagnose this? I didn't see anything in Log File Viewer. Googlubuntu didn't seem to have anything definite that I could find.

---

### Post by MoebusNet on 2012-12-09
bump

---

### Post by NightsShadeQueen on 2012-12-09
Try top? (top in terminal)

The data output should look roughly like the below. Not sure if you could get to it if your computer is currently unresponsive, but grabbing this right after your system begins to respond again will also provide useful information.

top - 11:42:30 up 14:21,  5 users,  load average: 2.45, 2.39, 2.32
Tasks: 169 total,   1 running, 168 sleeping,   0 stopped,   0 zombie
Cpu(s): 31.0%us,  7.8%sy,  0.0%ni, 60.3%id,  1.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2965228k total,  2472520k used,   492708k free,   207196k buffers
Swap:  4057084k total,        0k used,  4057084k free,  1086928k cached

(Probably incredibly stupid idea but actually something I've done before: Installed the ssh server package*, ssh'ed in from another computer, made ssh priority -5, and watched top whenever original computer became unresponsive. If you do this, 

```
ps aux --forest
```

also provides really useful information

* I also like turned all the security settings to the max - my account only, different port, etc. so wasn't being completely stupid.)

---

