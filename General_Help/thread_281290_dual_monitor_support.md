---
title: "dual monitor support"
date: 2006-10-20
forum: General Help
---

### Post by josh76 on 2006-10-20
I am an absolute beginner to leenux so please bear with me. I have two PCI video cards, ATI Radeon 7000 Stealth s 60. One monitor works, however I would like to extend my desktop to both monitors. I read something about typing code in an x server, however I don't even know what that is. As I said I am completely new to linux. Can some one out there explain to my very simply how to configure my system for dual monitor support thanx!!!:D

---

### Post by moeFinley on 2006-10-20
There are many different options for dual monitor linux setups and the instructions vary for different card types.

Lucky there are many posts in this forum with everything you need

[http://ubuntuforums.org/showthread.php?t=162363&highlight=Dual+Monitor+ATI]("http://ubuntuforums.org/showthread.php?t=162363&highlight=Dual+Monitor+ATI")

To edit your X Server config file type the following in the terminal
```
sudo gedit /etc/X11/xorg.conf
```
One ***VERY*** important tip. Make a backup of the xorg.conf file before you do any editing.  This makes it so much easier to get back to a nice graphical interface.

To replace your corupt copy with your backup type:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Hope this gets you started in the right direction.

---

### Post by josh76 on 2006-10-21
how do you make a copy of the x server file?

---

### Post by CatKiller on 2006-10-21
> **josh76 said:**
> how do you make a copy of the x server file?

Have the files the other way round in your command, like so: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Welcome to the community.

---

### Post by josh76 on 2006-10-28
thank you I hope it's not to late.

---

### Post by moeFinley on 2006-10-28
never too late for a thanks :)

---

