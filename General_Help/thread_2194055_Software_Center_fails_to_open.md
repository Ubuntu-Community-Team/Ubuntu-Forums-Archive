---
title: "Software Center fails to open"
date: 2013-12-16
forum: General Help
---

### Post by carolyn-meinel-d on 2013-12-16
After I upgraded to Ububtu 13.10, when I try to open Software Center, I get this message:

2013-12-16 02:35:21,588 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-12-16 02:35:23,721 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2013-12-16 02:35:24,257 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-12-16 02:35:24,276 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-12-16 02:35:24,319 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-12-16 02:35:24,319 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-12-16 02:35:24,447 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Killed

---

### Post by Y^2om&amp;#7sgP on 2013-12-16
Have you tried removing and re-installing?

sudo apt-get purge software-center

sudo apt-get install software-center

---

### Post by ibjsb4 on 2013-12-16
Another option would be to use the terminal to open the software center.  [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
gksudo software-center
```

This seems to be a [reoccurring problem]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+center+will+not+open&sa=Search&cof=FORID:9").  You could use a different package manager until you get this sorted out.  One good one is [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9").  If you wish to install it, open a terminal and enter:

```
sudo apt-get install synaptic
```

---

### Post by jimmyh1972 on 2013-12-17
[COLOR=#000000]sudo apt-get purge software-center

sudo apt-get autoremove

sudo apt-get autoclean

sudo apt-get update

[/COLOR][COLOR=#000000]sudo apt-get install software-center[/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by carolyn-meinel-d on 2014-01-10
> **ibjsb4 said:**
> Another option would be to use the terminal to open the software center.  [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
gksudo software-center
```

This seems to be a [reoccurring problem]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+center+will+not+open&sa=Search&cof=FORID:9").  You could use a different package manager until you get this sorted out.  One good one is [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9").  If you wish to install it, open a terminal and enter:

```
sudo apt-get install synaptic
```

Thank you, the synaptic package manager works well.

---

### Post by carolyn-meinel-d on 2014-01-10
> **jimmyh1972 said:**
> [COLOR=#000000]sudo apt-get purge software-center

sudo apt-get autoremove

sudo apt-get autoclean

sudo apt-get update

[/COLOR][COLOR=#000000]sudo apt-get install software-center[/COLOR][COLOR=#000000]

[/COLOR]

This did not work. Here are the error messages:

WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application

---

### Post by jeanjd63 on 2014-01-10
Hello,
You can see this [post]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1163886").
There is some solutions.

Bye

---

