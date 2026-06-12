---
title: "Problem running Google-Chrome on Ubuntu 22.04"
date: 2023-07-12
forum: General Help
---

### Post by satimis on 2023-07-12
Hi all,

[B][COLOR="#FF0000"]Ubuntu 22.04
Gnome desktop[/COLOR][/B]

Found in recent few days, on Google-Chome browsing all my websites on Internet, all their background disappeared.  Browsing on Firefox they don't have problem.

Just uninstall Google-Chrome and reinstall it running;
$ sudo apt update
$ wget [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
$ sudo dpkg -i google-chrome-stable_current_amd64.deb

Installation went through without complaint but prroblem still remains.

$ apt list --installed | grep google-chrome```

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
google-chrome-stable/stable,now 114.0.5735.198-1 amd64 [installed]

```

$ sudo apt update```

.......
The following packages have been kept back:
  gjs gnome-remote-desktop gnome-shell gnome-shell-common libgjs0g libspeechd2
  python3-speechd speech-dispatcher speech-dispatcher-audio-plugins
  speech-dispatcher-espeak-ng ubuntu-advantage-tools
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

```
gnome-remote-desktop gnome-shell gnome-shell-common
Not installed.  Would it matter?

Please help.  Thanks in advance.

Regards

---

### Post by QIII on 2023-07-12
Just had a similar issue on Kubuntu.

Did a purge and then removed the ~/.config/google-chrome directory completely.

Reinstalled starting from wget, etc.

---

### Post by satimis on 2023-07-12
> **QIII said:**
> Just had a similar issue on Kubuntu.

Did a purge and then removed the ~/.config/google-chrome directory completely.

Reinstalled starting from wget, etc.
Hi,

**[COLOR="#FF0000"]Performed following steps;[/COLOR]**

$ apt list --installed | grep google-chrome```

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
google-chrome-stable/stable,now 114.0.5735.198-1 amd64 [installed]

```

$ sudo apt --purge remove google-chrome-stable
It went through without complaint

$ sudo rmdir ~/.config/google-chrome```

rmdir: failed to remove '/home/satimis/.config/google-chrome': Directory not empty

```

$ sudo rm -rf ~/.config/google-chrome
It went through without complaint

$ sudo apt update ; sudo apt upgrade```

......
The following packages have been kept back:
  gjs gnome-remote-desktop gnome-shell gnome-shell-common libgjs0g
  libspeechd2 python3-speechd speech-dispatcher
  speech-dispatcher-audio-plugins speech-dispatcher-espeak-ng
  ubuntu-advantage-tools
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

```

$ wget [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
$ sudo dpkg -i google-chrome-stable_current_amd64.deb
Also it went through without complaint.

$ google-chrome
Starts Chrome

Problem solved.  Background of my websites popup on browsing.
[B][COLOR="#FF0000"]
Lot of thanks for your advice.[/COLOR][/B]

Regards

---

