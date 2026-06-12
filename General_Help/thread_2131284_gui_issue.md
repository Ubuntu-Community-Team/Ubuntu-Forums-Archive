---
title: "gui issue"
date: 2013-04-01
forum: General Help
---

### Post by autotron on 2013-04-01
I am new to these forums, and still learning ubuntu, i have setup many servers with ubuntu (meaning install needed modules and softwares for website) i have never install ubuntu on its own.
recently i purchased a server and had the server company install ver 12.04 on it and am having issues, i tried installing LAMP and phpmyadmin, on lamp install it seemed to work and displayed no errors Using
sudo apt-get install lamp-server^
the issue is durhing mysql portion of the install i did not get the usual graphical screen prompting for root pass etc, this wasnt a big issue, just added pass via console after, i then installed phpmyadmin and had the same issue, no graphical screen in console (putty)
after i could not access phpmyadmin via browser so purged both lamp and phpmyadmin to try again. this time i decided to try using tasksel using
tasksel
this command just put me back to command prompt so thought tasksel was not installed so did
apt-get install tasksel and recieved message saying tasksel already at highest version
so basically the issue is the graphical user input screens just wont show, is this a failed ubuntu install? or is there an easy fix?

---

### Post by steeldriver on 2013-04-01
Are you referring to the curses style reconfigure screens? they work fine for me from putty (on Windows 7) to Ubuntu 12.04 Server running on an old laptop on my LAN

For mysql-server, I did notice that 'sudo dpkg-reconfigure mysql-server' doesn't appear to do anything, however

```
sudo dpkg-reconfigure mysql-server**-5.5**
```

brings up the curses mysql root password dialog - you may need to modify that if your installed version isn't 5.5

The tasksel menu also works for me - maybe it is something to do with your local (putty) terminal configuration?

---

### Post by autotron on 2013-04-01
its not my putty, i have 5 other servers from various companies around the worls, all running various versions of ubuntu and all show these screens properly. example other servers if i do tasksel i get user select screen for install/uninstall various modules, this server tasksel after a second or two pause just returns to command prompt

---

