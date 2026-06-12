---
title: "HP Envy 4501 all in one printer - need to install"
date: 2015-03-19
forum: General Help
---

### Post by michael-piziak on 2015-03-19
HP Envy 4501 all in one printer - need to install

---

### Post by oldfred on 2015-03-19
Best to install hplip from HP directly. The copy in repository is usually not current enough.

From some other threads:
Ubuntu 14.04 supplies HPLIP 3.11.5 by default, which does not support your printer.
You must ensure latest HPLIP version (recommemded), or at least HPLIP 3.13.6 in order to use your printer with Ubuntu 14.04.
Creates lots of folders & files, best if in its own sub-directory

HPLIP issue on 14.04 - manual download of plugin to solve
[http://ubuntuforums.org/showthread.php?t=2230875](http://ubuntuforums.org/showthread.php?t=2230875)
HP printers broken in Linux? Here's a fix. 
[http://www.dedoimedo.com/computers/linux-hp-printing.html](http://www.dedoimedo.com/computers/linux-hp-printing.html)


[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version, best not to use this unless older model printer.
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade


If you get this error, I just ignore it:
No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

---

### Post by michael-piziak on 2015-03-19
Thanks!

Marking this thread as solved.

---

