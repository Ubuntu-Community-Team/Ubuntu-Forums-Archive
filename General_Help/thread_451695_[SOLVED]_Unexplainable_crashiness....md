---
title: "[SOLVED] Unexplainable crashiness..."
date: 2007-05-22
forum: General Help
---

### Post by shadarack on 2007-05-22
Hey, I have a problem, and due to my inexperiance with Ubuntu, I can only describe the symptoms.

I use my computer as an alarm clock, having Kalarm start up and play Juk to wake me up. The problem is, the last two days, it has not. In fact, the last two days when I woke up on my own, my system was unresponsive, so I'm not even sure what went wrong.

I don't even know enough about Ubuntu to know where to find the system logs to find out why.

Does anyone know why this might be happening, or more likely, where I can find the logs to find out why? I really need to be able to get up on time so I can not be late for work...

---

### Post by cborga1985 on 2007-05-22
KDE app's start your startup programs different than Gnome for one. Two, KDE's apps will not run as good when yo are using Gnome. I recommend you to install Exaile by doing this```
sudo apt-get install exaile
``` and use it's alarm plugin. Just be sure to leave exaile running so it will wake you up. As for the crashes, probally driver problems. The System Log is here System->Administration->System Logs. Also, i'm not trying to bash KDE as they are both good for different things. If you would like a stand alone alarm program than I recommend this [http://ltsword.allegronetwork.com/index.php?page=7](http://ltsword.allegronetwork.com/index.php?page=7) . I happen to know the person who makes it personaly.

---

