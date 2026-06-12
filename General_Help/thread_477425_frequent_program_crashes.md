---
title: "frequent program crashes"
date: 2007-06-18
forum: General Help
---

### Post by neufelry on 2007-06-18
I am getting a strange problem while running 7.04 kubuntu wherein several applications frequently crash. A few programs I have had problems with are Kopete, Adept (only once or twice in the last little while) and most frequently (2-3 times an hour) KTorrent. Since Ktorrent is the biggest culprit i'll describe an anatomy of the crashing. First off I have never had it crash while it was "open" and having me fiddle around. It has only crashed while minimized downloading something. During a crash some common applications that are open are vlc and firefox. I can probably provide more info if required, I just want things to be more stable!

---

### Post by gaelfx on 2007-07-17
Do me a favor: go into terminal and start KTorrent from there. Then post the output you get (if any) when KTorrent starts. I'm not saying I'll be able to help, but I think you and I are having the same problem (except that I'm not running KUbuntu).

Here is my output:
```
gaelfx@gaelfx-iBook2:~$ ktorrent
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
Qt: Warning: QObject::disconnect: Unexpected null parameter
Qt: Warning: QObject::disconnect: Unexpected null parameter

```

---

