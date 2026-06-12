---
title: "Horrible battery life on Toshiba Satellite A200"
date: 2013-08-07
forum: General Help
---

### Post by phelenon on 2013-08-07
I recently upgraded my battery.On windows it lasts about 2 hours but in Ubuntu it only lasted till half an hour,20 minutes from 100 to 0 then 10 minutes as battery not present.I am using tlp and aspm thing.If the battery stays the same i am goning to leave Ubuntu

---

### Post by cortman on 2013-08-07
Hi, try installing Jupiter, an excellent power management program. Follow the instructions [here]("https://launchpad.net/~webupd8team/+archive/jupiter") to add the PPA and install.

---

### Post by codemaniac on 2013-08-07
Last time i heard Jupiter as an abandoned project. [http://itsfoss.com/jupiter-linux-applet-development-stopped/](http://itsfoss.com/jupiter-linux-applet-development-stopped/)

You can try out tlp instead.

```
sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw
```

```
sudo tlp start
```

---

### Post by Mark Phelps on 2013-08-12
Sorry ... mispost.

---

