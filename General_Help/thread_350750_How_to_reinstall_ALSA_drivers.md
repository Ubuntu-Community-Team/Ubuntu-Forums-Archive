---
title: "How to reinstall ALSA drivers?"
date: 2007-02-01
forum: General Help
---

### Post by otakuj462 on 2007-02-01
Hi all, I'd been having some trouble with the mic input of my sound card and decided to download, compile and install the latest version of ALSA, because it stated in the changelog that this problem had been fixed... well that turned out not to be the case in actual fact. I'd now like to roll back the driver from the latest 1.0.14rc2 to the ubuntu 1.0.11, because it was actually working much better before. Thus far I've make uninstalled the downloads from ALSA, and have apt-get --reinstall installed asound2, and alsa-utils. It seems that's all that's left to reinstall is the package containing the 1.0.11 alsa drivers... but they are nowhere to be found in apt. I *have* found alsa-source, and I could certainly compile and make install it, but I'm not sure what the *Debian* way of installing this packages would be... if using this source package is even is the correct thing to do in this situation.
I'd appreciate any advice anyone can give.
Thanks.

-Jake

---

### Post by jocko on 2007-02-01
I think the package you are looking for is **alsa-base**.

---

### Post by marianom on 2007-02-01
check this [sticky]("http://ubuntuforums.org/showthread.php?t=205449")

---

