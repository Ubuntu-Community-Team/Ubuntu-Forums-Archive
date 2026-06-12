---
title: "From breezy to edgy isn't so easy. Apt issues."
date: 2006-10-26
forum: General Help
---

### Post by jon_k on 2006-10-26
Well,

I decided to take the plunge and I've plunged to my death. Any ideas on how to push apt through this issue?

I updated my sources.list to edgy from breezy and the upgrade got hung up (complained nice values must be between -20 to 9, well duh!) so I kept clicking OK OK OK to the debconf saying this. Seems it was in a loop, so I hit cancel which cancelled apts work.

Decided to resume by doing apt-get -f install; but it hangs up now. Any ideas on how to get the upgrade to resume? Seems like from Breezy to Edgy was a bad idea.

root@prole:/etc/apt# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  volumeid
The following NEW packages will be installed:
  volumeid
0 upgraded, 1 newly installed, 0 to remove and 1179 not upgraded.
26 not fully installed or removed.
Need to get 0B/61.4kB of archives.
After unpacking 111kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Sess[B]ion management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
[/B]
Preconfiguring packages ...
(Reading database ... 117896 files and directories currently installed.)
Unpacking volumeid (from .../volumeid_093-0ubuntu18_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/volumeid_093-0ubuntu18_i386.deb (--unpack):
 trying to overwrite `/sbin/vol_id', which is also in package udev
Errors were encountered while processing:
 /var/cache/apt/archives/volumeid_093-0ubuntu18_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@prole:/etc/apt#

---

### Post by PriceChild on 2006-10-26
All of the documentation on upgrading... you will be told that upgrading from versions must be done in increments.

You have to upgrade from breezy to dapper to edgy.

---

