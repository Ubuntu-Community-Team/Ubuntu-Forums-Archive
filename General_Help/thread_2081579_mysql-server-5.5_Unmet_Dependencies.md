---
title: "mysql-server-5.5: Unmet Dependencies"
date: 2012-11-07
forum: General Help
---

### Post by markcs on 2012-11-07
Hi All,

I can't seem to fix the mysql error I am getting, even after reading some of the other threads.

The error I am getting is:

You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mysql-server-5.5 : Depends: mysql-server-core-5.5 (= 5.5.24-0ubuntu0.12.04.1) but 5.5.28-0ubuntu0.12.04.2 is installed
E: Unmet dependencies. Try using -f.

When I try apt-get -f install, I get this error:

dpkg: dependency problems prevent configuration of mysql-server-5.5:
 mysql-server-5.5 depends on mysql-server-core-5.5 (= 5.5.24-0ubuntu0.12.04.1); however:
  Version of mysql-server-core-5.5 on system is 5.5.28-0ubuntu0.12.04.2.
dpkg: error processing mysql-server-5.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                    Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server

And if I try to remove mysql with the purge command, I get the following error as I have MythTV installed, which relies on mysql.  

mark@mythtv:/etc/apt$ sudo apt-get purge mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mysql-server-5.5 : Depends: mysql-server-core-5.5 (= 5.5.24-0ubuntu0.12.04.1) but 5.5.28-0ubuntu0.12.04.2 is to be installed
 mythtv : Depends: mysql-server
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I don't really want to remove MythTV which could remove all the settings....

Any help appreciated.

---

### Post by bl4z on 2012-11-17
go to this folder

root@ext:/var/cache/apt/archives#

and try this dpkg --force-depends -i mysql-server-5.5_5.5.28-0ubuntu0.12.04.2_amd64.deb 

(change the arch details of package; mine is amd64)

and it was fixed 

--output of command

(Reading database ... 155738 files and directories currently installed.)
Preparing to replace mysql-server-5.5 5.5.24-0ubuntu0.12.04.1 (using mysql-server-5.5_5.5.28-0ubuntu0.12.04.2_amd64.deb) ...
mysql stop/waiting
Unpacking replacement mysql-server-5.5 ...
Setting up mysql-server-5.5 (5.5.28-0ubuntu0.12.04.2) ...
mysql start/running, process 3363
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
root@ext:/var/cache/apt/archives# apt-get upgrade
Do you want to continue [Y/n]? 
Setting up mysql-server (5.5.28-0ubuntu0.12.04.2) ...

---

### Post by Jesse Degger on 2012-11-17
I get this output with the exact same problem:

```
# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mysql-server-5.5
Suggested packages:
  tinyca mailx
The following packages will be upgraded:
  mysql-server-5.5
1 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
1 not fully installed or removed.
Need to get 0 B/8,820 kB of archives.
After this operation, 13.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: dependency problems prevent configuration of mysql-server-5.5:
 mysql-server-5.5 depends on mysql-server-core-5.5 (= 5.5.24-0ubuntu0.12.04.1); however:
  Version of mysql-server-core-5.5 on system is 5.5.28-0ubuntu0.12.04.2.
dpkg: error processing mysql-server-5.5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 mysql-server-5.5
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I do not really understand how the solution of bl4z works. Could you please give some additional information?

Also, I figured my /boot partition is full, I can't delete old linux kernels because of this error.

---

