---
title: "Xubuntu is faster than Ubuntu??"
date: 2008-03-09
forum: General Help
---

### Post by bennyda on 2008-03-09
Is this really so? I am using Ubuntu Feisty. I find it pretty fast? What exactly does "faster" mean? 

How does one convert to Xubuntu? of Kubuntu for that matter?

p.s. XP sux

---

### Post by Crafty Kisses on 2008-03-09
> **bennyda said:**
> Is this really so? I am using Ubuntu Feisty. I find it pretty fast? What exactly does "faster" mean? 

How does one convert to Xubuntu? of Kubuntu for that matter?

p.s. XP sux

Xubuntu is usually for low-end computers, so yes, in some sense it's faster, it's really dimmed down though, still a great OS though.

---

### Post by lloyd_b on 2008-03-09
> **bennyda said:**
> Is this really so? I am using Ubuntu Feisty. I find it pretty fast? What exactly does "faster" mean? 

How does one convert to Xubuntu? of Kubuntu for that matter?

p.s. XP sux

All of the 'buntu flavors use the same basic Linux kernel, and the same basic services.  The difference is in the desktop.  Ubuntu uses Gnome, Kubuntu uses KDE, and Xubuntu uses Xfce.

Xfce is somewhat simpler than Gnome or KDE, and as a result uses somewhat less memory and responds a bit faster.  But unless you feel that Gnome is "too slow", there's no valid reason to switch (Xubuntu is targeted at older machines, with slower processors and typically a lot less memory than newer machines).

If you have enough disk space, there's no reason you can't have all three desktops installed on one machine.  To install the other two:
```
sudo apt-get install xubuntu-desktop
sudo apt-get install kubuntu-desktop
```
(or install those packages via synaptic)

And then at the login screen, click the options button, and select which "session type" you want to try.

Lloyd B.

---

### Post by jocko on 2008-03-09
> **bennyda said:**
> Is this really so? I am using Ubuntu Feisty. I find it pretty fast? What exactly does "faster" mean? 

How does one convert to Xubuntu? of Kubuntu for that matter?

p.s. XP sux

As far as I understand, xubuntu may be faster on systems with a low amount of ram because it requires less memory.
This will install xubuntu and kubuntu:
```
sudo apt-get install xubuntu-desktop
```
and:
```
sudo apt-get install kubuntu-desktop
```
It will not remove gnome, so you'll get to choose what to use when you log in.

---

### Post by banewman on 2008-03-09
You can install xubuntu-desktop from synaptic and then choose to run xubuntu from the login - options. It will have ubuntus' apps in the menu as well but will let you have a taste of the desktop.
:)

---

### Post by bennyda on 2008-03-09
hey guys, awesomely quick responses. thanks a lot. i will try it out.

---

