---
title: "Corrupt directory.......ubuntu doesn't boot....???"
date: 2007-08-18
forum: General Help
---

### Post by lol18041992 on 2007-08-18
I have never used linux in my life, but wanted to try it out, so i tried wubi

my system is a win xp pro
512 mb ram
1.3 ghz 
ntfs file system

ok so wubi installed ubuntu smoothly and i booted into ubuntu and started surfing in firefox and all of a sudden the screen froze, i waited for like 5 minutes, and then tried to reboot into ubuntu but it said that it couldn't find a gldr... something file and laid out some options for me like reboot and some searching etc, so when i chose one, the screen filled with "searching.....(the file)    cannot find file(in the next line), so tried to reboot again and after failure i booted into windows to reinstall, but when i tried to open the wubi directory it said that it was corrupt and i had to run chkdsk which did not resolve the problem, so i couldn't uninstall as the directory was corrupt, so i did a system restore and uninstalled wubi......and ubuntu

so can any one tell me what the problem was and how it could/can be fixed?

---

### Post by matthew.lns1 on 2007-08-18
I can't tell you why that happened but I can recomened installing from the desktop cd. It shouldn't give you any problems.

---

### Post by matthew.lns1 on 2007-08-23
I now know what the problem is: since wubi installs ubuntu in "c://wubi/" It is extreamly vunerable to file corruption. Unfortuetly to correct this problem you must reinstall using wubi ar some other method.

---

### Post by tuxcantfly on 2007-08-23
> since wubi installs ubuntu in "c://wubi/" It is extreamly vunerable to file corruption.

Hmm that's strange, I've never heard that before. Are you referring to corruption, as in via virus/human error, or filesystem corruption? Technically, it would be less vulnerable to filesystem corruption than if it were in a deeper directory, since the corruption of any of the higher directories makes all lower ones corrupted.

> Unfortuetly to correct this problem you must reinstall using wubi ar some other method.

Well if all you want is the no-cd installation features, and you don't want the potential filesystem-corruption problems of a loopmounted install, you could always try UNetbootin at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

