---
title: "how to initiate a service (application) on startup"
date: 2007-04-23
forum: General Help
---

### Post by tozebr on 2007-04-23
Hello
Sorry but i don have find anything in forum with this.

i've instaled apache2 , php5 and mysql
but apache2 dont  start in boot, i have to manualy start it by:
sudo /usr/local/apache2/bin/apachectrl start

how can i start it at boot time ?

Thankx and sorry for my poor english

---

### Post by DoktorSeven on 2007-04-23
The preferred way to start something is through the scripts in /etc/init.d/ (**/etc/init.d/apache2 start**).

However, from what I can tell, you manually installed Apache (since it's in /usr/local/) so there is probably not a script in /etc/init.d; any reason you didn't install apache2 by apt?  Not only does it correctly install an init script, but enables it at boot by default.

If you have to have your custom install, you'll need to look into writing an init script for it (look at the other scripts in /etc/init.d for the method).  You then symlink (ln -s) this script to /etc/rc2.d/ as a link named S(number)(scriptname), for example **S90apache2** (symlinked to ../init.d/apache2 or whatever you called the script; the number is the rough order that the program is started at boot).

As you can tell, installing it via apt is the easier method... :)

---

### Post by tozebr on 2007-04-23
Thankx, but i instaled it by hand, i have tryed to install it with tomcat and it didnt work.

i will try to make my init script

thanks a lot

---

