---
title: "Issue after failed Aptitude"
date: 2007-10-12
forum: General Help
---

### Post by Naatan on 2007-10-12
I just tried instaling Kubuntu-desktop with Aptitude, but when configuring all the packages it crashed, I rebooted and tried if it worked anyway, nope.. went into terminal and did a dpkg --configure -a, and after that removed the kubuntu-desktop and installed again.

Weird thing is when I re-install the kubuntu-desktop it takes like 10 seconds, though that whole process is supposed to take at least 10 minutes..

When I try to login to a kde session I get the following error:

Call to Inusertemp failed (temporary directories full?). Check your installation.

Gnome works fine..

---

### Post by Naatan on 2007-10-12
it seems to be related to my user homedir, when I create a new user and test KDE with that user it DOES work.. =\

---

### Post by Naatan on 2007-10-13
Fixed it, deleting the ~/.kde folder worked.

---

