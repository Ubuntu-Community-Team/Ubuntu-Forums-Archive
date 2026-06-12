---
title: "apache startup"
date: 2005-06-21
forum: General Help
---

### Post by kpeters on 2005-06-21
Hi all ~

just installed apache2 via Synaptic Package manager and now I am wondering how to configure its startup - is there some visual configuration editor to do this or must it be done via shell? If via shell, what do I do (am coming from BSD and the system V startup seems to be quite different)?

Thanks for all pointers,
Kai

---

### Post by bunced on 2005-06-21
[QUOTE=kpeters]Hi all ~

just installed apache2 via Synaptic Package manager and now I am wondering how to configure its startup - is there some visual configuration editor to do this or must it be done via shell? If via shell, what do I do (am coming from BSD and the system V startup seems to be quite different)?

Thanks for all pointers,
Kai[/QUOTE]
 There should be something under System -> System Administration. Then look for an option named 'services'. Select apache(2) to be started at boot.

Regards,
David

---

### Post by sgenchev on 2005-06-21
Never tried to look for visual runlevel editor but from the command line:

 look in /etc/rc2.d for symlink named S91apache2 - by default it is there if you install apache2. If it is there, apache will start automatically on next boot.
 What it means:
 /etc/rc2.d is a directory for runlevel 2 scripts - default runlevel on Ubuntu. When system is entering any runlevel - be it startup or runlevel change -  it looks in /etc/rcRUNLEVEL.d for things to do.
 First, it looks for scripts starting with "K" and runs them with "stop" argument. Digits after K define the order the scripts will run. K10foo  will run before K15bar and after K07baz.
 Then init goes to scripts staring with S and runs them with "start" argument - the order is again determined by digits after S.
 All entries in /etc/rcX.d are symlinks to the actual scripts in /etc/init.d

 If you need to change/add/remove startup daemons, just add/remove symlinks in appropriate runlevels and name them properly.
 There is an update-rc.d script on Debian distros that supposed to do symlinking for you but it seems to never do what I ask it to do. I must be too dumb to use it..

---

