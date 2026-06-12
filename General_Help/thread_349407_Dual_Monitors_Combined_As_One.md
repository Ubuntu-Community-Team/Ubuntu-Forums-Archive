---
title: "Dual Monitors Combined As One"
date: 2007-01-30
forum: General Help
---

### Post by Darkstar0082 on 2007-01-30
I've been trying to get a dual monitor display to work on my vaio with a NV17 [GeForce4 420 Go]. First attempt: completely messed up my system so I had to reinstall everything. Second attempt: got dual monitors to work but the showed the same thing on both monitors. Now I need to figure out how to combine both monitors together so I can move my mouse from one screen to the other. It did it automatically in windows xp but I can't seem to find any help that works. I am a new linux user so I need a bit of hand holding. Also I want my laptop to be the main screen and my LCD to be on the left side next to my main screen. Thanks in advanced for any possible help.

---

### Post by lisje on 2007-01-30
> **Darkstar0082 said:**
> I've been trying to get a dual monitor display to work on my vaio with a NV17 [GeForce4 420 Go]. First attempt: completely messed up my system so I had to reinstall everything. Second attempt: got dual monitors to work but the showed the same thing on both monitors. Now I need to figure out how to combine both monitors together so I can move my mouse from one screen to the other. It did it automatically in windows xp but I can't seem to find any help that works. I am a new linux user so I need a bit of hand holding. Also I want my laptop to be the main screen and my LCD to be on the left side next to my main screen. Thanks in advanced for any possible help.

First you need to install the 'nvidia-glx' package. And then you could try the configuration file I use:
[http://kleinewereld.be/xorg2.conf]("http://kleinewereld.be/xorg2.conf")

I've got my external monitor set up on the left side of my screen, but I use that monitor as my main screen... But it should be easy to change that...

Greets,
Lisje

---

### Post by Puschkin on 2007-01-30
I used this guide, which is very detailed and worked for me:

[http://www.paralipsis.org/2006/01/enabling-xinerama-in-ubuntu/]("http://www.paralipsis.org/2006/01/enabling-xinerama-in-ubuntu/")

maybe it helps.

Greets,
Puschkin

---

