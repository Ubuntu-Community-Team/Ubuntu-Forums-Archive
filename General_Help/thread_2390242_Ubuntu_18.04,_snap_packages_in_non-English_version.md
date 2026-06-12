---
title: "Ubuntu 18.04, snap packages in non-English versions of Ubuntu"
date: 2018-04-27
forum: General Help
---

### Post by Jay_Dogg on 2018-04-27
Hi,

There is an annoying bug in Ubuntu 18.04 if you are using a non-English localization. Snap packages occasionally duplicate directories in your home folder, as described in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/snapcraft/+bug/1746710](https://bugs.launchpad.net/ubuntu/+source/snapcraft/+bug/1746710)

Since some of the default applications (gnome-characters, gnome-logs, calculator and system monitor) in 18.04 are, for some reason, installed as snap packages, the bug will impact many. Not all of them trigger this bug, but **gnome-logs** and **gnome-characters** do. The workaround is to replace the misbehaving snap packages with the standard versions from Ubuntu's repositories. I hope this gets fixed soon... And snap packages still create that visible "snap" directory in your home folder, too, regardless of the localization you are using.

---

### Post by qrcyen on 2018-04-29
Is this the same problem from you ?
[IMG]https://image.ibb.co/hkJwDc/Captura_de_tela_de_2018_04_29_11_17_39.png[/IMG]

---

### Post by Jay_Dogg on 2018-04-29
Yes, that's the issue exactly. Some snap packages create empty default folders that are in English, unless the language is English already. As for "gnome-logs" and "gnome-characters", the issue disappeared on my computer at least. Not sure what happened there... Maybe reinstalling them helped or an update has sneaked in. But some others, like VLC as a snap package, definitely causes this still.

---

