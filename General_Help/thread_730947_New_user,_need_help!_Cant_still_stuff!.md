---
title: "New user, need help! Cant still stuff!"
date: 2008-03-21
forum: General Help
---

### Post by Eurocarfan00 on 2008-03-21
Hello, well, I am now switching and trying Ubuntu now, but the last time, back in August it worked perfectly, and you could install the Adobe flash player for the very first time. now in 7.10, FireFox wont install the Flash player, and when you actually  download it,  the Package manager thing, does not recognize it and cant install, and I assume this also happens when you install stuff... before installing I want a full functioning OS. I am new to this, and dont know nothing please help?

---

### Post by prshah on 2008-03-21
> **Eurocarfan00 said:**
> Hello, well, I am now switching and trying Ubuntu now, but the last time, back in August it worked perfectly, and you could install the Adobe flash player for the very first time. now in 7.10, FireFox wont install the Flash player, and when you actually  download it,  the Package manager thing, does not recognize it and cant install, and I assume this also happens when you install stuff... before installing I want a full functioning OS. I am new to this, and dont know nothing please help?

First prize for vagueness...

What I understand: FireFox does not play with flash
Solution: ```
sudo apt-get install gnash
``` or ```
sudo apt-get install flashplugin-nonfree
```

If you don't have an internet connection, it will ask you for your gutsy disk, and pull the files off that.

Before installing, close all firefox windows, install, then, if it still doesn't work, restart and try. If you still don't get it, post the result of ```
sudo apt-get check gnash
```

---

### Post by Eurocarfan00 on 2008-03-21
yes, Firefox does not work, but the problem is that you cant install any packages from the internet, lets say I downloaded rpm package, the window comes up saying that it does not support the format, the OS came like that today, am I blind? or is something in the OS damaged by default?

---

### Post by gfg on 2008-03-21
Ubuntu doesn't utilize rpm packages. Instead it uses deb packages. If you want to download packages of the web you should choose debs. I really recommend you use the package manager though. If you go to applications and choose add/remove you will find most of what you need. If you search for restricted extras in there it will install the most common restricted applications like flash,codecs and java.

---

