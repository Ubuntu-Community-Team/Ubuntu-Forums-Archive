---
title: "libre office - unmet dependancies - unable to fix"
date: 2013-04-11
forum: General Help
---

### Post by jreed72 on 2013-04-11
[FONT=century gothic]Background - Trying to flip from using Libre Office to Open Office to solve a different issue irrelevant to this. That uninstall and install went ok, however I decided to go back to Libre Office. I uninstalled open Office and tried to install Libre Office with Software center. During this install an error occured. (can't remember what at this point). Now Software center wants to repair the package catalogue, but keeps throwing an error.
I move to command line and run apt-get clean - update - upgrade and get:

[/FONT][FONT=courier new]Get:1 xxx[://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu/]("http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu/") quantal/main libreoffice-common all 1:4.0.2~rc2-0ubuntu1~quantal1 [11.6 MB]
Fetched 11.6 MB in 3min 33s (54.3 kB/s) 
(Reading database ... 219910 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.0.2~rc2-0ubuntu1~quantal1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.0.2~rc2-0ubuntu1~quantal1_all.deb (--unpack):
trying to overwrite '/usr/bin/soffice', which is also in package openoffice.org-debian-menus 3.4-9593
No apport report written because MaxReports is reached already
rmdir: failed to remove `/var/lib/libreoffice/share/prereg/': No such file or directory
rmdir: failed to remove `/var/lib/libreoffice/share/': Directory not empty
rmdir: failed to remove `/var/lib/libreoffice/program/': No such file or directory
rmdir: failed to remove `/var/lib/libreoffice': Directory not empty
rmdir: failed to remove `/var/lib/libreoffice': Directory not empty
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Errors were encountered while processing:
/var/cache/apt/archives/libreoffice-common_1%3a4.0.2~rc2-0ubuntu1~quantal1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

[FONT=century gothic]I then tried to fix these dependancies using [FONT=courier new]apt-get install -f[/FONT] and received much the same as above. I have also tried remove and purge on both open office/libreoffice, but keeps coming back to these sependancy issues. I am not a strong linux user, so kinda baffled of how to fix this.
any help would be appreciated.
running ubuntu 12.10 - 64bit[/FONT][/FONT]

---

### Post by blackbird34 on 2013-04-11
Have you tried removing the LibreOffice PPA? 
And also do you have Synaptic ("Synaptic Package Manager") installed? It is a more advanced software manager than the default Software Centre, and it has several custom filters, most notably: when you look at the bottom left of the panel, and select "Custom Filters", one of these is for "Broken" packages. This might help you find out what is getting in the way, and removing it.

---

### Post by jreed72 on 2013-04-11
I have tried removing using remove and purge : apt-get remove libreoffice*.* but it gives me an extended list of packages that are not installed, and then unmet dependencies at the end. Nomatter how many times I try to meet these dependencies it just keeps failing...
No I don't have Synaptic installed, I tried earlier, but it just keeps coming back to these dependency issues needing to be fullfilled...

The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.0.2~rc2) but it is not going to be installed
 libreoffice-emailmerge : Depends: libreoffice-common (>= 1:4.0.2~rc1) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-java-common : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 libreoffice-ogltrans : Depends: libreoffice-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Trying to install libreoffice-common leads nowhere...

---

### Post by N3XU5 on 2013-04-11
Typing apt-get -f install usually takes care of unmet dependecies.

---

### Post by Frogs Hair on 2013-04-11
I am currently showing a partial upgrade available for Libre Office. It is best to _wait_ until all the packages are available before attempting to upgrade. Since you have attempted to purge and disabled the ppa you may have complicated matters. When running PPA released versions of an application this can happen hence the risk of using a PPA. 

See the removal instructions at the link: [http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4](http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4)

---

### Post by jreed72 on 2013-04-11
ty N3XU5 I have tried apt-get -f install to no avail
Frogs Hair, I will check that thread out thanks

---

### Post by jreed72 on 2013-04-11
Well nothing there helped either...
I found a link that suggested I use this: gksudo gedit /var/lib/dpkg/status
and erase all references to LibreOffice, I took it one step further and cleaned anything out from OpenOffice as well so I can start with a clean install.
Seems to be promising so far.

---

### Post by Frogs Hair on 2013-04-11
The rest of the Libre Office updates came through after an hour . The big difference between the PPA and proposed packages and default version is libreoffice-core so I would try to purge that package. 

```
sudo apt-get remove --purge libreoffice-core
``` ```
sudo apt-get autoremove
``````
sudo apt-get update
```

---

### Post by Hagar Delest on 2013-04-14
I've always used the deb version from the official websites instead of the ppa versions and it has never failed.
Use Synaptic to remove any package related to LibreOffice and then install LO and/or AOO from their official site. See: [[Ubuntu] Installing OOo on Debian and Co.](http://forum.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by jreed72 on 2013-04-24
clearing all references in status allowed me to cleanup unmet dependencies

---

