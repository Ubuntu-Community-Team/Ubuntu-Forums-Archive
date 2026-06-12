---
title: "(xubuntu 12.04) software-center will not install/remove"
date: 2012-11-02
forum: General Help
---

### Post by gerret38 on 2012-11-02
Reinstall dont help.
software-center in terminal gives

ger@ubuntu:~$ software-center 
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-LmHSj9/pkcs11: Bestand of map bestaat niet ger@ubuntu:~$ software-center 
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-LmHSj9/pkcs11: Bestand of map bestaat niet 
2012-10-31 15:03:46,987 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')' 
2012-10-31 15:03:46,987 - root - ERROR - Could not find any typelib for Gst 
2012-10-31 15:03:47,076 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None' 
2012-10-31 15:03:47,083 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True 
2012-10-31 15:03:47,191 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files' 
2012-10-31 15:03:47,741 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file 
2012-10-31 15:03:48,205 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None. 
2012-10-31 15:03:48,718 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open() 
2012-10-31 15:03:56,159 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files' 
2012-10-31 15:03:59,623 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0 
2012-10-31 15:03:59,624 - softwarecenter.db.database - INFO - reopen() database 
2012-10-31 15:03:59,624 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True 

2012-10-31 15:03:46,987 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')' 
2012-10-31 15:03:46,987 - root - ERROR - Could not find any typelib for Gst 
2012-10-31 15:03:47,076 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None' 
2012-10-31 15:03:47,083 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True 
2012-10-31 15:03:47,191 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files' 
2012-10-31 15:03:47,741 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file 
2012-10-31 15:03:48,205 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None. 
2012-10-31 15:03:48,718 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open() 
2012-10-31 15:03:56,159 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files' 
2012-10-31 15:03:59,623 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0 
2012-10-31 15:03:59,624 - softwarecenter.db.database - INFO - reopen() database 
2012-10-31 15:03:59,624 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True 

How can i fix this?

---

### Post by kleenex on 2012-11-02
Hi, it seems to be related to this bug; [_https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1066250  _]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1066250")If you could, please report, that you are also affected by this bug. It should help to a faster resolve this problem.

---

### Post by ibjsb4 on 2012-11-02
I know you tried reinstall, but what about ([in terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal")):

sudo apt-get purge software-center && sudo apt-get install software-center

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by gerret38 on 2012-11-02
sudo apt-get purge software-center && sudo apt-get install software-center** make no difference**,yet thanks

---

### Post by pqwoerituytrueiwoq on 2012-11-02
could be it is not working cause of broken packages
```
sudo apt-get -f install 
```

---

### Post by gerret38 on 2012-11-04
unfortunately no result.

---

