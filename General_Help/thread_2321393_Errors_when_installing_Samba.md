---
title: "Errors when installing Samba"
date: 2016-04-22
forum: General Help
---

### Post by SuperFreak on 2016-04-22
I am getting errors when installing Samba. I think this might go back to an incomplete installation of a package that I fixed by editing out the offending package in /var/lib/dpkg/status as shown [HERE]("http://askubuntu.com/questions/122699/how-to-remove-package-in-bad-state-software-center-freezes-no-synaptic"). I am using 16.04 64 Bit

```
sudo apt-get install samba
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  attr libaio1 python-crypto python-dnspython python-ldb
  python-samba python-tdb samba-common samba-common-bin
  samba-dsdb-modules samba-vfs-modules tdb-tools
Suggested packages:
  python-crypto-dbg python-crypto-doc bind9 bind9utils
  ctdb ldb-tools ntp smbldap-tools winbind
  heimdal-clients
The following NEW packages will be installed:
  attr libaio1 python-crypto python-dnspython python-ldb
  python-samba python-tdb samba samba-common
  samba-common-bin samba-dsdb-modules samba-vfs-modules
  tdb-tools
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 3,437 kB of archives.
After this operation, 25.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 python-dnspython all 1.12.0-1 [85.2 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 python-crypto amd64 2.6.1-6build1 [245 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 python-ldb amd64 2:1.1.24-1ubuntu3 [29.3 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 python-tdb amd64 1.3.8-2 [11.1 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 python-samba amd64 2:4.3.8+dfsg-0ubuntu1 [1,058 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 samba-common all 2:4.3.8+dfsg-0ubuntu1 [81.0 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 samba-common-bin amd64 2:4.3.8+dfsg-0ubuntu1 [505 kB]
Get:8 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 tdb-tools amd64 1.3.8-2 [21.0 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 samba amd64 2:4.3.8+dfsg-0ubuntu1 [900 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 attr amd64 1:2.4.47-2 [25.5 kB]
Get:11 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 libaio1 amd64 0.3.110-2 [6,356 B]
Get:12 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 samba-dsdb-modules amd64 2:4.3.8+dfsg-0ubuntu1 [216 kB]
Get:13 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 samba-vfs-modules amd64 2:4.3.8+dfsg-0ubuntu1 [255 kB]
Fetched 3,437 kB in 5s (598 kB/s)           
Preconfiguring packages ...
Selecting previously unselected package python-dnspython.
(Reading database ... 193607 files and directories currently installed.)
Preparing to unpack .../python-dnspython_1.12.0-1_all.deb ...
Unpacking python-dnspython (1.12.0-1) ...
Selecting previously unselected package python-crypto.
Preparing to unpack .../python-crypto_2.6.1-6build1_amd64.deb ...
Unpacking python-crypto (2.6.1-6build1) ...
Selecting previously unselected package python-ldb.
Preparing to unpack .../python-ldb_2%3a1.1.24-1ubuntu3_amd64.deb ...
Unpacking python-ldb (2:1.1.24-1ubuntu3) ...
Selecting previously unselected package python-tdb.
Preparing to unpack .../python-tdb_1.3.8-2_amd64.deb ...
Unpacking python-tdb (1.3.8-2) ...
Selecting previously unselected package python-samba.
Preparing to unpack .../python-samba_2%3a4.3.8+dfsg-0ubuntu1_amd64.deb ...
Unpacking python-samba (2:4.3.8+dfsg-0ubuntu1) ...
Selecting previously unselected package samba-common.
Preparing to unpack .../samba-common_2%3a4.3.8+dfsg-0ubuntu1_all.deb ...
Unpacking samba-common (2:4.3.8+dfsg-0ubuntu1) ...
Selecting previously unselected package samba-common-bin.
Preparing to unpack .../samba-common-bin_2%3a4.3.8+dfsg-0ubuntu1_amd64.deb ...
Unpacking samba-common-bin (2:4.3.8+dfsg-0ubuntu1) ...
Selecting previously unselected package tdb-tools.
Preparing to unpack .../tdb-tools_1.3.8-2_amd64.deb ...
Unpacking tdb-tools (1.3.8-2) ...
Selecting previously unselected package samba.
Preparing to unpack .../samba_2%3a4.3.8+dfsg-0ubuntu1_amd64.deb ...
Unpacking samba (2:4.3.8+dfsg-0ubuntu1) ...
Selecting previously unselected package attr.
Preparing to unpack .../attr_1%3a2.4.47-2_amd64.deb ...
Unpacking attr (1:2.4.47-2) ...
Selecting previously unselected package libaio1:amd64.
Preparing to unpack .../libaio1_0.3.110-2_amd64.deb ...
Unpacking libaio1:amd64 (0.3.110-2) ...
Selecting previously unselected package samba-dsdb-modules.
Preparing to unpack .../samba-dsdb-modules_2%3a4.3.8+dfsg-0ubuntu1_amd64.deb ...
Unpacking samba-dsdb-modules (2:4.3.8+dfsg-0ubuntu1) ...
Selecting previously unselected package samba-vfs-modules.
Preparing to unpack .../samba-vfs-modules_2%3a4.3.8+dfsg-0ubuntu1_amd64.deb ...
Unpacking samba-vfs-modules (2:4.3.8+dfsg-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (229-4ubuntu4) ...
Processing triggers for ufw (0.35-0ubuntu2) ...
Setting up binfmt-support (2.1.6-1) ...
insserv: warning: script 'K20mmserver' missing LSB tags and overrides
insserv: warning: script 'mmserver' missing LSB tags and overrides
insserv: There is a loop at service plymouth if started
insserv: There is a loop between service plymouth and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service kerneloops at depth 1
insserv: There is a loop between service mmserver and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service mmserver if started
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service plymouth and urandom if started
insserv:  loop involving service urandom at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service mmserver and udev if started
insserv:  loop involving service mountkernfs at depth 1
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service mmserver and dns-clean if started
insserv:  loop involving service dns-clean at depth 1
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package binfmt-support (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of wine1.6:
 wine1.6 depends on binfmt-support (>= 1.1.2); however:
  Package binfmt-support is not configured yet.

dpkg: error processing package wine1.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.6-i386:i386:
 wine1.6-i386:i386 depends on wine1.6:any (= 1:1.6.2-0ubuntu14); however:
  Package wine1.6 is not configured yet.

dpkg: error processing package wine1.6-i386:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                No apport report written because the error message indicates its a followup error from a previous failure.
                                      Setting up python-dnspython (1.12.0-1) ...
Setting up python-crypto (2.6.1-6build1) ...
Setting up python-ldb (2:1.1.24-1ubuntu3) ...
Setting up python-tdb (1.3.8-2) ...
Setting up python-samba (2:4.3.8+dfsg-0ubuntu1) ...
Setting up samba-common (2:4.3.8+dfsg-0ubuntu1) ...

Creating config file /etc/samba/smb.conf with new version
Setting up samba-common-bin (2:4.3.8+dfsg-0ubuntu1) ...
Setting up tdb-tools (1.3.8-2) ...
update-alternatives: using /usr/bin/tdbbackup.tdbtools to provide /usr/bin/tdbbackup (tdbbackup) in auto mode
Setting up samba (2:4.3.8+dfsg-0ubuntu1) ...
insserv: warning: script 'K20mmserver' missing LSB tags and overrides
insserv: warning: script 'mmserver' missing LSB tags and overrides
insserv: There is a loop at service plymouth if started
insserv: There is a loop between service plymouth and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service kerneloops at depth 1
insserv: There is a loop between service mmserver and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service mmserver if started
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service plymouth and urandom if started
insserv:  loop involving service urandom at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service mmserver and udev if started
insserv:  loop involving service mountkernfs at depth 1
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service mmserver and dns-clean if started
insserv:  loop involving service dns-clean at depth 1
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting mmserver depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package samba (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
    Setting up attr (1:2.4.47-2) ...
Setting up libaio1:amd64 (0.3.110-2) ...
Setting up samba-dsdb-modules (2:4.3.8+dfsg-0ubuntu1) ...
Setting up samba-vfs-modules (2:4.3.8+dfsg-0ubuntu1) ...
No apport report written because MaxReports is reached already
    dpkg: dependency problems prevent configuration of wine1.6-amd64:
 wine1.6-amd64 depends on wine1.6:any (= 1:1.6.2-0ubuntu14); however:
  Package wine1.6 is not configured yet.

dpkg: error processing package wine1.6-amd64 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (229-4ubuntu4) ...
Processing triggers for ufw (0.35-0ubuntu2) ...
Errors were encountered while processing:
 binfmt-support
 wine1.6
 wine1.6-i386:i386
 samba
 wine1.6-amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
david@MainSqueeze:~$ 

```

---

### Post by SuperFreak on 2016-04-22
Results of sudo dpkg --audit

I tried suggested solutions in output but the packages would not install

```
sudo dpkg --audit
[sudo] password for david: 
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 wine1.6              Microsoft Windows Compatibility Layer (Binary Emulator an
 wine1.6-amd64        Microsoft Windows Compatibility Layer (64-bit support)
 wine1.6-i386:i386    Microsoft Windows Compatibility Layer (32-bit support)

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 binfmt-support       Support for extra binary formats
 samba                SMB/CIFS file, print, and login server for Unix
```

---

### Post by SuperFreak on 2016-04-24
Did a reinstall.

---

