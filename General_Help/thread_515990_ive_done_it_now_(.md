---
title: "ive done it now :("
date: 2007-08-02
forum: General Help
---

### Post by luckyd on 2007-08-02
I wanted a new version of gtk-dev so i could install the latest version of gimp. I couldn't find it in the ubuntu repos, so I i added the debian testing repo. Without looking at what it was going to install, I let synaptic install gtk2-dev and all of its dependencies. Now I see that some of those were very important, core dependencies like libc6 that are now the debian versions. I would remove them, then install the ubuntu version but when i try to remove them, i have to remove about every other package on the system, because they are dependant. Is there a way to fix this? Im afraid that if i reboot, well it wont reboot because of all these debian packages. PLEASE HELP:cry:

---

### Post by edward4130 on 2007-08-02
You can boot of another drive like a live CD and look for the Snyaptec logs to see all of the items removed and added. Sorry can't tell you where to find those off the top of my head.

You will need to apt-get remove in terminal to remove the items.
```
sudo apt-get remove {package-name}
```

After removing you will need to reinstall all of the packages removed during this gtk update.
```
sudo apt-get install {package-name}
```

this should get you rolling if you can locate the log for synaptec.
-Edward4130

---

### Post by olafbooij on 2007-08-02
I always look in the /var/log/dpkg* log-files if I want to now what is installed/removed.

Good luck!
Olaf

---

### Post by luckyd on 2007-08-03
so i can apt-get remove and install items on my system from the live cd?

---

### Post by olafbooij on 2007-08-04
Good point, I think it's not that easy. Did you already shutdown your pc?
If not, then try apt-getting from the pc itself.
If yes, then I wouldn't know, sorry.

Olaf

---

### Post by luckyd on 2007-08-04
Well, I backed up my home folder to an external, wiped the drive and then started over :(. It took a couple of hours, but now my install is perfectly clean, and pretty much looks the same way it did before. :)

---

