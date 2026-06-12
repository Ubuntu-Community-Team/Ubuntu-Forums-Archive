---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-01-30
forum: General Help
---

### Post by curtis19 on 2016-01-30
HELP... Cant seem to install anything on my computer because of this error. I think its because I uninstalled Libreoffice.  
When I type sudo apt-get install -f into the terminal I get the following response.
```

curtis@curtis-HP-Pavilion-15-Notebook-PC:~$ sudo apt-get install -f
[sudo] password for curtis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-l10n-en-gb
  libreoffice-l10n-en-za mythes-en-au mythes-en-us ttf-dejavu-extra
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-breeze libreoffice-style-crystal
  libreoffice-style-hicontrast libreoffice-style-human
  libreoffice-style-oxygen libreoffice-style-sifr libreoffice-style-tango
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 276 not upgraded.
10 not fully installed or removed.
Need to get 0 B/22.3 MB of archives.
After this operation, 83.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 317495 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a5.0.4~rc2-0ubuntu1~trusty1_all.deb ...
Unpacking libreoffice-common (1:5.0.4~rc2-0ubuntu1~trusty1) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a5.0.4~rc2-0ubuntu1~trusty1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.1-9775
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/prereg/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/program/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a5.0.4~rc2-0ubuntu1~trusty1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

