---
title: "header files"
date: 2007-06-02
forum: General Help
---

### Post by Shikatano on 2007-06-02
I am currently using Kubuntu, I just installed it yesterday because I like KDE better than Gnome. But my problem is, i need to install the madwifi driver for my d-link dwl 6520 rev. b, so i can get on the internet. When i tried to make the driver i have a bunch of errors and some say that there is no such file as stdio.h or many of the other header files needed. Does this mean that they aren't on my computer? If they aren't how can i get them on there without internet access on that machine? Any help would be appreciated.

---

### Post by taurus on 2007-06-02
Insert Ubuntu installer CD into a drive.  Then, open a terminal and run

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```
Now, you have gcc and everything else that you need to build something from source.

---

### Post by Shikatano on 2007-06-02
that would work only i cant get to the internet on it cause i need a driver for wireless card. any other suggestions?

---

### Post by Shikatano on 2007-06-02
i'm sorry nevermind i just skipped over the update. and it installed! so thanks so much!

---

