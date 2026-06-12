---
title: "Having issues removing java7 installer"
date: 2013-02-17
forum: General Help
---

### Post by Sethun on 2013-02-17
Okay so I think I downloaded the wrong java, problem is I can't remove the folder located within /var/cache/

I tried doing sudo apt-get remove  oracle-java7-installer and I get this..
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  oracle-java7-installer
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 82.9 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 172627 files and directories currently installed.)
Removing oracle-java7-installer ...
update-alternatives: error: unknown argument `cdrom'
dpkg: error processing oracle-java7-installer (--remove):
 subprocess installed pre-removal script returned error exit status 2
Downloading...
Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by MrKaliman on 2013-02-17
Try the following

Open a terminal (ctrl + alt + T) and type those two commands successively:

```
cd /var/lib/dpkg/info/
```
```
sudo rm oracle-java7-installer*
``````
sudo apt-get purge oracle-java7-installer
```And you should be good.

---

### Post by Sethun on 2013-02-17
> **MrKaliman said:**
> Try the following

Open a terminal (ctrl + alt + T) and type those two commands successively:

```
cd /var/lib/dpkg/info/
``````
sudo rm oracle-java7-installer*
``````
sudo apt-get purge oracle-java7-installer
```And you should be good.

Thank you :)

---

