---
title: "KDE startup items."
date: 2005-05-01
forum: General Help
---

### Post by sd5867 on 2005-05-01
Greetings, let me first say that I am a Linux Novice.  I am currently running a Debian system, but use both Kubunu and Knoppix live CD's.  I am basically trying to create a system that is a mix between Kubuntu and Knoppix, as they are both excellent distrobutions.  Where one lacks, the other picks up and vice-versa.  So, to get the system that I would maximize the most from, I am having to build it piece by piece.  Not an easy task, but one that I am willing to try to complete.

So, on to the question, I am trying to figure out how programs know to startup with KDE.  For example.  In KDE, I have gaim running, if I log out kde and goto Gnome, gaim doesn't start.  If I log out of Gnome, and back into KDE, gaim once again starts.  With this, I conclude that there is a script or config file that tells KDE what programs to start when KDE starts.   Also, if I leave a browser window open when I log out of KDE, when I login, it opens back up.  Initially I thought that the /etc/rc1.d through /etc/rc6.d and the /etc/rcS.d directories controlled startup programs.  They do, but only for each session and the X Window system, not for KDE.  I also noticed that all the files in the /etc/rcX.d directories were links from /etc/init.d.  I have not checked all the files in /etc/init.d, for there are dozens, but I don't believe that any of them control KDE startup programs.  I asked some questions somewhere else, and was pointed to ~/.kde/Autostart.  This directory controls some of the items that start with KDE but not all of them.  I belive that there maybe another folder for all users that use KDE to determine what starts when KDE starts and then the second one in ~/.kde/Autostart for user specific startups.  Any help would be appreciated.  Thanks in advance.

SD

---

### Post by brent on 2005-05-01
Open up Control Centre
KDE Components -> Session Manager

---

