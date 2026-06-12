---
title: "Adding wifi-radar to start up"
date: 2007-10-27
forum: General Help
---

### Post by nastavirss on 2007-10-27
I added the wifi-radar  program to my start up (/etc/init.d/wifi-radar)

But i guess since it requires root access its not showing up automatically when i boot (though its running in the Task manager). 

Can anyone help me with this..

---

### Post by fragos on 2007-10-27
Gnome-network-manager is installed by default.  You can't run both it and wifi-radar -- they interfere with each other.  You at least need to do System-> Preferences-> Sessions and uncheck "Network Manager".  You may also need to start wifi-radar here as well.

---

