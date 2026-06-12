---
title: "No Small caps!?"
date: 2008-05-11
forum: General Help
---

### Post by TheBuzzer on 2008-05-11
Hi!

While I install upgrades on Ubuntu version 7.10, it happen something that took off my possibility to enter small CAPS as I want to login and I would like to upgrade to 8.04 version, someone can help me accessing old session to upgrade it?

Marc

---

### Post by daengbo on 2008-05-12
You need to explain more fully what the problem is. I understand that English is probably not your first language, but I don't understand what happened, what your problem is, or what you need.

Maybe you can find someone to translate and help you explain your problem.

---

### Post by TheBuzzer on 2008-05-12
> **daengbo said:**
> You need to explain more fully what the problem is. I understand that English is probably not your first language, but I don't understand what happened, what your problem is, or what you need.

Maybe you can find someone to translate and help you explain your problem.

On my login window, I can't use small caps anymore, only big caps are working so as my password contain small caps in it, I can't log anymore on my linux ubuntu. After solving this problem, I'll update to 8.10!

And when I try the recover mode, it says <Unknown X keysum "0xfe11">

Thanks to be patient!

Marc

---

### Post by daengbo on 2008-05-13
Maybe your caps lock is on.
[http://forum.ubuntu-fr.org/viewtopic.php?pid=1554371](http://forum.ubuntu-fr.org/viewtopic.php?pid=1554371) ???

---

### Post by TheBuzzer on 2008-05-13
> **daengbo said:**
> Maybe your caps lock is on.
[http://forum.ubuntu-fr.org/viewtopic.php?pid=1554371](http://forum.ubuntu-fr.org/viewtopic.php?pid=1554371) ???

Sorry, I have over 20 years of computer experience, I would to that!

What I said is that when I'm in small caps, nothing appear so I can't enter my username and password caus it only have CAPS chars that works...

Exemple: word like "WoRd" appear without small chars like that->"WR" like I would type nothing!?!

---

### Post by Patrick793 on 2008-05-13
Maybe try typing with caps on, while holding shift?

---

### Post by TheBuzzer on 2008-05-16
> **Patrick793 said:**
> Maybe try typing with caps on, while holding shift?

When I press the shift, I have caps and when I take off my finger from the shift button, nothing at all!

I found the problem, I put "us" first in my /etc/X11/xorg.conf to upgrade to 8.04. The thing, I tried to put "fr-ca" but it doesn't work, after that I put "ca" and now it works very fine!

The new recovery mode from 8.04 version is better than the 7.10 one. 8.04 is doing verification in configuration files!

Thanks to all, it is now working!

Marc

---

