---
title: "Software update error"
date: 2008-02-03
forum: General Help
---

### Post by waldrepdebater on 2008-02-03
Whenever I try to install software updates I get the following error.

```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory


```

Does anyone know what the problem is?

---

### Post by manimal347 on 2008-02-03
Yeah, you probably have two instances of apt-get/Synaptic, and don't even realize it. This sometimes happens when you leave Synaptic open and go to run a system update (sudo apt-get upgrade) from the terminal, for example, or try to install two programs at once.

---

### Post by lhardyl on 2008-02-10
im having the exact problem, how does one fix it?

i cant seem to find another synaptic running

---

### Post by lhardyl on 2008-02-11
hmmm all that was required for me was a reboot. Still not sure why the error occured though. Gunna see if i can replicate it over the next couple of days

---

