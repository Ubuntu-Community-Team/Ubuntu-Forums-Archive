---
title: "Error after installing r-studio (Ubuntu 16.04.3)"
date: 2018-01-26
forum: General Help
---

### Post by Ziad_Arafat on 2018-01-26
Ubuntu 16.04 64-bit

I actually don't know if r-studio is the cause. 

```
sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Setting up python-configargparse (0.10.0-2) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ModuleNotFoundError: No module named 'ConfigParser'
dpkg: error processing package python-configargparse (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-configparser (3.3.0r2-2) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ModuleNotFoundError: No module named 'ConfigParser'
dpkg: error processing package python-configparser (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-markupsafe (0.23-2build2) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ModuleNotFoundError: No module named 'ConfigParser'
dpkg: error processing package python-markupsafe (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-scour (0.32-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ModuleNotFoundError: No module named 'ConfigParser'
dpkg: error processing package python-scour (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 python-configargparse
 python-configparser
 python-markupsafe
 python-scour
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by mörgæs on 2018-01-27
Does the output from ```
sudo apt update
``` give an indication to what is wrong?

---

### Post by Ziad_Arafat on 2018-02-05
> **mörgæs said:**
> Does the output from ```
sudo apt update
``` give an indication to what is wrong?
No 

```
cat@cat-Desktop:~$ sudo apt update
Hit:1 http://cran.rstudio.com/bin/linux/ubuntu xenial/ InRelease
Hit:2 http://linux-packages.resilio.com/resilio-sync/deb resilio-sync InRelease                                                                                                                        
Hit:3 http://packages.microsoft.com/repos/vscode stable InRelease                                                                                                                                      
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                                           
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial InRelease                                                                                                                                            
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                                                                                      
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                                                                          
Hit:8 http://dl.google.com/linux/chrome/deb stable Release                                                                                                      
Hit:9 http://archive.canonical.com/ubuntu xenial InRelease                                                                                                      
Hit:10 http://ppa.launchpad.net/octave/stable/ubuntu xenial InRelease                                                                      
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                                       
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [62.6 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [307 kB]            
Get:15 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [71.2 kB]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [51.3 kB]
Get:17 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [80.2 kB]                 
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [219 kB]                     
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [190 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [267 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,892 B]
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Get:23 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [4,696 B]
Fetched 1,570 kB in 1s (805 kB/s)                                            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.


```

---

### Post by Ziad_Arafat on 2018-02-05
Just to be sure did I post this in the right topic? Or is this section only for installing and upgrading to newer ubuntu releases?

---

### Post by QIII on 2018-02-05
^^ This.  ;)

Moved to General Help.

---

### Post by Ziad_Arafat on 2018-02-06
I've tried everything and it just got worse. More and more python errors kept showing up. Just gonna reinstall now :confused:

---

### Post by Ziad_Arafat on 2018-02-06
I submitted bug reports through the popups that appeared when the errors show up. I hope that helps.

---

### Post by mörgæs on 2018-02-06
If you reinstall I suggest that you begin with R and R-Studio. When that works you can add Python.

---

