---
title: "Ordering startup scripts"
date: 2008-05-14
forum: General Help
---

### Post by tjajab on 2008-05-14
I have some small desktop issues, and many of the solutions I have found on the forum includes some kind of startup script, which may or may not involve restarting the window-manager. The problem is that some of those script has to be run after everything else in the session has started, and to solve this the sleep command is often used.

I wonder is there a better way to make a startup script to run after certain other scripts are run? Sometimes I feel that even sleep 100 does not work, but when I manually run the script just seconds after startup, it works fine.

---

### Post by joshsmith on 2008-05-14
i never worked out what the "ordering" options meant in system>preferences>sessions>current session

but maybe that is what you want

---

### Post by skiamakhe on 2008-05-14
Directories to be concerned with:

/etc/init.d - start up scripts
/etc/rc3.d - links to scripts for Run Level 3 (text mode)
/etc/rc5.d - links to scripts for Run Level 5 (gui mode, the ubuntu default)
/etc/rc6.d - links to scripts for Run Level 6 (shutdown)
/etc/rcS.d - links to scripts for all run levels

For more on run levels, look here: [http://www.networkclue.com/os/Linux/run-levels.aspx](http://www.networkclue.com/os/Linux/run-levels.aspx)

Put your start up scripts in init.d, then symbolic links in the appropriate run level directory. The name of the link is the key. It's in this format:

[K/S]##<whatever>

ex: K01myscript, S92myscript

K is a kill script and is executed on shutdown, S is a startup script. The numbers set the order (S01myscript will execute before S02myscript).

To create a symbolic link: ln -s destdir linkname
ex: ln -s /etc/init.d/myscript /etc/rc5.d/S99myscript

---

### Post by joshsmith on 2008-05-14
@skiamakhe
you dont really want to run (almost all) scripts at this level (ie at the system start), especially if you are a new user

it would be better if you could run the scripts in your session. where you are not running them as superuser, and where they only affect your user

its the wrong level for "small desktop issues"

---

### Post by kevdog on 2008-05-14
Isn't run level 4 the deault level for Ubuntu and Debian?  And isn't the concept of run levels for debian based distros kind of antiquated?

---

### Post by rubicon on 2008-05-14
It is **2** level, yes it is default and always used in debian and its derivatives (among with 0, 1, 6 and S). 

Antiquated.. Huh, well said :D

---

