---
title: "[Problem]UNetbootin"
date: 2007-09-03
forum: General Help
---

### Post by AimLXJ on 2007-09-03
I have currently installed UNetbootin onto my Pentium 2 computer, here's the specs for it:
500MHz
64MB of RAM
10GB Hardrive
It seems like everything has been finished installing ( but haven't seen the option of which Ubuntu to install ), so I rebooted my PC and everything loaded fine but wheres the GUI? All I see is the terminal. A couple of users told me to type this in the terminal: > startx & > sudo dpkg-reconfigure xserver-xorg and I get this result: [[IMG]http://img405.imageshack.us/img405/527/4uejtydkn6.th.png[/IMG]](http://img405.imageshack.us/my.php?image=4uejtydkn6.png) so thats pretty much how it looks, no GUI and I'm new to Linux, I hope my computer isn't dead because it can't boot from the CD drive :(.

---

### Post by tuxcantfly on 2007-09-06
first of all, when typing sudo, use lowercase

second, seems like the install didn't finish installing all the packages. in the terminal, enter this to get a standard ubuntu desktop

```
sudo apt-get install ubuntu-desktop
```

or for kubuntu

```
sudo apt-get install kubuntu-desktop
```

or for xubuntu

```
sudo apt-get install xubuntu-desktop
```

---

