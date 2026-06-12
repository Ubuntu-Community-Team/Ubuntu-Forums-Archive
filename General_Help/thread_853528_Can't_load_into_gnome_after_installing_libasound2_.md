---
title: "Can't load into gnome after installing libasound2 i386 .deb on 64bit system."
date: 2008-07-08
forum: General Help
---

### Post by Dave_Connor on 2008-07-08
I am trying to load into Gnome after install the libasound2 packages and it is saying about wrong ELF class when trying to load. I am trying to fix this within safe mode but no internet connection is preventing me from trying to fix this. Is there a way to fix this issue so I can have gnome and X back again ?

---

### Post by ibuclaw on 2008-07-08
Do you have an Ethernet cable on you?

That would be the most sound way to connect to the internet, and run:
```
sudo aptitude reinstall libasound2
```
else, you can search and download the file from packages.ubuntu.com and run
```
sudo dpkg -i libasound*.deb
```

Just out of curiosity, how did you get an i386 package to install on your 64bit system?
By most conventional methods, apt should block this from happening.

Regards
Iain

---

