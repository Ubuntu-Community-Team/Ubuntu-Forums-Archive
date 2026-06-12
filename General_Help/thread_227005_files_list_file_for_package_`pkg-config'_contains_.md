---
title: "files list file for package `pkg-config' contains empty filename??"
date: 2006-08-01
forum: General Help
---

### Post by MachNine on 2006-08-01
well as you can see i got some problems..

I can't install anything anymore not through synaptic nor terminal with apt-get..

this is the faulty code i get when i try to install with apt-get in terminal : 

machnine@machnine-desktop:~$ apt-get install kwin-baghira
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
machnine@machnine-desktop:~$ su
Password:
root@machnine-desktop:/home/machnine# apt-get install kwin-baghira
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  kwin-baghira
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 658kB of archives.
After unpacking 1892kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe kwin-baghira 0.7a-1build2 [658kB]
Fetched 658kB in 4s (137kB/s)
Selecting previously deselected package kwin-baghira.
(Reading database ... dpkg: error processing /var/cache/apt/archives/kwin-baghira_0.7a-1build2_i386.deb (--unpack):
files list file for package `pkg-config' contains empty filename
Errors were encountered while processing:
/var/cache/apt/archives/kwin-baghira_0.7a-1build2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@machnine-desktop:/home/machnine# apt-get install dpkg
Reading package lists... Done
Building dependency tree... Done
dpkg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.

And just to show my pkg-config.list file looks like this.

/.
/usr
/usr/lib
/usr/lib/pkgconfig
/usr/share
/usr/share/pkgconfig
/usr/share/aclocal
/usr/share/aclocal/pkg.m4
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/pkg-config.1.gz
/usr/share/doc
/usr/share/doc/pkg-config
/usr/share/doc/pkg-config/README
/usr/share/doc/pkg-config/AUTHORS
/usr/share/doc/pkg-config/copyright
/usr/share/doc/pkg-config/changelog.gz
/usr/share/doc/pkg-config/NEWS.gz
/usr/share/doc/pkg-config/changelog.Debian.gz
/usr/bin

Anyone that has a clue of whats going on? :S cause i don't and i don't want to reinstall ubuntu again and loose all my stuff on the harddrive :(

---

### Post by happynix on 2006-08-08
THIS is not a proper solution!
 Definately a "IHSPATWFM" (I had the same problem and this worked for me"

I moved the files in /var/lob/dpkg/info/<empty filename reference>

I was then able to do an apt-get install.
I reinstalled the <empty filename reference package> just to try to set everything right.

---

