---
title: "Adept broken"
date: 2007-10-14
forum: General Help
---

### Post by chambliss on 2007-10-14
Hi All,

I have Kubuntu installed.  When the adept icon goes off in the taskbar, I would religiously update my box.  About a month or so ago, these updates started throwing an error message:

There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 


What's the best way to trouble shoot this problem?  The current update that is hanging is hplip.  I can't capture Adept's error messages so here is the console version:

duser@mineboxen:~$ sudo apt-get install hplip
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  openoffice.org-filter-mobiledev libwps-0.1-1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  hpijs-ppds hplip-doc
Recommended packages:
  hpijs python-reportlab
The following packages will be upgraded:
  hplip
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/621kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 157942 files and directories currently installed.)
Preparing to replace hplip 1.7.3-0ubuntu1 (using .../hplip_1.7.3-0ubuntu1.1_i386.deb) ...
usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/hplip.dirs does not exist
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/hplip.dirs does not exist
dpkg: error processing /var/cache/apt/archives/hplip_1.7.3-0ubuntu1.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
 * Starting HP Linux Printing and Imaging System                                                                                                               [fail] 
invoke-rc.d: initscript hplip, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/hplip_1.7.3-0ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



Any ideas??

---

### Post by zvacet on 2007-10-14
```
sudo dpkg -f install
```

---

### Post by chambliss on 2007-10-14
duser@mineboxen:~$ sudo dpkg -f install
dpkg-deb: failed to read archive `install': No such file or directory


duser@mineboxen:~$ sudo dpkg -f install hplip
dpkg-deb: failed to read archive `install': No such file or directory


duser@mineboxen:~$ sudo dpkg -f hplip
dpkg-deb: failed to read archive `hplip': No such file or directory


duser@mineboxen:~$ sudo dpkg --force-downgrade hplip
dpkg: need an action option



??? Jeez, dpkg help is ridiculous.  Any other ideas to try??

---

### Post by ThrobbingBrain66 on 2007-10-14
I think he meant:
```
sudo apt-get install -f
```

Alternatively, you can try:
```
sudo dpkg --configure -a
```

---

### Post by Pumalite on 2007-10-14
Id nothing else works, try this:

sudo dpkg -i --force-overwrite /var/cache/apt/archives/<packagename>

---

