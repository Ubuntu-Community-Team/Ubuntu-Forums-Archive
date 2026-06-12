---
title: "Uninstalled Firefox -- No Help Program"
date: 2007-07-18
forum: General Help
---

### Post by abrichr on 2007-07-18
While trying to get swiftweasel to act as the default browser, I ended up uninstalling firefox, which ended up uninstalling some applications which apparently were dependent on it.  I'd like to reinstall those applications, as I know one of them is the help application in Ubuntu, the one that is included as one of the three default launchers in the default panel upon a fresh install.  Does anyone know the name of this program?  Is there a way to figure out which packages are dependent on firefox, or does synaptic keep any kind of history I can use to reinstall them?

---

### Post by abrichr on 2007-07-18
Alright, so I finally got a message telling me that the program's name is "yelp", which I installed.  This installed firefox, which is again my default browser, but that's for another thread.  I'm still wondering what the other programs that I uninstalled were?  How do I figure out dependencies, or histories of installed packages?

---

### Post by aysiu on 2007-07-18
> **abrichr said:**
> Alright, so I finally got a message telling me that the program's name is "yelp", which I installed.  This installed firefox, which is again my default browser, but that's for another thread.  I'm still wondering what the other programs that I uninstalled were?  How do I figure out dependencies, or histories of installed packages?
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install ubuntu-desktop
``` That will give you back all the default programs.

---

### Post by abrichr on 2007-07-18
perfect, thanks :)

---

