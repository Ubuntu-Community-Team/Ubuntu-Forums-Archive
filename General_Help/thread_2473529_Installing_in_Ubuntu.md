---
title: "Installing in Ubuntu"
date: 2022-04-07
forum: General Help
---

### Post by johnssschultz on 2022-04-07
[COLOR=#333333][FONT=&quot]I installed a new SSD harddisc in my PC and I installed a fresh Ubuntu 20.04. One of the software packages I need is Freecad.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]- Installing with "sudo apt-get install freecad" will install an outdated dinosaur package Freecad 0.18[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]- sudo add-apt-repository ppa:freecad-maintainers/freecad-daily[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]sudo apt-get update for a daily package will install nothing[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]With the ubuntu snap I could install a freecad 0.19[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]I do not know how to get a daily version[/FONT][/COLOR]

---

### Post by &amp;KyT$0P# on 2022-04-07
> **johnssschultz said:**
> - sudo add-apt-repository ppa:freecad-maintainers/freecad-daily
sudo apt-get update for a daily package will install nothing

Right, [FONT=Courier New]sudo apt-get update[/FONT] does not install anything, it just refreshes the lists of available packages.  You then need to do
```
sudo apt-get install freecad-daily
```

---

### Post by coffeecat on 2022-04-07
Support request, not a Cafe topic.

*Thread moved to **General Help**.*

---

