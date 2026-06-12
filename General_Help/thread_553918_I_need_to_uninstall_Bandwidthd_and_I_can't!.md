---
title: "I need to uninstall Bandwidthd and I can't!"
date: 2007-09-18
forum: General Help
---

### Post by madelman on 2007-09-18
I cannot install and cannot uninstall. I tried to install SARGE-bandwidthd_2.0.1_i386.deb 
And also download bandwidthd-2.0.1.tgz from their website and same results. 
I had to copy bandwidthd.conf to /usr/share/doc/bandwidthd/ because it was giving errors while installing and that did not help. I need to remove this program that does not work in 7.04
 
So I tried as follows: 
 
sudo apt-get -f install 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
The following extra packages will be installed: 
bandwidthd 
The following packages will be upgraded: 
bandwidthd 
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
1 not fully installed or removed. 
Need to get 0B/65.2kB of archives. 
After unpacking 36.9kB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Preconfiguring packages ... 
Selecting previously deselected package bandwidthd. 
(Reading database ... 127298 files and directories currently installed.) 
Preparing to replace bandwidthd 2.0.1 (using .../bandwidthd_2.0.1+cvs20050208-11_i386.deb) ... 
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected 
invoke-rc.d: initscript bandwidthd, action "stop" failed. 
dpkg: warning - old pre-removal script returned error exit status 2 
dpkg - trying script from the new package instead ... 
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected 
invoke-rc.d: initscript bandwidthd, action "stop" failed. 
dpkg: error processing /var/cache/apt/archives/bandwidthd_2.0.1+cvs20050208-11_i386.deb (--unpack): 
subprocess new pre-removal script returned error exit status 2 
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected 
invoke-rc.d: initscript bandwidthd, action "start" failed. 
dpkg: error while cleaning up: 
subprocess post-installation script returned error exit status 2 
Errors were encountered while processing: 
/var/cache/apt/archives/bandwidthd_2.0.1+cvs20050208-11_i386.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
 
================================= 
sudo dpkg -r bandwidthd 
dpkg: error processing bandwidthd (--remove): 
Package is in a very bad inconsistent state - you should 
reinstall it before attempting a removal. 
Errors were encountered while processing: 
bandwidthd 
 
=========================== 
sudo apt-get remove bandwidthd 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
The following packages will be REMOVED: 
bandwidthd 
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded. 
1 not fully installed or removed. 
Need to get 0B of archives. 
After unpacking 201kB disk space will be freed. 
Do you want to continue [Y/n]? y 
dpkg: error processing bandwidthd (--remove): 
Package is in a very bad inconsistent state - you should 
reinstall it before attempting a removal. 
Errors were encountered while processing: 
bandwidthd 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
 
Trying to the update manager, since I have an alert to update Bandwidthd it says: 
 
E: /var/cache/apt/archives/bandwidthd_2.0.1+cvs20050208-11_i386.deb: subprocess new pre-removal script returned error exit status 2 
 
I cannot update, install or remove this package. It is just there.

---

### Post by awir_bio on 2008-01-26
same with me........can somebody help us..please........my operation system is ubuntu 7.10. and it not working too....


sudo apt-get remove bandwidthd 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgd2-noxpm
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bandwidthd
0 upgraded, 0 newly installed, 1 to remove and 108 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 201kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing bandwidthd (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd
E: Sub-process /usr/bin/dpkg returned an error code (1)


please...somebody help us...

---

### Post by sridhar85 on 2008-02-04
I have the same problem.. Pls help..

---

### Post by sridhar85 on 2008-02-08
This worked for me.. I got this from
[http://ubuntuforums.org/showthread.php?t=12737](http://ubuntuforums.org/showthread.php?t=12737)

Here's what I did:
1. Edit the file /var/lib/dpkg/status , look for the listing for the broken package, remove the info for that package. Here search bandwidthd package and then remove all details under it.
2. mv /var/lib/dpkg/info /var/lib/dpkg/info_old
3. mkdir /var/lib/dpkg/info
4. apt-get update, apt-get -f install
5. mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
6. rm -f /var/lib/dpkg/info
7. mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info

---

