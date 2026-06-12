---
title: "Kernel panic and nvidia weirdness"
date: 2012-10-21
forum: General Help
---

### Post by squaregoldfish on 2012-10-21
I upgraded to 12.10 yesterday, and everything went without a hitch.

Today I'd been using my machine for a few hours when suddenly I got a kernel panic. This was mildly surprising (haven't seen one in years), but it didn't concern me overmuch.

I did a hard reboot, and X wouldn't start at all. Bizarrely X wouldn't load, complaining that it couldn't find the nvidia module. After poking around for a bit, I discovered that *the entire nvidia package had disappeared*. No sign of it anywhere. Running apt-get to install nvidia-current brought everything back without any problems, and it's all good again.

While this is a bit of a non-problem, I'm slightly troubled that all trace of the nvidia package simply disappeared from my system. Where did it go, and what sent it away? Am I infected by a Weeping Angel*?

Any thoughts would be interesting to read.

Steve.

* Sorry - just been catching up on Doctor Who.

---

### Post by s3a on 2012-10-21
A possibility could be that the packages were removed together with other packages you removed. I've seen this happen in Debian a few times (and Ubuntu is based off Debian).

I think bugs should be filed for these situations if they occur but, as an easy workaround, I personally wrote a script that re-installs every single package (from the repositories) that I use so if something like this happens or if I re-install the OS to my root partition (and re-mount my home), everything is back to normal after running this script of mine.

---

### Post by squaregoldfish on 2012-10-21
But that's where the weirdness lies - the package wasn't removed during the upgrade, because I've restarted the machine a couple of times since then and it was all fine. The package disappeared at some point today during normal use. I can't see how the kernel panic was related, unless the nvidia module disappeared from underneath it and caused the panic that way.

Steve.

---

