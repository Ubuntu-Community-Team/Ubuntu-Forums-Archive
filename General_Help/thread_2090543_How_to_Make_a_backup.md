---
title: "How to Make a backup"
date: 2012-12-02
forum: General Help
---

### Post by hSync on 2012-12-02
Hey, how can i make a backup of the configs of my system? I spent hours trying to fix the video problems and now finally everything is working fine, i wanted to have a backup just in case.
Thank you.

---

### Post by thnewguy on 2012-12-02
Configuration files are usually stored in the /etc directory and in your home directory. Backing up these two locations on a regular basis is a good way to make sure your personal files and all configuration settings are safe. The easiest way to do that is probably to hook up an external drive and run a command like

cp -R /etc ~ /media/external-drive

Where "external-drive" is the directory where your USB drive is attached to the system.

---

### Post by hSync on 2012-12-02
> **thnewguy said:**
> Configuration files are usually stored in the /etc directory and in your home directory. Backing up these two locations on a regular basis is a good way to make sure your personal files and all configuration settings are safe. The easiest way to do that is probably to hook up an external drive and run a command like

cp -R /etc ~ /media/external-drive

Where "external-drive" is the directory where your USB drive is attached to the system.

Thank you!

---

