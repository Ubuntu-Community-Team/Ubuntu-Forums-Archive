---
title: "Errors with apt-get etc"
date: 2013-06-27
forum: General Help
---

### Post by JaySeeJC on 2013-06-27
I've recently started getting errors while trying to install things via the package manager...

```
root@clara:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
Setting up man-db (2.6.3-3) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up gdm (3.6.1-0ubuntu4) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing gdm (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gdm (>= 3.5.90); however:
  Package gdm is not configured yet.


dpkg: error processing gnome-shell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on gdm (>= 3.4); however:
  Package gdm is not configured yet.
 gnome-core depends on gnome-shell (>= 3.4); however:
  Package gnome-shell is not configured yet.


dpkg: error processing gnome-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-shell-extensions:
 gnome-shell-extensions depends on gnome-shell (>= 3.6); however:
  Package gnome-shell is not configured yet.
 gnome-shell-extensions depends on gnome-shell (<< 3.7); however:
  Package gnome-shell is not configured yet.


dNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                           No apport report written because MaxReports is reached already
                                                                                                                                                                         No apport report written because MaxReports is reached already
                                     pkg: error processing gnome-shell-extensions (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 man-db
 gdm
 gnome-shell
 gnome-core
 gnome-shell-extensions
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

I'm absolutely clueless as to what's causing this. Any help would be much appreciated.

---

### Post by Bucky Ball on 2013-06-27
Try these three, one at a time. Ignore error messages.

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade

```
What did that spit out?

---

### Post by JaySeeJC on 2013-06-27
Fixed the problem. Reinstalling debconf worked for me.
[COLOR=#CCCCCC][FONT=verdana] 'apt-get --reinstall install debconf'[/FONT][/COLOR]

---

### Post by Bucky Ball on 2013-06-27
Good news. Please help others and mark thread as solved by following the link in my signature.

PS: Run those commands anyhow. Won't hurt and will freshen up the system (the upgrade command doesn't upgrade the release, just packages in it that have a newer version in the repos - if there are upgrades it asks if you want them first). ;)

---

### Post by fantab on 2013-06-27
Deleted. As the OP fixed the problem.

---

