---
title: "Firejail DBUS Warning"
date: 2017-12-13
forum: General Help
---

### Post by pointy2 on 2017-12-13
A fresh install of Firejail on Artful gives this output when launching FF from terminal. Firefox launches and works, however these warnings are puzzling. A Google and forum search didn't seem to yield any results. 

        ```
quasimoto@esmerelda:~$ firejail firefox
        Reading profile /etc/firejail/firefox.profile
        Reading profile /etc/firejail/disable-common.inc
        Reading profile /etc/firejail/disable-devel.inc
        Reading profile /etc/firejail/disable-programs.inc
        Reading profile /etc/firejail/whitelist-common.inc
        Parent pid 5435, child pid 5437
        Blacklist violations are logged to syslog
        Child process initialized in 70.15 ms

       (firefox:5): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
       Failed to connect to socket /run/user/1000/bus: Permission denied

         (firefox:5): LIBDBUSMENU-GLIB-WARNING **: Unable to get session bus: Could not connect: Permission denied

        (firefox:5): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
        Failed to connect to socket /run/user/1000/bus: Permission denied

        (firefox:5): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
        Failed to connect to socket /run/user/1000/bus: Permission denied

        (firefox:5): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
        Failed to connect to socket /run/user/1000/bus: Permission denied

        
```

Does the forum have an idea of what this might affect, and how to fix the errors?
*EDIT* exit command doesn't allow to close the terminal. There is no name/user profile **quasimoto@esmerelda:~$**

---

### Post by litlesam on 2017-12-13
Hi, Have you tried the following?

```
firejail /usr/bin/firefox
```

or

```
firejail --noprofile /usr/bin/firefox
```

---

