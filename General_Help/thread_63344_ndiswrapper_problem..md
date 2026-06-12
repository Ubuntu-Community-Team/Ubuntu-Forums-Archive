---
title: "ndiswrapper problem."
date: 2005-09-07
forum: General Help
---

### Post by xVern on 2005-09-07
first its saying i already have it installed.

then when i try to remove it, its saying its not installed.

its something like this:
root@ubuntu: ndiswrapper -i ~/desktop/windows_drivers/bcmwl5.inf
bcmwl5.inf installed already. -e to remove
root@ubuntu: ndiswrapper -e ~/desktop/windows_drivers/bcmwl5.inf
bcmwl5.inf is not installed. -l to see a list of installed drivers


im using the ndiswrapper from the synaptic package manager.

anyone know whats going on?

---

### Post by Steve1961 on 2005-09-07
Have to tried uninstalling ndiswrapper-utils from synaptic?  If this solves the problem download and install the ndiswrapper 1.2 package.  I've had more success with this version and broadcom drivers.  This is how I installed it:

[http://ubuntuforums.org/showthread.php?p=334239#post334239](http://ubuntuforums.org/showthread.php?p=334239#post334239)

---

### Post by xVern on 2005-09-07
[QUOTE=Steve1961]Have to tried uninstalling ndiswrapper-utils from synaptic?  If this solves the problem download and install the ndiswrapper 1.2 package.  I've had more success with this version and broadcom drivers.  This is how I installed it:

[http://ubuntuforums.org/showthread.php?p=334239#post334239](http://ubuntuforums.org/showthread.php?p=334239#post334239)[/QUOTE]

i tried that way, and its still says "bcmwl5 invalid" when i do the '-l' command.

---

### Post by Steve1961 on 2005-09-08
Try using a different driver.  The ndiswrapper sourcefoge site has a link for a del driver called bcmwl5a in the list for the belkin f5d7000 ver 3.  If you have version 3 of the broadcom chipset you might have more success with this

---

