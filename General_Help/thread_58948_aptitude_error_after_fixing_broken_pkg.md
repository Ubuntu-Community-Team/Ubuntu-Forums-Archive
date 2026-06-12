---
title: "aptitude error after fixing broken pkg"
date: 2005-08-22
forum: General Help
---

### Post by auburn on 2005-08-22
I installed screem yesturday and had trouble with dependencies with libgtkhtml2-0. I then went to synaptic and told it to repair it and now I get errors processing  libbonobo2-common everytime I try to aptitude upgrade. How can I fix this?

$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
The following packages will be upgraded:
  php4 php4-common
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/168kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/php4-common_4%3a4.3.10-10ubuntu4.1_i386.deb (--unpack):
 unable to open files list file for package `libbonobo2-common': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/php4-common_4%3a4.3.10-10ubuntu4.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack!  Something bad happened while installing packages.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done

---

### Post by heimo on 2005-08-22
This is unconfirmed and may cause even more problems. And this is what I'd do:
 ```

sudo rm /var/cache/apt/archives/php4-common_4%3a4.3.10-10ubuntu4.1_i386.deb
sudo rm /var/lib/dpkg/info/php4-common*
sudo apt-get --purge remove php4-common
sudo apt-get update

```

---

### Post by auburn on 2005-08-22
Thanks for your help.

so, I think what you're suggesting is to physically delete (rm) offending items until the problems are all gone and apt-get can act normally. Well, trying to apt-get remove php4-common (even after I've deleted it) tells me I can't because phpldapadmin seems to be in the way (below). Should I just continue physically deleting the items listed under "The following packages will be REMOVED"? And Then apt-get remove the same files? I'm not actually using php at the moment so I'm not destroying important anything...yet.

$ sudo apt-get --purge remove php4-common
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  libapache-mod-php4* php4* php4-common* php4-ldap* php4-mysql*
  php4-universe-common* phpldapadmin*
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 5784kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `php4-universe-common' missing, assuming package has no files currently installed.
dpkg: error processing phpldapadmin (--purge):
 unable to open files list file for package `libbonobo2-common': Input/output error
Errors were encountered while processing:
 phpldapadmin
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by heimo on 2005-08-22
Those php4 packages are safe to remove (take backups of config files that you've edited if removing with --purge) and you can always reinstall them. But libbonobo for instance, may mess up something on X (*me thinks*) and it seems your dpkg database is badly corrupted, hopefully it's not more than those packages listed on your post above. If it's worse, some other approach may be needed.

---

