---
title: "Deja-dup won't restore to external drive"
date: 2020-05-18
forum: General Help
---

### Post by JamButty on 2020-05-18
Just started working with a new external HDD. One of the partitions on it is meant for backups. It will perform a backup to the external drive backup partition and will restore from it to the internal drive, but will not restore to the other partition on the external. In case this was a snap issue, I deinstalled the default deja-dup and reinstalled via command line apt, but the issue remains.
This is 20.04

---

### Post by TheFu on 2020-05-18
Check that the apt installed package isn't just a wrapper that still installs the snap version.

Canonical has been doing that with some apps.

---

### Post by JamButty on 2020-05-18
How would I check that? 
fwiw, here is the install output
```
 sudo apt install deja-dup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  duplicity librsync2 python3-bcrypt python3-fasteners python3-future
  python3-lib2to3 python3-lockfile python3-monotonic python3-paramiko
Suggested packages:
  python3-boto python3-swiftclient python3-pydrive ncftp lftp tahoe-lafs
  python3-pip par2 python-future-doc python-lockfile-doc python3-gssapi
The following NEW packages will be installed:
  deja-dup duplicity librsync2 python3-bcrypt python3-fasteners python3-future
  python3-lib2to3 python3-lockfile python3-monotonic python3-paramiko
0 upgraded, 10 newly installed, 0 to remove and 45 not upgraded.
Need to get 1,105 kB of archives.
After this operation, 5,904 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 librsync2 amd64 2.0.2-1ubuntu1 [38.8 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 python3-monotonic all 1.5-0ubuntu2 [5,660 B]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 python3-fasteners all 0.14.1-2 [14.1 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 python3-lib2to3 all 3.8.2-1ubuntu1 [74.1 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 python3-future all 0.18.2-2 [336 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 python3-lockfile all 1:0.12.2-2ubuntu2 [14.6 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 duplicity amd64 0.8.11.1612-1 [199 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 deja-dup amd64 40.6-1ubuntu2 [270 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 python3-bcrypt amd64 3.1.7-2ubuntu1 [30.4 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 python3-paramiko all 2.6.0-2 [122 kB]
Fetched 1,105 kB in 1s (1,187 kB/s)        
Selecting previously unselected package librsync2:amd64.
(Reading database ... 195059 files and directories currently installed.)
Preparing to unpack .../0-librsync2_2.0.2-1ubuntu1_amd64.deb ...
Unpacking librsync2:amd64 (2.0.2-1ubuntu1) ...
Selecting previously unselected package python3-monotonic.
Preparing to unpack .../1-python3-monotonic_1.5-0ubuntu2_all.deb ...
Unpacking python3-monotonic (1.5-0ubuntu2) ...
Selecting previously unselected package python3-fasteners.
Preparing to unpack .../2-python3-fasteners_0.14.1-2_all.deb ...
Unpacking python3-fasteners (0.14.1-2) ...
Selecting previously unselected package python3-lib2to3.
Preparing to unpack .../3-python3-lib2to3_3.8.2-1ubuntu1_all.deb ...
Unpacking python3-lib2to3 (3.8.2-1ubuntu1) ...
Selecting previously unselected package python3-future.
Preparing to unpack .../4-python3-future_0.18.2-2_all.deb ...
Unpacking python3-future (0.18.2-2) ...
Selecting previously unselected package python3-lockfile.
Preparing to unpack .../5-python3-lockfile_1%3a0.12.2-2ubuntu2_all.deb ...
Unpacking python3-lockfile (1:0.12.2-2ubuntu2) ...
Selecting previously unselected package duplicity.
Preparing to unpack .../6-duplicity_0.8.11.1612-1_amd64.deb ...
Unpacking duplicity (0.8.11.1612-1) ...
Selecting previously unselected package deja-dup.
Preparing to unpack .../7-deja-dup_40.6-1ubuntu2_amd64.deb ...
Unpacking deja-dup (40.6-1ubuntu2) ...
Selecting previously unselected package python3-bcrypt.
Preparing to unpack .../8-python3-bcrypt_3.1.7-2ubuntu1_amd64.deb ...
Unpacking python3-bcrypt (3.1.7-2ubuntu1) ...
Selecting previously unselected package python3-paramiko.
Preparing to unpack .../9-python3-paramiko_2.6.0-2_all.deb ...
Unpacking python3-paramiko (2.6.0-2) ...
Setting up python3-lockfile (1:0.12.2-2ubuntu2) ...
Setting up python3-bcrypt (3.1.7-2ubuntu1) ...
Setting up python3-monotonic (1.5-0ubuntu2) ...
Setting up python3-fasteners (0.14.1-2) ...
Setting up librsync2:amd64 (2.0.2-1ubuntu1) ...
Setting up python3-paramiko (2.6.0-2) ...
Setting up python3-lib2to3 (3.8.2-1ubuntu1) ...
Setting up python3-future (0.18.2-2) ...
update-alternatives: using /usr/bin/python3-futurize to provide /usr/bin/futuriz
e (futurize) in auto mode
update-alternatives: using /usr/bin/python3-pasteurize to provide /usr/bin/paste
urize (pasteurize) in auto mode
Setting up duplicity (0.8.11.1612-1) ...
Setting up deja-dup (40.6-1ubuntu2) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.64.2-1~fakesync1) ...
Processing triggers for libc-bin (2.31-0ubuntu9) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu2) ...

```

---

### Post by TheFu on 2020-05-19
snap list

---

### Post by JamButty on 2020-05-23
Sorry, missed your reply earlier. Not much under snap currently. Dejadup is not there.
[PHP]Name                 Version                     Rev   Tracking         Publisher   Notes
audacity             2.3.3                       648   latest/stable    diddledan   -
canonical-livepatch  9.5.5                       95    latest/stable    canonical&#10003;  -
core                 16-2.44.3                   9066  latest/stable    canonical&#10003;  core
core18               20200427                    1754  latest/stable    canonical&#10003;  base
gnome-3-28-1804      3.28.0-16-g27c9498.27c9498  116   latest/stable    canonical&#10003;  -
gnome-3-34-1804      0+git.3009fc7               33    latest/stable/…  canonical&#10003;  -
gtk-common-themes    0.1-36-gc75f853             1506  latest/stable/…  canonical&#10003;  -
gtk2-common-themes   0.1                         9     latest/stable    canonical&#10003;  -
snap-store           3.36.0-80-g208fd61          454   latest/stable/…  canonical&#10003;  -
snapd                2.44.3                      7264  latest/stable    canonical&#10003;  snapd
vlc                  3.0.10                      1620  latest/stable    videolan&#10003;   -

[/PHP]

---

