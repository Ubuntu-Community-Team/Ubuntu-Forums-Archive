---
title: "Virus message during install"
date: 2008-05-24
forum: General Help
---

### Post by hummel on 2008-05-24
sorry, I had a virus alert during installing wubi.
Trojan.win32.agent.muq

Is this a known problem, or is it serious?

---

### Post by eldragon on 2008-05-24
as far as i know, wubi modifies system boot files, these files are monitored by av programs. so i guess its a false positive. but just to be in the safe side, redownload the cd. and md5checksum it.

---

### Post by hummel on 2008-05-24
I dont know how to md5checksum, can you explain this please?

---

### Post by ago on 2008-05-24
[https://bugs.launchpad.net/wubi/+bug/229548](https://bugs.launchpad.net/wubi/+bug/229548)

Doublechecking with another a/v does not hurt, the wubi you download from the ubuntu website (as well as the one on CD) also has checksum

---

