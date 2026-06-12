---
title: "ddclient on bootUp"
date: 2005-05-07
forum: General Help
---

### Post by FLEO on 2005-05-07
Hi guys,

I configured ddclient properly but I want to start the deamon automatically on startup. Do you have ideas where to put this line:

/usr/sbin/ddclient -daemon 300 -syslog

because they say to put that line in the startUp script but where is it ?

Thanks,

FLEO

---

### Post by JonahRowley on 2005-05-08
ddclient comes with a startup script, **/etc/init.d/ddclient**.  The "proper" way to do this would be to edit the ddclient defaults file at /etc/defaults/ddclient, specifically setting the **run_daemon** variable.  After that, either reboot, or **sudo /etc/init.d/ddclient start**.

---

### Post by FLEO on 2005-05-14
Perfect I did what you said and it works fine.  ;-) 

Thanks, 

FLEO

---

