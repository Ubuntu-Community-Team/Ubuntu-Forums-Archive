---
title: "gnome doesn't boot"
date: 2007-07-13
forum: General Help
---

### Post by metricben on 2007-07-13
Yesterday I was trying to setup a LAMP server for testing web design and found numerous guides explaining various ways to do this.  One that seemed very simple and easy was the "tasksel" command.  I entered this program and it gave me options about what to install so I selected "LAMP Server" and deselected "Ubuntu Desktop" as I didn't want Ubuntu to be completely reinstalled.  After pressing OK, I noticed a very large apt-get command on the screen so quickly scrolled to the top and realized it was trying to remove my whole system!  I quickly hit ctrl-c but only after it had removed 3 or so packages.  Apt-get was broken so I ran "sudo dpkg --configure -a" to fix my packages then went ahead to individually install apache2, php5 and mysql.  When I tried to boot this morning, the login screen appears as per usual, but when I try to login normally it just hangs on a black screen.  I can login in failsafe mode which lead me to believe it was a startup script, so I used BUM to reselect apache and mysql, but that had no affect.  I should really like to fix this problem without reinstalling my OS so welcome any suggestions.

I know the problem must be something that a normal login tries but a failsafe does not.

Thanks
Ben

---

