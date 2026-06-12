---
title: "Software center break - how to repair?"
date: 2012-11-09
forum: General Help
---

### Post by eslavko on 2012-11-09
Hello....

I was trying to install avidemux nightly from getdeb.net
But something get wrong and now I have hanging software center.

It's says that I can't instal or uninstall until repair.
If I click repair I got

```

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 395160 files and directories currently installed.) 
Unpacking libavidemux2.6 (from .../libavidemux2.6_1%3a2.6.0-1~getdeb2~quantal_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/libavidemux2.6_1%3a2.6.0-1~getdeb2~quantal_amd64.deb (--unpack): 
 trying to overwrite '/usr/lib/libADM6postproc.so.52', which is also in package avidemux3-core:i386 2.6.0-r8273 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Unpacking avidemux2.6-common (from .../avidemux2.6-common_1%3a2.6.0-1~getdeb2~quantal_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/avidemux2.6-common_1%3a2.6.0-1~getdeb2~quantal_all.deb (--unpack): 
 trying to overwrite '/usr/share/avidemux6/help/QtScript/class_spin_box_control.png', which is also in package avidemux3-plugins-common:i386 2.6.0-8273 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Unpacking avidemux2.6-jobs (from .../avidemux2.6-jobs_1%3a2.6.0-1~getdeb2~quantal_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/avidemux2.6-jobs_1%3a2.6.0-1~getdeb2~quantal_amd64.deb (--unpack): 
 trying to overwrite '/usr/bin/avidemux3_jobs', which is also in package avidemux3-qt4:i386 2.6.0-8273 
Processing triggers for man-db ... 
Processing triggers for hicolor-icon-theme ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/libavidemux2.6_1%3a2.6.0-1~getdeb2~quantal_amd64.deb 
 /var/cache/apt/archives/avidemux2.6-common_1%3a2.6.0-1~getdeb2~quantal_all.deb 
 /var/cache/apt/archives/avidemux2.6-jobs_1%3a2.6.0-1~getdeb2~quantal_amd64.deb 
Error in function:  
dpkg: dependency problems prevent configuration of avidemux2.6: 
 avidemux2.6 depends on libavidemux2.6 (>= 1:2.6.0); however: 
  Package libavidemux2.6 is not installed. 
 avidemux2.6 depends on avidemux2.6-common; however: 
  Package avidemux2.6-common is not installed. 
 avidemux2.6 depends on avidemux2.6-jobs; however: 
  Package avidemux2.6-jobs is not installed. 
dpkg: error processing avidemux2.6 (--configure): 
 dependency problems - leaving unconfigured 

```

how to solve that?

I have 12.04
and folow steps on that page:
[http://www.getdeb.net/updates/ubuntu/12.04/#how_to_install](http://www.getdeb.net/updates/ubuntu/12.04/#how_to_install)
and to install this
[http://www.getdeb.net/software/Avidemux%202.6](http://www.getdeb.net/software/Avidemux%202.6)

thanks

---

### Post by dino99 on 2012-11-09
/var/cache/apt/archives/libavidemux2.6_1%3a2.6.0-1~getdeb2~quantal_amd64.deb (--unpack): 
 trying to overwrite '/usr/lib/libADM6postproc.so.52', which is also in package avidemux3-core:i386 2.6.0-r8273

as it says, you cant have both 2.6 & 3 version

sudo apt-get purge avidemux

---

### Post by eslavko on 2012-11-09
not work

```
slavko@ePodstresnik:~$ sudo apt-get purge avidemux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 avidemux2.6 : Depends: libavidemux2.6 (>= 1:2.6.0) but it is not going to be installed
               Depends: avidemux2.6-common but it is not going to be installed
               Depends: avidemux2.6-jobs but it is not going to be installed
               Recommends: avidemux2.6-plugins-gtk but it is not going to be installed
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
slavko@ePodstresnik:~$ 

```


and sugested one gave me..

```
slavko@ePodstresnik:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  wine-mono0.0.4 wine-gecko1.7 wine-gecko1.7:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  avidemux2.6-common avidemux2.6-jobs libavidemux2.6
The following NEW packages will be installed:
  avidemux2.6-common avidemux2.6-jobs libavidemux2.6
0 upgraded, 3 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0 B/2,928 kB of archives.
After this operation, 8,776 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 395160 files and directories currently installed.)
Unpacking libavidemux2.6 (from .../libavidemux2.6_1%3a2.6.0-1~getdeb2~quantal_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libavidemux2.6_1%3a2.6.0-1~getdeb2~quantal_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libADM6postproc.so.52', which is also in package avidemux3-core:i386 2.6.0-r8273
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking avidemux2.6-common (from .../avidemux2.6-common_1%3a2.6.0-1~getdeb2~quantal_all.deb) ...
dpkg: error processing /var/cache/apt/archives/avidemux2.6-common_1%3a2.6.0-1~getdeb2~quantal_all.deb (--unpack):
 trying to overwrite '/usr/share/avidemux6/help/QtScript/class_spin_box_control.png', which is also in package avidemux3-plugins-common:i386 2.6.0-8273
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking avidemux2.6-jobs (from .../avidemux2.6-jobs_1%3a2.6.0-1~getdeb2~quantal_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/avidemux2.6-jobs_1%3a2.6.0-1~getdeb2~quantal_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/avidemux3_jobs', which is also in package avidemux3-qt4:i386 2.6.0-8273
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/libavidemux2.6_1%3a2.6.0-1~getdeb2~quantal_amd64.deb
 /var/cache/apt/archives/avidemux2.6-common_1%3a2.6.0-1~getdeb2~quantal_all.deb
 /var/cache/apt/archives/avidemux2.6-jobs_1%3a2.6.0-1~getdeb2~quantal_amd64.deb
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Sub-process /usr/bin/dpkg returned an error code (1)
slavko@ePodstresnik:~$

```

---

### Post by eslavko on 2012-11-09
seems that 
```

 sudo apt-get remove avidemux2.6

```

solve the problem



now software center seems working but  sudo apt-get check is not clean!

```
slavko@ePodstresnik:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
slavko@ePodstresnik:~$
```

how to remove that error?

---

