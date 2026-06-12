---
title: "Hibernate (resume) sometimes turns off networking"
date: 2015-10-29
forum: General Help
---

### Post by Ralph L on 2015-10-29
I am running xubuntu 14.04 using a wireless router.  Sometimes when I resume from hibernation, networking is disabled and I am must to do a complete restart to get it working again.  Although I can click on the network icon on my task panel and check the enable network box, the network won't restart.  Googling I found this solution ([http://ubuntuforums.org/showthread.php?t=2223566](http://ubuntuforums.org/showthread.php?t=2223566) ):
Enter into Terminal ```
sudo service network-manager restart
``` or
```
Put "service network-manager restart" in  /etc/pm/config.d/config file and it now resumes with networking.
```
Does anybody know if this is a reasonable solution that won't damage my system???  I don't want to install it if it will cause damage.

---

