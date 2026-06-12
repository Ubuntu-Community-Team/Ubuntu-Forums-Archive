---
title: "Installing bugzilla on ubuntu server 7.10"
date: 2008-04-09
forum: General Help
---

### Post by mebuntu on 2008-04-09
hi, 

am trying to install bugzilla for the first time on Ubuntu 7.10 but am getting the following output:

root@qrmitst2:/home/ubuntu1# sudo apt-get install bugzilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libnet-ldap-perl libgd-text-perl libgd-graph-perl ruby
The following NEW packages will be installed
  bugzilla
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/832kB of archives.
After unpacking 4542kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package bugzilla.
(Reading database ... 108189 files and directories currently installed.)
Unpacking bugzilla (from .../bugzilla_2.22.1-2.2ubuntu1_all.deb) ...
Setting up bugzilla (2.22.1-2.2ubuntu1) ...
dbconfig-common: writing config to /etc/dbconfig-common/bugzilla.conf
Not replacing deleted config file /etc/bugzilla/dbconfig-params
granting access to database bugzilla for bugzilla@localhost: already exists.
creating database bugzilla: already exists.
dbconfig-common: flushing administrative password
.: 77: Can't open /etc/bugzilla/dbconfig-params
dpkg: error processing bugzilla (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 bugzilla
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@qrmitst2:/home/ubuntu1# 

would appreciate any advice/assistance on this

thanks

---

### Post by xarquid on 2008-04-09
> apt-get -f install

and/or

> apt-get -f install bugzilla

to force an install of the files that didn't get loaded (because of that error you stated above)...this should help resolve most of the issue.

Then try apt-get upgrade again, apt-get -f install back and forth until only the package that has the error is left.

apt-get install bugzilla should work...

Let us know.

xq

---

### Post by mebuntu on 2008-04-10
hi,

thanks for the tips but i ran the cmds you suggested but still getting the same error as before :(

---

