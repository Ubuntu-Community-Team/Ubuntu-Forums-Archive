---
title: "Ubuntu/Linux equivalent of autoexec.bat"
date: 2008-01-21
forum: General Help
---

### Post by stchman on 2008-01-21
I would like to know if there is a configuration file that I can run processes at startup.  I am aware of the System >Preferences >Sessions, but that does not do root stuff.

Thanks.

---

### Post by az on 2008-01-21
By default, you boot into runlevel 2.

All start (S) and stop (K) scripts are in /etc/rc.d/* and are  symlinks to the scripts in /etc/init.d.

---

### Post by Whiffle on 2008-01-21
/etc/rc.local 

is what you're looking for.

---

