---
title: "Machine not starting certain services on boot"
date: 2007-03-01
forum: General Help
---

### Post by speedsix on 2007-03-01
Had a power cut the other day, rebooted my server machine and while it boots into Ubuntu fine, it doesn't seem to be starting alot of the services such as Apache/SSH/nfs etc.

I can start the services manually after it's booted (sudo /etc/init.d/apache2 start). Also ctrl+alt+F1 etc. doesn't bring up a terminal, just a flashing cursor.

Any idea where I can begin looking for the problem? Not sure which log to check for problems with scripts in init.d and the boot process?



Thanks

Dom

---

### Post by llamakc on 2007-03-01
type "ctrl-alt-F2" to get a console (or -F3 through F6).

---

### Post by speedsix on 2007-03-01
I need to find out why alot of the services don't start on boot. The machine doesn't have a monitor so if sshd doesn't start it's a major pain as I can't access it!



Dom.

---

