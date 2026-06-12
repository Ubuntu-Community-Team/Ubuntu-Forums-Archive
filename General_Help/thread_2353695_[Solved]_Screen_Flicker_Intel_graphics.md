---
title: "[Solved] Screen Flicker Intel graphics"
date: 2017-02-24
forum: General Help
---

### Post by doug23 on 2017-02-24
This is a solved message right off the bat. I have an ASUS K601 that I recently installed Ubuntu Mate 16.04 on. The screen had an annoying flicker. By flicker I mean had a beat in it like hum bars going through it. I searched for an answer and there were several out there that involved xorg.conf files, kernel commands, etc. and none worked.

Finally I decided to install the xorg ppa and all was solved. This fixed not only the screen flicker but the washed out colors problem. It is a solid bright and vivid screen now.

[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

Also see - [https://wiki.archlinux.org/index.php/intel_graphics](https://wiki.archlinux.org/index.php/intel_graphics)

You do have to remove it for an Ubuntu upgrade (total system upgrade not nornal updates) but that's a small price to pay for the results I got.

---

