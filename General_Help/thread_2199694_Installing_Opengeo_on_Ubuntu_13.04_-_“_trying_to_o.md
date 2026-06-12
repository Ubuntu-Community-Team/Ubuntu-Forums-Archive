---
title: "Installing Opengeo on Ubuntu 13.04 - “ trying to overwrite '/usr/bin/shp2pgsql-gui'"
date: 2014-01-15
forum: General Help
---

### Post by cjennison92 on 2014-01-15
[SIZE=4][COLOR=#333333][FONT=Helvetica Neue]I am trying to upgrade Opengeo Suite from 2.0 to 4.0, specifically for the upgrade of PostGis 2.0 to 2.1, I followed the instructions outlined on this page: [http://suite.opengeo.org/opengeo-docs/installation/ubuntu/upgrade.html](http://suite.opengeo.org/opengeo-docs/installation/ubuntu/upgrade.html) But had no success. I am on Ubuntu 13.04, but am aware that Opengeo and geoserver do not fully support 13.04, but are only officially supported for 10.X. From what I can see, I have a package conflict and I need to know how to resolve it.[/FONT][/COLOR]
[/SIZE][COLOR=#333333][FONT=Helvetica Neue][SIZE=4]I realized I hadn't fully installed opengeo-client or postgis 2.1, so I used apt-get install and received this:[/SIZE]
[/FONT][/COLOR]
```
The following packages have unmet dependencies:
opengeo-client : Depends: postgis-2.1 (>= 2.1.0) but it is not installed
postgresql-9.3-postgis-2.1 : Depends: postgis-2.1 but it is not installed
E: Unmet dependencies. Try using -f.
```


[SIZE=4][COLOR=#333333][FONT=Helvetica Neue]So I used -f and received..
[/FONT][/COLOR][/SIZE]

```
The following extra packages will be installed:
  postgis-2.1
The following NEW packages will be installed:
  postgis-2.1
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
28 not fully installed or removed.
Need to get 0 B/701 kB of archives.
After this operation, 1,839 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: warning: files list file for package 'postgresql-9.2-postgis2' missing; assuming                     package has no files currently installed
(Reading database ... 384786 files and directories currently installed.)
Unpacking postgis-2.1 (from .../postgis-2.1_2.1.0-1+opengeo_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/postgis-2.1_2.1.0-1+opengeo_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/shp2pgsql-gui', which is also in package postgis 1.5.3-2ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/postgis-2.1_2.1.0-1+opengeo_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

[COLOR=#333333][FONT=Helvetica Neue][SIZE=4]I was recommended to go back and forth with **apt-get upgrade** and **apt-get -f install** to isolate the issue. But I am assuming that Postgis 1.5 is still in use, but I cannot find where to remove it. (If it is possible to do a complete wipe of the Opengeo suite then I can also do that if it would be simpler, all of my data is backed up)[/SIZE]

[SIZE=4]*What do I need to do to resolve this?*[/SIZE][/FONT][/COLOR][SIZE=4]
[COLOR=#333333][FONT=Helvetica Neue]Please be as specific as possible in what to do, I'm not experienced in Linux. Most of my work is on the GIS/Web side.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]My Ubuntu release is: Ubuntu 13.04 Raring[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Let me know if I need to provide any more information (and how to provide it) and I'll be as hasteful as possible.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Thank you.



Edit:
I have tried to uninstall the entire suite, with 
[/FONT][/COLOR][/SIZE]```
sudo apt-get --purge remove opengeo-suite
```
but I am getting the same "The following packages have unmet dependencies" response.

---

### Post by egeezer on 2014-01-15
Are you aware that the last kernel update for 13.04 has just come out, and that it will no longer be supported after January 27?  Since you say your data is all backed up, it might be time to start over with a fresh install of 13.10 or the 12.04 LTS and tackle the problem there.

---

### Post by Bucky Ball on 2014-01-15
> **egeezer said:**
>  Since you say your data is all backed up, it might be time to start over with a fresh install of 13.10 or the 12.04 LTS and tackle the problem there.

+1. This is a good idea. 12.04 and 13.10 are both directly upgradeable to 14.04 LTS when it is released in April, supported for five years.

Have you seen this?

[http://dev.horizon.opengeo.org/opengeo-docs/installation/linux/ubuntu/suite.html](http://dev.horizon.opengeo.org/opengeo-docs/installation/linux/ubuntu/suite.html)

Also this from Boundless (formerly Opengeo):

[http://boundlessgeo.com/solutions/opengeo-suite/download/](http://boundlessgeo.com/solutions/opengeo-suite/download/)

There is a download specifically for Ubuntu.

---

### Post by cjennison92 on 2014-01-15
> **Bucky Ball said:**
> +1. This is a good idea. 12.04 and 13.10 are both directly upgradeable to 14.04 LTS when it is released in April, supported for five years.

Have you seen this?

[http://dev.horizon.opengeo.org/opengeo-docs/installation/linux/ubuntu/suite.html](http://dev.horizon.opengeo.org/opengeo-docs/installation/linux/ubuntu/suite.html)

Also this from Boundless (formerly Opengeo):

[http://boundlessgeo.com/solutions/opengeo-suite/download/](http://boundlessgeo.com/solutions/opengeo-suite/download/)

There is a download specifically for Ubuntu.

You're right, I will be switching down to 12.04. I think when I initially installed 12.04 it wasn't supported and I upgraded out of curiosity. 
I have learned my lesson. 
Thanks you!

---

