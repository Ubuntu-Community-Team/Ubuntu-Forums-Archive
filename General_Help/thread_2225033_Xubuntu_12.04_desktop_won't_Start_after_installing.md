---
title: "Xubuntu 12.04 desktop won't Start after installing Joomla"
date: 2014-05-19
forum: General Help
---

### Post by OldPowel on 2014-05-19
I'm a total newbie and tried to install the CMS-Platform Joomla! to create a Homepage. With the terminal "apt-get install […]" i installed apache2, MySQL and phpadmin. With "tasksel", i installed the LAMP-server. Everything worked. 
Problem: when rebooting, my laptop won't load the desktop. Following lines are showed instead: 
*St [OK]
System V runlevel compatibility
apache2: could not reliable determinate the server's fully qualified domain name, using 127.0.1.1 for ServerName 
*Stopping save kernel messages    [OK]
*Starting web Server apache2      [OK]
*checking battery state...        [OK]

Still i am able to enter the terminal with alt+f1.

And suggestions how to geht back the normal desktop?
Thank you!

---

### Post by Erik1984 on 2014-05-19
What happens if you run

```

startx

```

from tty1 (ctrl + alt + F1)?

---

### Post by OldPowel on 2014-05-26
Thank you very much!
"startx" was good, but "sudo startxfce4" was better, couldnt get HSPA connection with your version. 
Still you made my day!

---

