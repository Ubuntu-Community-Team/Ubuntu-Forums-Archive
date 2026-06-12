---
title: "Problem with gnome-appearance-properties"
date: 2008-04-26
forum: General Help
---

### Post by adamsad1 on 2008-04-26
Hey all,

I'm running 8.04 and having troubles with gnome-appearance-proprieties... 

Whenever I load Appearance it starts to consume a huge portion of my CPUs (about 50%--and I have  a 1.6 Core2 Duo) and doesn't go away when I close the interface (I have to manually kill the process).

Also, when I go into visual effects and try and change it from "none" I get an error that "Desktop effects could not be enabled"

Any ideas?

- Adrian

---

### Post by adamsad1 on 2008-04-27
Update --

I created a new user and that one can run appearance-properties with no problem.

I installed gtk-qt-engine and now the effects tab works fine. I thought that this package was installed with Ubuntu though? Maybe I removed something I shouldn't have? It's odd though--I read on other forms that **removing** this package solve the problem...

Running one instance of gnome-appearance-properties eats up one CPU. Running it twice eats up both.

---

### Post by pdxpete on 2008-05-03
Depending on your configuration, you may need to install a restricted driver for your graphics card before using advanced desktop effects.

---

