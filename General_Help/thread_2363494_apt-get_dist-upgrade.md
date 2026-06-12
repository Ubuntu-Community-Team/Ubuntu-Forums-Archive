---
title: "apt-get dist-upgrade"
date: 2017-06-10
forum: General Help
---

### Post by aminbaik on 2017-06-10
Hello,
I try to update my packges after I excute apt-get dist I get this result:
```
sudo apt-get dist-upgrade
[sudo] password for aminbaik:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libaio1 libdbd-mysql-perl libdbi-perl libterm-readkey-perl
  mariadb-server-core-5.5
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  mariadb-client-5.5 mariadb-client-core-5.5 mariadb-server mariadb-server-5.5
The following NEW packages will be installed
  apache2-utils liblua5.2-0 libnghttp2-14
The following packages will be upgraded:
  apache2 apache2-bin apache2-data
3 to upgrade, 3 to newly install, 4 to remove and 0 not to upgrade.

```
I notes that it' will be remove  
```
mariadb-client-5.5 mariadb-client-core-5.5 mariadb-server mariadb-server-5.5
```
so any problem to do that ?
also is there any problem to Run ```
'do-release-upgrade' 
```to upgrade my system ?
thank.s

---

### Post by deadflowr on 2017-06-10
When it lists packages that will be removed, it's usually the case that you have already removed some package(s) that those packages were installed with and therefor the system now believes that those other packages are also not needed anymore.

> also is there any problem to Run

```
'do-release-upgrade'
```
to upgrade my system ?

No problems normally, unless there is something wrong with the system already.

---

### Post by aminbaik on 2017-06-11
Hello,
but in my case  the process will remove the maria-db component ! and I managed my msqldb in it ! so how that will be happen ?
thanks.

---

### Post by vasa1 on 2017-06-11
If you use the command line for installing and removing packages,```
grep -i "apt-get" .bash_history | tail -25
```may give us a hint of what you've done previously.

---

### Post by Impavidus on 2017-06-11
You have 3 apache packages that can be upgraded. The dependencies of those packages changed, so if you upgrade them, you have to install the 3 new dependencies. But either the new versions of the apache packages or their new dependencies conflict with the 4 mariadb packages, so you would have to remove those.

This is a rather uncommon situation. You rarely have to remove packages for an upgrade. Which version of Ubuntu do you run? Have you installed any PPAs? Whith those this may happen more often.

do-release-upgrade should be relatively safe, but is something completely different. It should upgrade your system to the next release of Ubuntu and may uninstall some packages in the process.

---

