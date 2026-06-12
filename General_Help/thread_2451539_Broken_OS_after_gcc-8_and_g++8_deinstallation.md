---
title: "Broken OS after gcc-8 and g++8 deinstallation"
date: 2020-10-06
forum: General Help
---

### Post by davidlbit on 2020-10-06
Hey guy's, 
**I need your help!** I just installed gcc10 and g++10 on my Ubuntu 20.04 Laptop and setting it as my default compiler. While i was doing that I noticed that I've got two older versions on the Machine gcc8 g++8 and gcc9 g++9. So I through it would be unnecessary to have that many versions on the Machine, that's why I deleted the oldest version (8) with the command: **<sudo apt-get purge gcc-8 g++8>** and it totally broke the os.

Is there any way to repair the os or at least save some important files on the machine?!!
[B][U]
Current behavior:[/U][/B]
It tries to boot into ubuntu and then the following message will show up: [B]/dev/sda2: clean, 1240878/7782400 files, 17019459/31127296 blocks

[UPDATE]
[/B]With the help of a bootable Ubuntu USB stick I was able to check with fsck if some filesystems are broken. Luckily that's not the case. After that I used boot-repair to repair any damages that my actions caused. However, it's still not possible to boot into my system and I'm getting a slightly different error now:

[B]/dev/sda2: clean, 1240878/7782400 files, 17019459/31127296 blocks
[xxx.xxxxxxx] ieee80211 phy0: brcmf_cfg80211_escan_handler: buffer is too small: ignoring[/B]
[B][xxx.xxxxxxx] ieee80211 phy0: brcmf_cfg80211_escan_handler: buffer is too small: ignoring
[B][xxx.xxxxxxx] ieee80211 phy0: brcmf_cfg80211_escan_handler: buffer is too small: ignoring
.
.
.
[/B][/B]

---

