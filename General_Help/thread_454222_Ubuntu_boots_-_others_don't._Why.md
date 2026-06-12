---
title: "Ubuntu boots - others don't. Why?"
date: 2007-05-25
forum: General Help
---

### Post by floke on 2007-05-25
have been on a bit of a distro testing spree recently, and have discovered that a few distros won't boot on my PC. Why is this if they all use the same kernel?

_Ones that work include:_
Ubuntu (obviously) + Debian + Sidux
Pardus
Gentoo / Kororaa / Sabayon
Vector
Foresight
Mepis

_One's that don't include_
OpenSUSE (don't ask - just being curious) LiveDVD - CD works fine (10.2)
MCNLive
PCLinuxOS (works fine off LiveCD but Kernel panics on install - and GParted can no longer read partitons, so a bit of a show-stopper).
Knoppix

When trying to boot these it hangs and my fan blows at a million miles an hour, forcing a hard shutdown.

Any ideas about this?

---

### Post by FunnyLookinHat on 2007-05-25
Most likely they are bugs with their software in that the installers and liveCDs don't know how to handle your hardware configuration.  It's strange that PCLinuxOS only works in some cases because it is based off Ubuntu last I checked, but they do a bit of hacking with it so that could be the reason.

When you're getting kernel panics it is most certainly due to hardware discrepencies though.

---

### Post by floke on 2007-05-25
Thanks. I 'think' I may have cracked it. It seemed to be a problem with Mandriva based distros (I tried Mandriva too and it crapped out on me). A bit of research dug up that it was a problem with the Tecra A8 core duo stuff. So disabling one of the processors in the bios has allowed me to run MCNLive - the only one I've tested so far - but I'm confident the others will now work too. From what I've read its a case of updating the kernels for Mandriva etc. once installed so they can cope with the core duo.

Here's hoping....

---

