---
title: "Kernel Upgrade / Nvdia driver issue"
date: 2008-05-24
forum: General Help
---

### Post by Tipharet on 2008-05-24
I upgraded my kernel to 2.6.25.4. I can no longer install video drivers nor do I have sound.

I have uninstalled all vid drivers via synaptic and tried envy. I have reinstalled them via synaptic, envy and manually. 

Ive uninstalled all compiz and then tried to reinstall nothing. Ive tried various solutions Ive found goodling, and heeds no results.

Im running x86-64 distro.

Anyone have ideas?

Edit: Couple of interesting things. When I boot into the herdy generic kernel I have sound, but still am unable to install video. This is what it says in 2.6.25.4 when double click the volume control:
'> No volume control GStreamer plugins and/or devices found.

Did the kernel not compile a driver for my audigy card?

---

### Post by sdennie on 2008-05-24
> **Tipharet said:**
> 
Did the kernel not compile a driver for my audigy card?

It's been a while since I've looked into it but, if you used the kernel config from Hardy as a base, I believe it won't compile some common intel sound and wireless drivers (I assume they are compiled out of kernel).

---

### Post by Tipharet on 2008-05-24
> **vor said:**
> It's been a while since I've looked into it but, if you used the kernel config from Hardy as a base, I believe it won't compile some common intel sound and wireless drivers (I assume they are compiled out of kernel).

I actually used [Kernelcheck]("http://http://kcheck.sourceforge.net/") and it compiled the package for me. I have a Creative soundcard.

---

### Post by drs305 on 2008-05-24
If you haven't, install the ubuntu-restricted-extras in synaptic or
```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by Tipharet on 2008-05-24
Will do, I uninstalled the upgraded kernel and that got me my sound back. However the video drivers refuse to cooperate :confused:

edit:
alright I removed envy then I could install the drivers from synaptic. They are there, but I cant make it my native resolution. Whats interesting is the the drive sees my native as 1440x900 but I am unable to choose it.

---

### Post by Tipharet on 2008-05-25
any other takers?

Guess Ill just reinstall.

---

