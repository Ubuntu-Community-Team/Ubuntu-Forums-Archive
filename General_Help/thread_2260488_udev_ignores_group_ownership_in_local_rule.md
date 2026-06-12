---
title: "udev ignores group ownership in local rule"
date: 2015-01-12
forum: General Help
---

### Post by kao on 2015-01-12
Hi all,
I would like removable drives to mount  to shared /media directory and change group to common group of my family.
So i've written following rule to /etc/udev/rules.d/local.rules
ENV{ID_FS_USAGE}=="filesystem", ENV{UDISKS_FILESYSTEM_SHARED}="1", GROUP="klmk"

Rule worked flawlessly some time ago before upgrading to 14.10. But I've found out that it works only partially now.
It uses ENV{UDISKS_FILESYSTEM_SHARED}="1", but ignores GROUP="klmk" and removable drives are mounted with primary group of my own

I've attached udevadm monitor output [ATTACH]259191[/ATTACH]

May anybody have already encountered similiar problem?

Thank you
lsb_release -rd
Description:	Ubuntu 14.10
Release:	14.10

apt-cache policy udev
udev:
  Installed: 208-8ubuntu8.2
  Candidate: 208-8ubuntu8.2

---

