---
title: "Problem with xserver and gnome keyboards"
date: 2007-11-04
forum: General Help
---

### Post by jmvidalvia on 2007-11-04
Hello, 

Trying to get  3D acceleration I installed xserver-xgl.
It didn't work, so I removed it, but as soon as I restart my box a message appears saying which keyboard config I would like to use: the X config or the Gnome one.
¿how can I avoid this message?
I don't know which config file I should use, but only one, please!
I alrerady did dpkg-reconfigure xserver-org, with no success.
Thanks in advanced!

PS: I am using Gutsy/Gnome

---

### Post by heatpumpcontrol on 2007-11-05
same here.....I have to select which keyboard layout i want to use. System expected one layout but got another. hmmm any ideas anyone?

---

### Post by heatpumpcontrol on 2007-11-06
bump

---

### Post by heatpumpcontrol on 2007-11-11
> **heatpumpcontrol said:**
> bump


bump again

---

### Post by jmvidalvia on 2007-12-01
Solved!
Just delete .gconf y .gnome in your /home/user
You will loose your personal settings but .gconf y .gnome will be created again automatically as soon as you set a new personalization.
Best luck!

---

