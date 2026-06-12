---
title: "Ubuntu Update Issue"
date: 2008-06-17
forum: General Help
---

### Post by stephenbp on 2008-06-17
I was updating my current ubuntu desktop when it install lockup and froze.  I restarted the desktop and attempted to restart the update when I received the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

When I attempt to run the command, I receive the following message:
dpkg --configure -a
requested operate requires superuser privilage

Does anyone know how I can repair and continue updating my desktop?

---

### Post by skymera on 2008-06-17
sudo dpkg --configure -a

---

### Post by stephenbp on 2008-06-17
Thanks. It seems to be working.  Is there a recommended way to update a ubuntu desktop?  I usually run this command:
sudo apt-get update

Then I usually use the gui interface to complete the install.

---

### Post by FuturePilot on 2008-06-17
You can just use Update Manager. System&#8594;Administration&#8594;Update Manager. Usually it will automatically notify you of updates but you can also use the Check button in Update Manager to check for updates. No need to run sudo apt-get update before hand.

---

