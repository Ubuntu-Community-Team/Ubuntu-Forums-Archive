---
title: "kacpid hogs CPU"
date: 2006-11-02
forum: General Help
---

### Post by musicinmybrain on 2006-11-02
Top reports on a fresh boot that kacpid is taking about 15% to 20% of the CPU resources. I haven't seen this with versions of Ubuntu prior to Edgy (this is a fresh install, not an upgrade).

Is this a known issue that I can't seem to find a fix for? There are posts all over the Internet where kacpid has taken the entire CPU, but they mostly seem to be old and unresolved. Plus, 20% is different from 98%. Any ideas?

---

### Post by musicinmybrain on 2006-11-15
Hate to pester, but surely somebody has an idea?

---

### Post by musicinmybrain on 2006-11-20
Looks like this occurs when the processor is in danger of overheating. When I improve the thermal situation, kacpid drops to 0.0% CPU usage. I'm guessing it's enforcing idle cycles to keep the processor from overheating.

---

