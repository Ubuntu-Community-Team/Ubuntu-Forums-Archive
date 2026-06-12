---
title: "Startup Scripts"
date: 2007-11-13
forum: General Help
---

### Post by maldojr88 on 2007-11-13
hey guys.....i donno if this is the best place to 
post this but here i go...
first off im running gutsy

well basically i just want to load gaim when i boot...
similar to msconfig in windows....like that applications start up 
during boot up.
the location of the application gaim...is 

/usr/bin/gaim

so what i did was i created a script call echo: 

#!/bin/sh
/usr/bin/gaim


next i ran these commands accomodate priviledges, place in correct directory and create Symbolic links from rc*.d directories to the /etc/init.d/echo directory

$sudo chmod +x echo
$mv echo /etc/init.d/echo
$sudo update-rc.d echo defaults


*When i reboot my computer the application does not open. However, when i run the script while Im logged in it works(opens application). Someone told me to use absolute paths in the script because when the scripts are run during boot up the PATH variable has not been set but I am using absolute paths!!!!!

AM i missing something???

Thanks in advance guys.

---

### Post by zvacet on 2007-11-13
**system<preferences>sessions>start up services>new**

---

### Post by maldojr88 on 2007-11-14
is there a way to do this via 
the command line.....im trying to learn most of the linux things
thru command mode..because if i learn it there then
i learn it anywhere

---

