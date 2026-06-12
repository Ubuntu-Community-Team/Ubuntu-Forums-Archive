---
title: "Blacklisted?"
date: 2008-04-24
forum: General Help
---

### Post by jpeddicord on 2008-04-24
[[SIZE="1"](original thread by Amaranth)[/SIZE]]("http://ubuntuforums.org/showthread.php?t=582112")

Trying to run compiz and getting the following output?```
Blacklisted PCIID '8086:2972' found
```

This means your video card has been blacklisted due to driver issues. This applies to some Radeon Mobility cards, Radeon rv350 and rv450 cards, and the Intel 965 (X3000, X3100). 8.04 does not blacklist i965 cards.

You can dodge that blacklist (at your own peril) with the following:```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

If you do this please do not post about any issues you have with stability or video playback problems, that's why your card was blacklisted in the first place.

For more desktop effects and theming information, see the [Desktop Effects FAQ]("http://ubuntuforums.org/showthread.php?t=809695").

---

