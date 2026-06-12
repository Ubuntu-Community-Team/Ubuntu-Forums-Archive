---
title: "The unknown download"
date: 2013-08-08
forum: General Help
---

### Post by jo4hnc on 2013-08-08
I have to preface this by saying that I think that a recent download has hised Unity on my system. Switched to Gnome and while there have been a few problems, it seems to be working fine.

This morning, the software updater presented me with a download of 388kb that had no info or description(screenshot attached). Since the last update, I'm hesitant to install the unknown. 

Any help or clue would be greatly appreciated. Thanks

---

### Post by zukeprime on 2013-08-08
Same here.  Reregistered with Ubuntu Forums just to get this answer.

---

### Post by QIII on 2013-08-08
zukeprime -

If you had a previous account, it can probably be recovered.

Please start a thread in he Resolution Centre.

---

### Post by zukeprime on 2013-08-08
Thanks QIII...this was my previous account.  Meant to say "reactivate".  :D

---

### Post by Cheesemill on 2013-08-08
Run the following commands in a terminal and it will show you what it wants to upgrade without actually doing it.
```
sudo apt-get update
sudo apt-get -y -s dist-upgrade
```

---

### Post by zukeprime on 2013-08-08
Looks safe to me...wonder why it doesn't show in the "normal" ubuntu update window.

> 4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.Inst python3-problem-report [2.9.2-0ubuntu8.1] (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Inst python3-apport [2.9.2-0ubuntu8.1] (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Inst apport [2.9.2-0ubuntu8.1] (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Inst apport-gtk [2.9.2-0ubuntu8.1] (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Conf python3-problem-report (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Conf python3-apport (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Conf apport (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Conf apport-gtk (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])

---

### Post by jo4hnc on 2013-08-08
Thanks Cheesemill,
I needed a direction and you pointed me in the right one
Here's what I got, Looks like a GTK Python problem report. I guess I'll install it as it seems to be the front end GUI for crash reporting and having had several crashes lately help would be useful.
Still wondering why the description did not appear in the update dialog.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apport apport-gtk python-apport python-problem-report python3-apport
  python3-problem-report
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst python3-problem-report [2.9.2-0ubuntu8.1] (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Inst python3-apport [2.9.2-0ubuntu8.1] (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Inst apport [2.9.2-0ubuntu8.1] (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Inst apport-gtk [2.9.2-0ubuntu8.1] (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Inst python-problem-report [2.9.2-0ubuntu8.1] (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Inst python-apport [2.9.2-0ubuntu8.1] (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Conf python3-problem-report (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Conf python3-apport (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Conf apport (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Conf apport-gtk (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Conf python-problem-report (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])
Conf python-apport (2.9.2-0ubuntu8.3 Ubuntu:13.04/raring-updates [all])

---

