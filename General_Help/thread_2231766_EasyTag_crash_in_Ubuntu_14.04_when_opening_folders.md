---
title: "EasyTag crash in Ubuntu 14.04 when opening folders"
date: 2014-06-27
forum: General Help
---

### Post by kogami2 on 2014-06-27
Hey everyone,

I have noticed that a lot of my software tends to crash when it attempts  to browse to folders on the computer. PuddleTag crashes when I attempt  to browse for music files, dBpoweramp (Wine) the same, etc. I am  wondering what's causing this, and how I can get verbose output from the  program.

Thanks,
Kogami

---

### Post by tgalati4 on 2014-06-27
*eastag* does not have a --debug switch, but many programs do.  Open a terminal and run easytag and capture any text output from the console after a crash. *Puddletag* accepts the --debug switch, but I have never crashed it, so I don't know if it captures useful information after a crash. 

```
puddletag --debug
```

If many applications are crashing, then check the SMART parameters of your hard drive:

```
sudo smartctl -a /dev/sda
```

---

### Post by kogami2 on 2014-06-27
Puddletag doesn't dump any useful debug, just that it was terminated. I've discovered that the problem only applies to my opening my home directory, for whatever reason.

---

### Post by kogami2 on 2014-06-27
Also, when I start EasyTag, for whatever reason, two buttons on the top seem to be stuck down.

---

