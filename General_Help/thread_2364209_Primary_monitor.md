---
title: "Primary monitor"
date: 2017-06-20
forum: General Help
---

### Post by Apofix on 2017-06-20
Hi,

I have laptop Dell Inspiron 15 7000 and I'm using Ubuntu 17.04 with Cinnamon.
I have plugged Extern monitor via HDMI. I want laptop screen have as primary screen but, i already set it in settings and no changes.
Changes are saved, but no effect.

Main problem is, when i want maximize screen on laptop screen, then automatically windows is switched to extern monitor.
Both monitors are FullHD, same resolution.

When I tried use Unity, i cant event use "extend" mode properly, just mirror, everything was weird and stretched, mouse pointer wasnt coresponding to clicks.

Nvidia driver: 381.22, i tried using others but without success.
When I run "nvidia-xsettings" it sometimes works, but afterwards my laptop resolution is only 640x480. Afterwars I have to delete "xorg.conf" to be able set higher resolution than 640x480.

With different laptop and ubuntu 16.10 works everything as expected with the same monitor. (also cinnamon)

If I start laptop without external monitor and i plug in during login(after i entered password), then everything works as expected

---

### Post by dragonfly41 on 2017-06-20
Some issues re: managing dual monitors were discussed here (to avoid repeating them).
[URL="http://https://ubuntuforums.org/showthread.php?t=2363950"]
https://ubuntuforums.org/showthread.php?t=2363950[/URL]

Try using [Windows} + [P] keys as discussed.
Also install arandr.

---

### Post by Apofix on 2017-06-20
WIn+P doesn't work, arandr i tried, there is set that my laptop monitor is primary
In BIOS there is any option to disable Optimus. I tried non-NVIDIA driver, but then externaal monitor is black.
I tried also set Power Saving Model in nvidia-settings(to use Intel GPU) but then also monitor doesn't work.

---

