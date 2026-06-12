---
title: "auditd - update-rc.d: warning: start and stop actions are no longer supported"
date: 2016-11-26
forum: General Help
---

### Post by niraj_vara on 2016-11-26
Hi

I  have the docker image for ubuntu:16.04 and ubuntu:16.10. In Both when I am trying to install the auditd I getting the following error.

update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
invoke-rc.d: could not determine current runlevel
invoke-rc.d: policy-rc.d denied execution of start.

what could be the reason for this error.

---

### Post by cariboo on 2016-11-26
Ubuntu doesn't use upstart any more, to see if auditd is running, run the following command:

```
sudo systemctl status auditd.service
```

---

### Post by niraj_vara on 2016-11-26
Hi

during installation I am getting this error.

 root@8a135f3b1d8e:/# apt-get install auditdReading package lists... Done
Building dependency tree... Done
The following additional packages will be installed:
  libauparse0
Suggested packages:
  audispd-plugins
The following NEW packages will be installed:
  auditd libauparse0
0 upgraded, 2 newly installed, 0 to remove and 21 not upgraded.
Need to get 224 kB of archives.
After this operation, 753 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety/main amd64 libauparse0 amd64 1:2.6.6-1ubuntu1 [38.6 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety/main amd64 auditd amd64 1:2.6.6-1ubuntu1 [186 kB]
Fetched 224 kB in 0s (409 kB/s)
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package libauparse0:amd64.
(Reading database ... 6501 files and directories currently installed.)
Preparing to unpack .../0-libauparse0_1%3a2.6.6-1ubuntu1_amd64.deb ...
Unpacking libauparse0:amd64 (1:2.6.6-1ubuntu1) ...
Selecting previously unselected package auditd.
Preparing to unpack .../1-auditd_1%3a2.6.6-1ubuntu1_amd64.deb ...
Unpacking auditd (1:2.6.6-1ubuntu1) ...
Setting up libauparse0:amd64 (1:2.6.6-1ubuntu1) ...
Setting up auditd (1:2.6.6-1ubuntu1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
invoke-rc.d: could not determine current runlevel
invoke-rc.d: policy-rc.d denied execution of start.
Processing triggers for libc-bin (2.24-0ubuntu1) ...

---

