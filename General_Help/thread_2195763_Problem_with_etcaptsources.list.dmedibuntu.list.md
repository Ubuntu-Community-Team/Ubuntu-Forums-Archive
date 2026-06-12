---
title: "Problem with /etc/apt/sources.list.d/medibuntu.list"
date: 2013-12-26
forum: General Help
---

### Post by ogburnpaul on 2013-12-26
E: Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

please someone help Im still really a noob ... I screwed up ... thanks in advance ...

---

### Post by steeldriver on 2013-12-26
It sounds like you downloaded a raw web page instead of a plaintext version of the medibuntu.list file - what were you doing right before this happened?

My understanding is that the medibuntu project has been discontinued btw

---

### Post by coffeecat on 2013-12-26
Moved to own thread.

@ogburnpaul, your problem is somewhat different from the thread you posted to. It's better to start your own threads.

---

### Post by oldos2er on 2013-12-26
> **ogburnpaul said:**
> E: Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

please someone help Im still really a noob ... I screwed up ... thanks in advance ...

As steeldriver said, the medibuntu repo is no more. ```
sudo rm /etc/apt/sources.list.d/medibuntu*

sudo apt-get update
```

---

