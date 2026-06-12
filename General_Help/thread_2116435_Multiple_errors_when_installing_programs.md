---
title: "Multiple errors when installing programs"
date: 2013-02-15
forum: General Help
---

### Post by MrRikhado on 2013-02-15
Hi, I've reinstalled Ubuntu after switching to a new PC. Whenever I try to install or uninstall a program, I get a whole bunch of errors. Although the programs seem to work fine, is there some way to get rid of these errors? This has never happened on my old computer.

I've included the details of uninstalling jockey below. It's exactly the same for all other programs.

Error log:

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 193359 files and directories currently installed.)
Removing jockey-kde ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
dpkg: error processing libkpimidentities4 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of libkalarmcal2:
 libkalarmcal2 depends on libkpimidentities4 (= 4:4.9.4-0ubuntu0.1); however:
  Package libkpimidentities4 is not configured yet.

dpkg: error processing libkalarmcal2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepim-runtime:
 kdepim-runtime depends on libkalarmcal2; however:
  Package libkalarmcal2 is not configured yet.
 kdepim-runtime depends on libkpimidentities4 (>= 4:4.9.4); however:
  Package libkpimidentities4 is not configured yet.

dpkg: error processing kdepim-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkgapi0:amd64:
 libkgapi0:amd64 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkgapi0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-kNo apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
de4:
 python-kde4 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing python-kde4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkolab0:
 libkolab0 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkolab0 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libkpimidentities4
 libkalarmcal2
 kdepim-runtime
 libkgapi0:amd64
 python-kde4
 libkolab0
dpkg: error processing libkpimidentities4 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of kdepim-runtime:
 kdepim-runtime depends on libkpimidentities4 (>= 4:4.9.4); however:
  Package libkpimidentities4 is not configured yet.

dpkg: error processing kdepim-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkalarmcal2:
 libkalarmcal2 depends on libkpimidentities4 (= 4:4.9.4-0ubuntu0.1); however:
  Package libkpimidentities4 is not configured yet.

dpkg: error processing libkalarmcal2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-kde4:
 python-kde4 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing python-kde4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkolab0:
 libkolab0 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkolab0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkgapi0:amd64:
 libkgapi0:amd64 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkgapi0:amd64 (--configure):
 dependency problems - leaving unconfigured
```


Is there anything I can do to fix this?

---

### Post by claracc on 2013-02-16
You have to add more information in order to obtain good advice:

What ubuntu have you installed? 12.04, 12.10? and what desktop, kde?
Which way have you installed ubuntu: wubi?, dual boot with windows?. What have you used for installing usb, cd ?

What are the specs of uour hardware?

---

