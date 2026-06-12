---
title: "wont allow me to remove"
date: 2016-06-16
forum: General Help
---

### Post by myron2 on 2016-06-16
hello

im just trying to remove the mongodb but it says a broken pipes even i remove it by purge is there any way to get rid of this? thanks

root@fblinuxserver:~# sudo dpkg -l | grep mongo
ii  mongodb-clients                                1:2.0.4-1ubuntu2.1                  object/document-oriented database (client apps)
ii  mongodb-server                                 1:2.0.4-1ubuntu2.1                  object/document-oriented database (server package)


root@fblinuxserver:~# apt-get --purge remove mongodb-clients
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  mongodb-10gen
The following packages will be REMOVED:
  mongodb-clients* mongodb-server*
The following NEW packages will be installed:
  mongodb-10gen
0 upgraded, 1 newly installed, 2 to remove and 5 not upgraded.
Need to get 0 B/87.4 MB of archives.
After this operation, 171 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 213719 files and directories currently installed.)
Unpacking mongodb-10gen (from .../mongodb-10gen_2.4.14_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/mongodb-10gen_2.4.14_i386.deb (--unpack):
 trying to overwrite '/usr/bin/mongo', which is also in package mongodb-clients 1:2.0.4-1ubuntu2.1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mongodb-10gen_2.4.14_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by X-RED_Tech on 2016-06-16
Why are you in a root shell?
You should be running APT (apt-get) with your normal user and sudo.

---

### Post by Habitual on 2016-06-16
> **X-RED_Tech said:**
> Why are you in a root shell?
You should be running APT (apt-get) with your normal user and sudo.

And this
[quote=][COLOR=#ff0000]root@[/COLOR]fblinuxserver:~# [COLOR=#ff0000]sudo[/COLOR] dpkg -l | grep mongo[/quote]

---

