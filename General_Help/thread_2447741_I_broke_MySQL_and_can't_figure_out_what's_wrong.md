---
title: "I broke MySQL and can't figure out what's wrong"
date: 2020-07-24
forum: General Help
---

### Post by Abdul_Hakim on 2020-07-24
Ubuntu Server 20.04


Somehow in the course of trying to install `phpmyadmin`, I broke MySQL and I can't figure out how to fix it.


I originally installed the LAMP stack via `tasksel`. In the course of trying to install a wordpress site, I was trying to get phpmyadmin installed and I'm not sure what happened but now MySQL is broken. I'm sure I did something wrong somewhere I'm just not sure where.


I've already done `sudo apt purge` on `phpmyadmin` and `mysql-server`, as well as `autoremove` and `autoclean` after every uninstall. I also tried `mariadb-server` but this same exact problem happens whether I use mysql or mariadb.


I've also tried deleting `/etc/mysql` and `/var/lib/mysql` in the course of troubleshooting


At this point, `mariadb-server`, `mysql-server`, and `phpmyadmin` are all purged and autocleaned/autoremoved. I'm going to attempt installing `mariadb-server` again and I will record my results:




[Installation Output]([https://hastebin.com/irixedocak.sql](https://hastebin.com/irixedocak.sql))






So it seems like for some reason, dpkg is failing to properly configure the mariadb-common package after installation. I tried googling what "dpkg exit status 2" means, but couldn't find anything helpful 


Wasn't sure if I already had gdebi installed, but [this post]([https://askubuntu.com/questions/652941/dpkg-error-exit-status-2](https://askubuntu.com/questions/652941/dpkg-error-exit-status-2)) suggested installing it, so when I tried to install it, this happens: 


[Installing GDebi]([https://hastebin.com/taqarerade.cs](https://hastebin.com/taqarerade.cs))




So now it looks like this is going to effect all package installations going forward unless I purge mariadb or fix the problem.


If I try `sudo dpkg --configure -a` I get this:






[`sudo dpkg --configure -a`]([https://hastebin.com/eqilayoxis.makefile](https://hastebin.com/eqilayoxis.makefile))






And if I try `sudo apt --fix-broken install`:






[`sudo apt --fix-broken install`]([https://hastebin.com/uginuvubud.sql](https://hastebin.com/uginuvubud.sql))




As far as I can tell, for some reason dpkg is not completeting the configuration process after the package installation, and it's breaking everything. But it's only happening for `mysql-server`/`mariadb-server`, not for any other packages. I'm tempted to just nuke the server and reinstall Ubuntu but I'd really like to avoid that if possible.


I've also tried removing the `mysql-server`/`mariadb-server` packages with Synaptic instead of apt/dpkg, but it makes no difference, same problem happens upon reinstallation.


Does anyone know how to fix this without doing a whole server reinstallation? Thanks in advance

---

