---
title: "unable to update certain files"
date: 2008-04-07
forum: General Help
---

### Post by labud on 2008-04-07
After install of kde desktop re instructions from [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
[just a reference point, not saying kde or install directions were at fault]

I started having problems updating machine
I use  sudo apt-get update which seems to work fine [??]  but then when I use

sudo apt-get install -f    or sudo apt-get -f install     I recieve this in the terminal window:

labud@LGraBow:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdm libsqlite0
Suggested packages:
  menu
The following NEW packages will be installed:
  libsqlite0
The following packages will be upgraded:
  kdm
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
11 not fully installed or removed.
Need to get 0B/845kB of archives.
After unpacking, 446kB of additional disk space will be used.
Do you want to continue [Y/n]? y 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 120741 files and directories currently installed.)
Preparing to replace kdm 4:3.5.8-0ubuntu2 (using .../kdm_4%3a3.5.8-0ubuntu2.2_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/kdm_4%3a3.5.8-0ubuntu2.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Unpacking libsqlite0 (from .../libsqlite0_2.8.17-2.1build1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/libsqlite0_2.8.17-2.1build1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/kdm_4%3a3.5.8-0ubuntu2.2_i386.deb
 /var/cache/apt/archives/libsqlite0_2.8.17-2.1build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


if I go thru synaptic pkg mngr it also gives me problems stating basically the same as above


can anyone tell me what to do to fix this   or point me to a how to fix  ??

thank you

---

### Post by mikewhatever on 2008-04-07
> debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

That error usually comes up when Synaptic/Adept or Add/Remove is open while you are trying to run commands. Make sure they are both closed on all workspaces.

---

