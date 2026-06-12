---
title: "&quot;GNOME Display Manager&quot; when booting ubuntu =/"
date: 2008-03-26
forum: General Help
---

### Post by stiansoftcore on 2008-03-26
When booting into Ubuntu now, something weird happens. I don't get into the logon screen as usual, but something that looks like the terminal shows up, asking for username and password. I don't know what to do. I've tried to log in and trying different commands, but I don't know much about GNOME Terminal. When I write *reboot* it says "Exiting GNOME Display Manager"and reboots and does the same thing over again.

Distro: Ubuntu 7.10 GG

Last thing I remember doing, was open terminal and writing *sudo reboot 1*, because the "Restart" thing in the exit-gui-thingy (don't know what it's called) disappeared (I think it happened after my try with *sudo apt-get install kubuntu-desktop*).

Thanks.

---

### Post by Rocket2DMn on 2008-03-26
Try having X auto-reconfigure itself from that terminal with
```
sudo dpkg-reconfigure xserver-xorg -phigh
startx
```

---

### Post by stiansoftcore on 2008-03-26
It worked :D Thank you very much. 

Almost everything visual i'd configured is default, but I guess it's not that hard to put it back. Thanks :)

---

