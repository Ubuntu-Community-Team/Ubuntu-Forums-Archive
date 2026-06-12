---
title: "Broken packages on shimmer-themes"
date: 2014-08-15
forum: General Help
---

### Post by 13l-jason on 2014-08-15
Ran into this problem trying to install xubuntu-desktop into my 14.04 installation.  

I've tried the following commands, but keep going in circles.  Is there a manual method for fixing this?
sudo dpkg --configure -a
sudo apt-get -f install

Thanks in advance.

```
mtx@tds:~$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  shimmer-themes
Suggested packages:
  shimmer-wallpapers
The following NEW packages will be installed:
  shimmer-themes
0 upgraded, 1 newly installed, 0 to remove and 218 not upgraded.
3 not fully installed or removed.
Need to get 187 kB of archives.
After this operation, 2,202 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe shimmer-themes all 1.7.3-0ubuntu1 [187 kB]
Fetched 187 kB in 0s (400 kB/s)        
(Reading database ... 442669 files and directories currently installed.)
Preparing to unpack .../shimmer-themes_1.7.3-0ubuntu1_all.deb ...
Unpacking shimmer-themes (1.7.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/shimmer-themes_1.7.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/themes/Orion/gtk-3.0/settings.ini', which is also in package orion-gtk-theme 2013.01.19-0~satya164~quantal
Errors were encountered while processing:
 /var/cache/apt/archives/shimmer-themes_1.7.3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ubudog on 2014-08-15
From [https://bugs.launchpad.net/ubuntu/+source/shimmer-themes/+bug/1243753]("https://bugs.launchpad.net/ubuntu/+source/shimmer-themes/+bug/1243753"), it looks like a conflict between the official repo and a PPA you have installed.

---

### Post by 13l-jason on 2014-08-17
Thanks for the reply.  it helped.  Thought I'd gotten rid of that PPA.  Thanks

---

