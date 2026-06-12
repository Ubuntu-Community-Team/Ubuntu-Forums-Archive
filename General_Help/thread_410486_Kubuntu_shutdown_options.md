---
title: "Kubuntu shutdown options"
date: 2007-04-15
forum: General Help
---

### Post by 14bmail on 2007-04-15
Hello there,
           I don't know if this is a KDE, kubuntu or feisty specific question + answer. I installed feisty ubuntu then installed kubuntu via apt-get install kubuntu-desktop. My problem is that the Shutdown options only has "Log Out" (which logs the user out to main sessions menu). It also only shows Log Out when I do [ctrl] [alt] [del]. So I click "Log Out" and in the main sessions menu I can choose the shutdown options of Log Out, hibernate, restart, turn off etc. I was wondering if there is a way to get all these options to show while I am in KDE/kubuntu.

Thank you :guitar: <- Had to put that in, I went to see slayer last night :D

---

### Post by Ptero-4 on 2007-04-15
You need to use KDM instead of GDM as your login manager to have the shutdown stuff under KDE. To make KDM default when installing kubuntu over ubuntu you need to type:
```
sudo dpkg-reconfigure kdm
```
In the terminal and choose KDM when it asks.

---

### Post by 14bmail on 2007-04-15
Cheers, much appreciated :D

---

