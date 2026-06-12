---
title: "[SOLVED] Can out-of-date repositories be used?"
date: 2008-01-08
forum: General Help
---

### Post by sofasurfer on 2008-01-08
Can repositories for version 6.06 (for instance) be used for 7.10 and updated with the apt-get update command or do you need to find repositories specifically for your version number?

---

### Post by bodhi.zazen on 2008-01-08
No I would expect breakage if you mix repositories like that.

You can possibly install single packages, although I would expect some tweaking, and that is not for "beginners".

apt-get upgrade is likely to either fail or cause total system failure.

The way you would do it would be with pinning :

PINNING:
		[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)
		[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

Why, what is it you are trying to do ?

---

