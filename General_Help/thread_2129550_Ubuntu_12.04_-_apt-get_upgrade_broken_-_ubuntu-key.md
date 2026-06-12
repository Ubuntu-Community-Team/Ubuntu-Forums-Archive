---
title: "Ubuntu 12.04 - apt-get upgrade broken - ubuntu-keyring package"
date: 2013-03-26
forum: General Help
---

### Post by bonuswhore on 2013-03-26
This has now broken 3 separate Ubuntu 12.04 installations I maintain:



apt-get update, then apt-get upgrade


it tries to upgrade 'apt' as part of the apt-get upgrade and this happens every time:

> Fetched 333 MB in 3min 2s (1,829 kB/s)                                                   
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up apt (0.8.16~exp12ubuntu10.10) ...
ERROR: Can't find the archive-keyring
Is the ubuntu-keyring package installed?
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)




from then on, you can no longer apt-get install or apt-get upgrade or do any actions.

---

### Post by bonuswhore on 2013-03-26
tried the following things with no luck :



# apt-get -f install ubuntu-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 219 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up apt (0.8.16~exp12ubuntu10.10) ...
ERROR: Can't find the archive-keyring
Is the ubuntu-keyring package installed?
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)



# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 219 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up apt (0.8.16~exp12ubuntu10.10) ...
ERROR: Can't find the archive-keyring
Is the ubuntu-keyring package installed?
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)


these all fail too with same problem -

apt-get -m upgrade

apt-get -f upgrade

apt-get dist-upgrade

---

### Post by bonuswhore on 2013-03-26
#     sudo dpkg --configure -a
Setting up apt (0.8.16~exp12ubuntu10.10) ...
ERROR: Can't find the archive-keyring
Is the ubuntu-keyring package installed?
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 apt


#     apt-cache policy ubuntu-keyring
ubuntu-keyring:
  Installed: 2011.11.21.1
  Candidate: 2011.11.21.1
  Version table:
 *** 2011.11.21.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2011.11.21 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages



#     sudo apt-get -f install ubuntu-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-keyring is already the newest version.
The following package was automatically installed and is no longer required:
  libgnome2-gconf-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 130 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up apt (0.8.16~exp12ubuntu10.10) ...
ERROR: Can't find the archive-keyring
Is the ubuntu-keyring package installed?
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libperl5.14 (5.14.2-6ubuntu2.3) ...
Setting up perl-modules (5.14.2-6ubuntu2.3) ...
Setting up perl (5.14.2-6ubuntu2.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bonuswhore on 2013-03-26
#     ls -l /usr/share/keyrings
total 4
-rw-r--r-- 1 root root 1265 Mar 25 10:25 sur5r-keyring.gpg




I'm guessing I'm mising files there, I know I did not delete them and they've gone missing on 3 different installations.  not sure what is causing this to occur.  will I be able to copy the files over from any old ubuntu install to fix that?





*edit*

copied the keys from /usr/share/keyrings/  from a fresh install to the boxes and that fixed apt.   Wish I knew what was deleting these keys or why this is happening but hopefully this will help anyone else seeing these problems

---

