---
title: "dpkg: error processing duplicity (--configure)"
date: 2014-03-10
forum: General Help
---

### Post by 13718484207 on 2014-03-10
When i type the command " sudo apt-get autoremove", it returns such errors.
```
After this operation, 0 B of additional disk space will be used.dpkg: error processing duplicity (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of deja-dup:
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
                                                                                       No apport report written because MaxReports is reached already
      No apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                                                                                                   deja-dup depends on duplicity (>= 0.6.14); however:
  Package duplicity is not configured yet.


dpkg: error processing deja-dup (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing python-apt (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: error processing python-dbus (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of ubuntu-system-service:
 ubuntu-system-service depends on python-apt (>= 0.7.0); however:
  Package python-apt is not configured yet.
 ubuntu-system-service depends on python-dbus; however:
  Package python-dbus is not configured yet.


dpkg: error processing ubuntu-system-service (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on ubuntu-system-service (>= 0.1.10); however:
  Package ubuntu-system-service is not configured yet.


dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on python-dbus (>= 0.80); however:
  Package python-dbus is not configured yet.


dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on hplip (>= 3.12.6-3ubuntu4.3); however:
  Package hplip is not configured yet.


dpkg: error processing printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 duplicity
 deja-dup
 python-apt
 python-dbus
 ubuntu-system-service
 gnome-control-center
 hplip
 printer-driver-postscript-hp
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
Does someone also have encountered  such problem? can somebody help me?
thank you !

---

### Post by ibjsb4 on 2014-03-10
Try a couple of maintenance commands.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one line at a time):

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by 13718484207 on 2014-03-10
I have tried these commands. but it returns the same errors.
When i typed 
```

**[COLOR=#ff0000]sudo dpkg --configure -a[/COLOR]**
dpkg: error processing duplicity (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: error processing python-dbus (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of deja-dup:
 deja-dup depends on duplicity (>= 0.6.14); however:
  Package duplicity is not configured yet.


dpkg: error processing deja-dup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-system-service:
 ubuntu-system-service depends on python-dbus; however:
  Package python-dbus is not configured yet.


dpkg: error processing ubuntu-system-service (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing python-apt (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on python-dbus (>= 0.80); however:
  Package python-dbus is not configured yet.


dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on ubuntu-system-service (>= 0.1.10); however:
  Package ubuntu-system-service is not configured yet.


dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on hplip (>= 3.12.6-3ubuntu4.3); however:
  Package hplip is not configured yet.


dpkg: error processing printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 duplicity
 python-dbus
 deja-dup
 ubuntu-system-service
 python-apt
 hplip
 gnome-control-center
 printer-driver-postscript-hp


[COLOR=#ff0000]**when i typed sudo apt-get -f install**[/COLOR]
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 231 not upgraded.
8 not fully installed or removed.
Need to get 0 B/516 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing duplicity (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of deja-dup:
 deja-dup depends on duplicity (>= 0.6.14); however:
  Package duplicity is not configured yet.


dpkg: error processing deja-dup (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: error processing python-apt (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: error processing python-dbus (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of ubuntu-system-service:
 ubuntu-system-service depends on python-apt (>= 0.7.0); however:
  Package python-apt is not configured yet.
 ubuntu-system-service depends on python-dbus; however:
  Package python-dbus is not configured yet.


dpkg: error processing ubuntu-system-service (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on ubuntu-system-service (>= 0.1.10); however:
  Package ubuntu-system-service is not configured yet.


dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigurNo apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               ed
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on python-dbus (>= 0.80); however:
  Package python-dbus is not configured yet.


dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on hplip (>= 3.12.6-3ubuntu4.3); however:
  Package hplip is not configured yet.


dpkg: error processing printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 duplicity
 deja-dup
 python-apt
 python-dbus
 ubuntu-system-service
 gnome-control-center
 hplip
 printer-driver-postscript-hp
E: Sub-process /usr/bin/dpkg returned an error code (1)


 

```

---

### Post by ibjsb4 on 2014-03-11
Do as suggested and try reinstalling those packages.

```
sudo apt-get install --reinstall **name-of-package**
```

---

### Post by 13718484207 on 2014-03-11
Thanks ! It does work for me.:p

---

