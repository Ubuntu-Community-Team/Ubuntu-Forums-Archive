---
title: "Computer freeze using System Settings [gnome-control-center] &quot;nouveau&quot;"
date: 2013-10-21
forum: General Help
---

### Post by VMC on 2013-10-21
This occurs on both  Saucy - Ubuntu 13.10 and GNOME 13.10.

Integrated graphics:  [B][I]GeForce 6150SE nForce 430

[/I][/B]This happens using the default ***nouveau*** driver and goes away using ***nvidia*** driver.
****Once I open the System Settings gui, I can usually go from screen to screen without problems, but trying to exit eith clicking on the "X" , or Alt+F4 it freezes. Only a power cycle will revive the computer [REISUB]("http://kember.net/articles/reisub-the-gentle-linux-restart/") does nothing.  no mouse, no keyboard keys.

I filed a _**[bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1242767")**_, so if you have the nvidia chip and are using nouveau driver (which you will be on first install), or if you experience the same situation using another nvidia graphics, please confirm on the bug report.

Thanks[B][I].
[/I][/B]
PS: A lame hack is to launch the System Settings through a terminal, using : gnome-control-center &, then killing the process once I have completed.

---

