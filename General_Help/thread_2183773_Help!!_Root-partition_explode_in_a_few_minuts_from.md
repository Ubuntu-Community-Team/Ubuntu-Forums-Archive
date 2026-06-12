---
title: "Help!! Root-partition explode in a few minuts from 8-9GB to 23GB!!!"
date: 2013-10-26
forum: General Help
---

### Post by Azyx on 2013-10-26
Turned on full logging for gUFW and after a few minutes system warned that the root-partion full.

[http://ubuntuforums.org/showthread.php?t=2183503](http://ubuntuforums.org/showthread.php?t=2183503)

Is it even possible to fill up a log-file with 10-15GB on a few minutes? It is on a local Gbitnetwork with samba, ssh vnc and bonjore (or what the service is called)

I have a separate root and home partition and think I maybe will make a new install with my home-folder intact, but have some special tweaks and other stuff like Catalyst I need to install again.

Is there a way to print all installed application and repositories (PPA and stuff) before a new install?

/Cheers

---

### Post by Impavidus on 2013-10-26
To get a list of all installed packages:```
sudo dpkg --get-selections >packagelist.txt
```
To restore later```
sudo dpkg --set-selections <packagelist.txt
sudo apt-get update
sudo apt-get dselect-upgrade
```
(just copying from another thread in the forum, never tried it myself).
Make a backup of your software sources to recover your PPAs.

But I think reinstalling is a bit of overkill in this situation. Yes, logfiles sometimes fill up rapidly and it's often a good thing to find out why, but to get rid of it you can just delete the log file, maybe reboot too.

---

### Post by VMC on 2013-10-26
To get the top 10 size from *var* use this"
```
sudo du -ah /var | sort -n -r | head -n 10
```

---

### Post by Azyx on 2013-10-26
Thanks.
For the tips :)

Have get rid off some old linux headers and stuff and are now down to 10GB, so reinstall are not necessary. 

/Cheers

---

