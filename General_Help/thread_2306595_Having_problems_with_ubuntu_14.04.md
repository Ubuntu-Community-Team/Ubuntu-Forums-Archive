---
title: "Having problems with ubuntu 14.04"
date: 2015-12-17
forum: General Help
---

### Post by Dragon_Wings on 2015-12-17
Hello! (as the title said i am running ubuntu 14.04)
I am a new user of ubuntu and recently i ran into alot of problems. One of them is i can't connect to my wireless connection and the second one is alot of applications crash (.EXE applications and some other applications that came with ubuntu) If anybody could help me that would be amazing! :D BTW i run ubuntu on a laptop.

---

### Post by v3.xx on 2015-12-17
I would start with the basic update and upgrade in terminal.  This will give you a printout of any errors which you can post here.

So open a terminal (Ctrl + Alt + t) and enter:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Also please post your laptop specs (ram, cpu, video) or again in terminal:

```
inxi -b
```

---

### Post by Bucky Ball on 2015-12-17
> **Dragon_Wings said:**
> ... alot of applications crash (.EXE applications and some other applications that came with ubuntu) If anybody could help me that would be amazing! :D BTW i run ubuntu on a laptop.

Welcome. .exe files are for Windows, not Ubuntu. They won't run in Ubuntu without the use of software like Wine. Some Windows programs will work, some partially, and some not at all. If you're looking to run mostly Windows apps in Ubuntu that probably won't work too well. You could try looking for open-source alternatives to your Windows apps ...

(Ubuntu is not a drop-in, free replacement for Windows. :))

As for wireless connection issues, might be better to start a thread devoted to that in ***[Networking and Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")***. Read [the sticky]("http://ubuntuforums.org/showthread.php?t=370108") for that forum prior to posting Good luck.

(PS: For terminal output, see the last link in my signature for how to use code tags.)

---

