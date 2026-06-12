---
title: "Error trying to fix broken packages"
date: 2013-09-25
forum: General Help
---

### Post by lads on 2013-09-25
Hello everyone,

After upgrading some GIS software synaptic is complaining that I have a few broken packages. I tried to mark them for re-install but during the process I'm getting back this error:
> 
E: /var/cache/apt/archives/postgresql-9.1-postgis-2.0-scripts_2.0.3-2~precise4_all.deb: trying to overwrite '/usr/share/postgresql/9.1/contrib/postgis-2.0/rtpostgis_upgrade_20_minor.sql', which is also in package postgresql-9.1-postgis 2.0.1-2~precise3

The same happens if I try to mark these packages for removal. I also tried to fix it in the command line, but the result isn't much different:

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  qgis-plugin-grass-common libgeos-3.3.3 python-gdal libqgis1.8.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgdal1h libmapserver-6.2.1 libqgis2.0.1 postgresql-9.1-postgis-2.0 postgresql-9.1-postgis-2.0-scripts qgis-common
Suggested packages:
  libmapscript-perl libmapscript-ruby
The following packages will be REMOVED
  libgdal1 postgresql-9.1-postgis
The following NEW packages will be installed
  libgdal1h libmapserver-6.2.1 libqgis2.0.1 postgresql-9.1-postgis-2.0 postgresql-9.1-postgis-2.0-scripts
The following packages will be upgraded:
  qgis-common
1 upgraded, 5 newly installed, 2 to remove and 9 not upgraded.
7 not fully installed or removed.
Need to get 0 B/25.0 MB of archives.
After this operation, 27.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 466362 files and directories currently installed.)
Unpacking postgresql-9.1-postgis-2.0-scripts (from .../postgresql-9.1-postgis-2.0-scripts_2.0.3-2~precise4_all.deb) ...
dpkg: error processing /var/cache/apt/archives/postgresql-9.1-postgis-2.0-scripts_2.0.3-2~precise4_all.deb (--unpack):
 trying to overwrite '/usr/share/postgresql/9.1/contrib/postgis-2.0/rtpostgis_upgrade_20_minor.sql', which is also in package postgresql-9.1-postgis 2.0.1-2~precise3
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/postgresql-9.1-postgis-2.0-scripts_2.0.3-2~precise4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Something seems wrong with postgis or postgres, but I don't know how to fix it. Any hints would be welcome. Thanks.

---

### Post by bkline on 2013-09-25
Here's a thread with useful advice for when the package manager gets tied up in knots:

[http://ubuntuforums.org/showthread.php?t=1780047](http://ubuntuforums.org/showthread.php?t=1780047)

---

### Post by hg-knight on 2013-09-25
if you have synaptic then its possible to fix from that.
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by lads on 2013-09-26
Thank you all for the replies. The only way I found to fix this was to remove all the packages marked as broken in a single *apt-get remove* command. It was an iterative process, each time I issued the command it would declare a few more packages as broken and I'd add them to the list. Eventually it executed (removing about 20 packages) and things went back to normal.

---

