---
title: "Can't Install libgnutls28"
date: 2015-05-30
forum: General Help
---

### Post by tehtotalpwnage on 2015-05-30
Okay, I kind of had a TIFU moment today when running upgrades on my desktop. I was noticing the message when updating that some packages had been get back. Then, thanks to whatever bright idea I decided to have, I ran a dist-upgrade command. That resulted in another library getting installed. I don't remember what it was called, but it removed a hell of a lot of packages from my system. In fact, Ubuntu desktop and Kubuntu desktop are basically completely uninstalled and useless. They both rely on a package called libgnutls28 which I can't reinstall since there's no installation candidate since it had been obsoleted by aforementioned package. 

I know this is probably asking a lot to fix this major a screw up, but if someone could point me in the right direction, I'd appreciate it.

---

### Post by dino99 on 2015-05-30
Such a case is often met when third party sources are used (ppa, ...) and introducing version package conflict. Then blindly hitting 'Enter' key without understanding the consequencies ends up to huge removal; and finally needs a complete fresh reinstall (quicker most of the time than trying to fix the built mess)

---

### Post by mc4man on 2015-05-30
For curiosity - 
```
apt-cache madison libgnutls2*
```
```
apt-cache policy libgnutls2*
```

---

