---
title: "Laptop problem with graphics"
date: 2013-02-25
forum: General Help
---

### Post by 0badc0de on 2013-02-25
Hello forum users!
I install Ubuntu 12.10 x86_64 on my ASUS X55VD which have Intel and Nvidia 610M graphics.
But after installing nvidia-current (or nvidia-current-updates) and after i reboot, my desktop is gone, but i can open terminal using CTRL+ALT+T.
linux-headers are installed.
In lspci i see my Nvidia card.
After removing nvidia-current, my desktop appear, but i prefered to use Nvidia 610M.
Help me :)

---

### Post by Bashing-om on 2013-02-25
0badc0de; Hi ! Welcome to the forum.

Your 610M is an Intel/Nvidia hybrid card, and it is not officially supported by Nvidia. See this link here for installing the drivers: Switchable laptop graphics issues on Ubuntu 12.04?
[http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310](http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310)

[INDENT][INDENT]hope this helps

[/INDENT][/INDENT]

---

