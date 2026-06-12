---
title: "Software Updater Activates After Apt-Get Update"
date: 2013-07-04
forum: General Help
---

### Post by buzzingrobot on 2013-07-04
I usually update via "apt-get update" and "apt-get upgrade".

After "apt-get update" completes, and if there are updates to be installed, Software Updater will activate itself and pop its icon into the Launcher.  

If I then run "apt-get upgrade" to collect the updates, and then click launch Software Updater, it happily goes through the motions of retrieving and installing the same updates. 

Doesn't seem harmful, but it's consistent here and a bit odd. 

I'm on 13.04.

---

### Post by dino99 on 2013-07-04
the thing is that ubuntu is glancing for updates itself, poping software updater
[http://www.garron.me/en/linux/turn-off-stop-ubuntu-automatic-update.html](http://www.garron.me/en/linux/turn-off-stop-ubuntu-automatic-update.html)

---

### Post by buzzingrobot on 2013-07-04
Understod, but apt-get update seems to be triggering Software Updater.  I have the Updater configured to check automatically daily, and it does popup independently.

But, if it has not yet on any given day, and I run apt-get update, and updates are available, then the Updater will launch a few seconds after apt-get update completes.

---

