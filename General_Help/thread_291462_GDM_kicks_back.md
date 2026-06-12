---
title: "GDM kicks back"
date: 2006-11-02
forum: General Help
---

### Post by MiguelC on 2006-11-02
Hi to all. I have the following problem: when I want to log into my system via gdm, I enter my login and password, the screen goes black and.... gdm appears again. A partial solution I found is to stop gdm and use startx. It works, but it isn't what i want. I'm using Edgy Eft and Beryl. Can anybody help? Thanks in advance :)

---

### Post by Kateikyoushi on 2006-11-02
It means beryl isn't configured properly or something is missing. I assume startx does not start beryl.

Try this.
```
sudo nvidia-xconfig
```

---

### Post by MiguelC on 2006-11-02
I haven't got a nVidia board. I have an Intel 915 on-board chip

---

### Post by highneko on 2006-11-02
In your situation I would install aiglx and beryl. Read how here; [http://wiki.beryl-project.org/](http://wiki.beryl-project.org/)
How did you get this problem? Were you following a beryl installation guide? If so what guide?

---

### Post by MiguelC on 2006-11-02
Beryl was working reasonably well but, after I put "apt-get install kubuntu-desktop", BAM!

---

### Post by Kateikyoushi on 2006-11-02
Edgy comes with aiglx so it's not necessary to install it. Which graphical interface did you choose to boot ? The settings are different for kubuntu and ubuntu desktops that might be the problem.

---

### Post by MiguelC on 2006-11-02
I started with Gnome and later I used KDE. I'll try to install beryl again. I'll keep you informed

---

### Post by Kateikyoushi on 2006-11-02
I mean at login window you can select which graphical environment to boot, does gnome work and just KDE fails ?

---

### Post by MiguelC on 2006-11-02
Neither Gnome, nor KDE, nor XFce works

---

