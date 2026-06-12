---
title: "Dpkg: Dependency problems - leaving unconfigured"
date: 2013-12-18
forum: General Help
---

### Post by cessanfrancisco on 2013-12-18
I was doing "sudo apt-get upgrade" and got this:

Does anyone know what it means and how do I fix it?  Thanks.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0 B/769 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing dpkg-dev (--configure):
 package dpkg-dev is not ready for configuration
 cannot configure (current status `half-installed')
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on dpkg-dev (>= 1.16.2); however:
  Package dpkg-dev is not installed.

dpkg: error processing debhelper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alien:
 alien depends on debhelper (>= 7); however:
  Package debhelper is not configured yet.
 alien depends on dpkg-dev; however:
  Package dpkg-dev is not installed.

dpkg: error processing alien (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on alien (>= 8.36); however:
  Package alien is not configured yet.

dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core (>= 4.1+Debian11ubuntu4); however:
  Package lsb-core is not configured yet.

dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration ofNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                            No apport report written because the error message indicates its a followup error from a previous failure.
                      No apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                     lsb-cxx:
 lsb-cxx depends on lsb-core (>= 4.1+Debian11ubuntu4); however:
  Package lsb-core is not configured yet.

dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-multimedia:
 lsb-multimedia depends on lsb-core (>= 4.1+Debian11ubuntu4); however:
  Package lsb-core is not configured yet.

dpkg: error processing lsb-multimedia (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-desktop:
 lsb-desktop depends on lsb-graphics (>= 4.1+Debian11ubuntu4); however:
  Package lsb-graphics is not configured yet.
 lsb-desktop depends on lsb-multimedia (>= 4.1+Debian11ubuntu4); however:
  Package lsb-multimedia is not configured yet.

dpkg: error processing lsb-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-printing:
 lsb-printing depends on lsb-core (>= 4.1+Debian11ubuntu4); however:
  Package lsb-core is not configured yet.

dpkg: error processing lsb-printing (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-languages:
 lsb-languages depends on lsb-core (>= 4.1+Debian11ubuntu4); however:
  Package lsb-core is not configured yet.

dpkg: error processing lsb-languages (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core (>= 4.1+Debian11ubuntu4); however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics (>= 4.1+Debian11ubuntu4); however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx (>= 4.1+Debian11ubuntu4); however:
  Package lsb-cxx is not configured yet.
 lsb depends on lsb-desktop (>= 4.1+Debian11ubuntu4); however:
  Package lsb-desktop is not configured yet.
 lsb depends on lsb-printing (>= 4.1+Debian11ubuntu4); however:
  Package lsb-printing is not configured yet.
 lsb depends on lsb-languages (>= 4.1+Debian11ubuntu4); however:
  Package lsb-languages is not configured yet.

dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gutenprint:
 gutenprint depends on lsb (>= 3.1); however:
  Package lsb is not configured yet.

dpkg: error processing gutenprint (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dpkg-dev
 debhelper
 alien
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb-multimedia
 lsb-desktop
 lsb-printing
 lsb-languages
 lsb
 gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by tgalati4 on 2013-12-18
The first error is the clue:

dpkg: error processing **dpkg-dev** (--configure):

Are you doing development work on dpkg?  Why did you install this?

Alien is a package to convert RedHat/Fedora rpm packages to Debian packages, so why did you install this?

Try removing *dpkg-dev* and *alien* if you are not using them.

---

### Post by cessanfrancisco on 2013-12-18
Thanks.  I was trying to install this package, gutenprint (5.0.1-1lsb3.1), through synaptic but something went awry during installation.  I tried your suggestion and this is what I am getting now:



```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/769 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing dpkg-dev (--configure):
 package dpkg-dev is not ready for configuration
 cannot configure (current status `half-installed')
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 dpkg-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
chad@UL80jt:~$ sudo apt-get remove dpkg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dpkg-dev
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,670 kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing dpkg-dev (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 dpkg-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by mörgæs on 2013-12-18
Please use a more informative thread title. 
Changed.

---

### Post by cessanfrancisco on 2013-12-18
@tgalati4
Thanks!  I reinstalled "dpkg-dev" through Synaptics and then completely removed it.  Success!  Thanks for pointing me in the right direction.

@mörgæs
Sorry about that.  I wasn't sure what to title thread at first.  Thanks for changing the name.

---

### Post by mörgæs on 2013-12-18
Ok, please mark the thread 'solved'.

---

### Post by tgalati4 on 2013-12-18
In the future, you can try clearing your cache:

```
sudo apt-get purge
sudo apt-get clean
sudo apt-get check
```

---

### Post by cessanfrancisco on 2013-12-21
@tgalati4
Thanks!  So just to clarify, by simply using:

```
sudo apt-get purge
```

...without specifying a package or application, will clear my cache?

Thanks.

---

