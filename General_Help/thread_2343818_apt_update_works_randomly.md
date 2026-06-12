---
title: "apt update works randomly"
date: 2016-11-19
forum: General Help
---

### Post by Sebastin_Perez on 2016-11-19
Hi. Im having a problem with the Apt update command. Sometimes work, but in the last two days the majority of the time it fails. I have a conection timeout frequently with ppa.launchpad.net, and sometimes with mirror.globo.com.

I tried with different mirrors but the problem is the same. It seems to work better if i use a sifferent internet connection. ¿Anyone know something i can do? Thanks!

---

### Post by ian-weisser on 2016-11-20
Apt does not have a 'randomly fail' feature.
You seem to be describing network congestion or unavailable remote servers. Apt can do nothing about those.

I think you already found the best solution: Use a different set of mirrors.

---

### Post by Impavidus on 2016-11-21
ppa.launchpad.net and mirror.globo.com are not part of the official repositories. The built-in feature to find a good mirror for the repositories only works for the official repositories. It doesn't know the mirrors of your PPAs.

---

### Post by Bucky Ball on 2016-11-21
> **Impavidus said:**
> ppa.launchpad.net and mirror.globo.com are not part of the official repositories. The built-in feature to find a good mirror for the repositories only works for the official repositories. It doesn't know the mirrors of your PPAs.

+1. Welcome. You add any third-party PPAs manually at your own risk. If they break, they break. If they go down, same. Not a Ubuntu thing. ;)

---

