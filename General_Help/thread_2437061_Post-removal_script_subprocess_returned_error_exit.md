---
title: "Post-removal script subprocess returned error exits status 1"
date: 2020-02-18
forum: General Help
---

### Post by skoles on 2020-02-18
Installed CQRlog from the Ubuntu Software options and had issues with it. :( I went to uninstall using Ubuntu Software and this issue developed. It has locked up my ability to use Ubuntu Software to install other software.

How I do I "CLEAN UP" the botched uninstall so that Ubuntu Software is happy again ?

---

### Post by Impavidus on 2020-02-18
Let's first try and see if we can get a meaningful error message. Try these commands and show us the full output:```
sudo apt update
sudo apt install -f
```Also, which release of Ubuntu do you use?

---

### Post by skoles on 2020-02-18
Hello ! Thanks for the reply

```
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic
```

```
wx3k@wx3k-Inspiron-3670:~$ sudo apt update
[sudo] password for wx3k: 
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Fetched 163 kB in 1s (234 kB/s)                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
31 packages can be upgraded. Run 'apt list --upgradable' to see them.
wx3k@wx3k-Inspiron-3670:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-geocodeglib-1.0 libllvm8 ubuntu-web-launchers
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  cqrlog
0 upgraded, 0 newly installed, 1 to remove and 31 not upgraded.
1 not fully installed or removed.
After this operation, 29.0 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 162984 files and directories currently installed.)
Removing cqrlog (2.0.5-3ubuntu1) ...
dpkg: error processing package cqrlog (--remove):
 installed cqrlog package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 cqrlog
E: Sub-process /usr/bin/dpkg returned an error code (1)
```




> **Impavidus said:**
> Let's first try and see if we can get a meaningful error message. Try these commands and show us the full output:```
sudo apt update
sudo apt install -f
```Also, which release of Ubuntu do you use?

---

### Post by Impavidus on 2020-02-19
That error message is not very helpful.

Sometimes reinstalling a package helps. At least it should put the package manager back into a consistent state and allow you to install upgrades and other things, but with a bit of luck it also fixes whatever causes this post-removal script to return 1.
```
sudo apt update
sudo apt install --reinstall cqrlog
sudo apt upgrade
sudo apt remove cqrlog
```

---

### Post by skoles on 2020-02-27
ok, no problem....Did find a solution in removing the half-install

sudo vi /var/lib/dpkg/status
sudo apt-get update

---

