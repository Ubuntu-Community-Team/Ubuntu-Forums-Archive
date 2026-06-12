---
title: "i think i messed something up?"
date: 2018-05-01
forum: General Help
---

### Post by delfiler on 2018-05-01
so i recently just installed citadel groupware and adjusted my firewall script so the ports for it are open. and now when i try to do apt-get upgrade (as root) i get the following
```
root@pe-fw:/etc# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apt-xapian-index aptitude-common gcc-4.8-base gcc-4.9-base libapt-inst1.5 libarchive-extract-perl libbind9-90 libboost-iostreams1.54.0 libboost-iostreams1.58.0 libcgi-fast-perl libcgi-pm-perl libck-connector0 libclass-accessor-perl
  libcwidget3 libdns100 libencode-locale-perl libept1.4.12 libfcgi-perl libgck-1-0 libgcr-3-common libgcr-base-3-1 libhtml-parser-perl libhtml-tagset-perl libhttp-date-perl libhttp-message-perl libio-html-perl libio-string-perl
  libisc95 libisccc90 libisccfg90 libjson0 liblog-message-perl liblog-message-simple-perl liblwp-mediatypes-perl liblwres90 libmodule-pluggable-perl libmodule-runtime-perl libparams-classify-perl libparse-debianchangelog-perl
  libpod-latex-perl libprocps3 libsigc++-2.0-0c2a libsub-name-perl libsystemd-daemon0 libsystemd-login0 libterm-ui-perl libtext-soundex-perl libtimedate-perl liburi-perl libxapian-1.3-5 libxapian22v5 libxtables10
  linux-headers-3.13.0-142 linux-headers-3.13.0-142-generic linux-image-3.13.0-142-generic linux-image-extra-3.13.0-142-generic python-ndg-httpsclient python-requests python-urllib3 python-xapian python3-xapian1.3
Use 'apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
Setting up ifupdown (0.8.10ubuntu1.3) ...
insserv: warning: script 'K15webcit' missing LSB tags and overridesinsserv: warning: script 'webcit' missing LSB tags and overrides
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `screen-cleanup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `screen-cleanup'
insserv: There is a loop at service plymouth if started
insserv: There is a loop between service webcit and plymouth if started
insserv:  loop involving service plymouth at depth 2
insserv:  loop involving service webcit at depth 1
insserv:  loop involving service rsyslog at depth 1
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true! (<-- that line repeats 48 times)
insserv: Max recursions depth 99 reached
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package ifupdown (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ifupdown
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
so i guess something is messed up cause i can't seem to find the problem so any help?

update1: i can't install anything at all aswell so this is something that must be fixed

the following happens when i try to install something:
```
root@pe-fw:/etc# apt-get install spamassassinReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apt-xapian-index aptitude-common gcc-4.8-base gcc-4.9-base libapt-inst1.5 libarchive-extract-perl libbind9-90 libboost-iostreams1.54.0 libboost-iostreams1.58.0 libcgi-fast-perl libcgi-pm-perl libck-connector0 libclass-accessor-perl
  libcwidget3 libdns100 libept1.4.12 libfcgi-perl libgck-1-0 libgcr-3-common libgcr-base-3-1 libio-string-perl libisc95 libisccc90 libisccfg90 libjson0 liblog-message-perl liblog-message-simple-perl liblwres90 libmodule-pluggable-perl
  libmodule-runtime-perl libparams-classify-perl libparse-debianchangelog-perl libpod-latex-perl libprocps3 libsigc++-2.0-0c2a libsub-name-perl libsystemd-daemon0 libsystemd-login0 libterm-ui-perl libtext-soundex-perl libxapian-1.3-5
  libxapian22v5 libxtables10 linux-headers-3.13.0-142 linux-headers-3.13.0-142-generic linux-image-3.13.0-142-generic linux-image-extra-3.13.0-142-generic python-ndg-httpsclient python-requests python-urllib3 python-xapian
  python3-xapian1.3
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  libdigest-hmac-perl libio-socket-inet6-perl libmail-spf-perl libnet-dns-perl libnet-ip-perl libnetaddr-ip-perl libsocket6-perl libsys-hostname-long-perl re2c sa-compile spamc
Suggested packages:
  razor libio-socket-ssl-perl libdbi-perl pyzor libmail-dkim-perl libencode-detect-perl
The following NEW packages will be installed:
  libdigest-hmac-perl libio-socket-inet6-perl libmail-spf-perl libnet-dns-perl libnet-ip-perl libnetaddr-ip-perl libsocket6-perl libsys-hostname-long-perl re2c sa-compile spamassassin spamc
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 1,963 kB of archives.
After this operation, 6,533 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 libdigest-hmac-perl all 1.03+dfsg-1 [12.1 kB]
Get:2 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 libsocket6-perl i386 0.25-1build2 [23.9 kB]
Get:3 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 libio-socket-inet6-perl all 2.72-2 [13.8 kB]
Get:4 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 libnet-ip-perl all 1.26-1 [31.5 kB]
Get:5 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 libnet-dns-perl i386 0.81-2build1 [266 kB]
Get:6 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 libnetaddr-ip-perl i386 4.078+dfsg-1build1 [82.6 kB]
Get:7 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 libmail-spf-perl all 2.9.0-4 [115 kB]
Get:8 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 libsys-hostname-long-perl all 1.5-1 [11.7 kB]
Get:9 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 re2c i386 0.16-1 [225 kB]
Get:10 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 spamassassin all 3.4.1-3 [1,116 kB]
Get:11 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 sa-compile all 3.4.1-3 [13.8 kB]
Get:12 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 spamc i386 3.4.1-3 [52.2 kB]
Fetched 1,963 kB in 0s (3,170 kB/s)
Selecting previously unselected package libdigest-hmac-perl.
(Reading database ... 166167 files and directories currently installed.)
Preparing to unpack .../libdigest-hmac-perl_1.03+dfsg-1_all.deb ...
Unpacking libdigest-hmac-perl (1.03+dfsg-1) ...
Selecting previously unselected package libsocket6-perl.
Preparing to unpack .../libsocket6-perl_0.25-1build2_i386.deb ...
Unpacking libsocket6-perl (0.25-1build2) ...
Selecting previously unselected package libio-socket-inet6-perl.
Preparing to unpack .../libio-socket-inet6-perl_2.72-2_all.deb ...
Unpacking libio-socket-inet6-perl (2.72-2) ...
Selecting previously unselected package libnet-ip-perl.
Preparing to unpack .../libnet-ip-perl_1.26-1_all.deb ...
Unpacking libnet-ip-perl (1.26-1) ...
Selecting previously unselected package libnet-dns-perl.
Preparing to unpack .../libnet-dns-perl_0.81-2build1_i386.deb ...
Unpacking libnet-dns-perl (0.81-2build1) ...
Selecting previously unselected package libnetaddr-ip-perl.
Preparing to unpack .../libnetaddr-ip-perl_4.078+dfsg-1build1_i386.deb ...
Unpacking libnetaddr-ip-perl (4.078+dfsg-1build1) ...
Selecting previously unselected package libmail-spf-perl.
Preparing to unpack .../libmail-spf-perl_2.9.0-4_all.deb ...
Unpacking libmail-spf-perl (2.9.0-4) ...
Selecting previously unselected package libsys-hostname-long-perl.
Preparing to unpack .../libsys-hostname-long-perl_1.5-1_all.deb ...
Unpacking libsys-hostname-long-perl (1.5-1) ...
Selecting previously unselected package re2c.
Preparing to unpack .../archives/re2c_0.16-1_i386.deb ...
Unpacking re2c (0.16-1) ...
Selecting previously unselected package spamassassin.
Preparing to unpack .../spamassassin_3.4.1-3_all.deb ...
Unpacking spamassassin (3.4.1-3) ...
Selecting previously unselected package sa-compile.
Preparing to unpack .../sa-compile_3.4.1-3_all.deb ...
Unpacking sa-compile (3.4.1-3) ...
Selecting previously unselected package spamc.
Preparing to unpack .../spamc_3.4.1-3_i386.deb ...
Unpacking spamc (3.4.1-3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for systemd (229-4ubuntu21.2) ...
Processing triggers for ureadahead (0.100.0-19) ...
Setting up ifupdown (0.8.10ubuntu1.3) ...
insserv: warning: script 'K15webcit' missing LSB tags and overrides
insserv: warning: script 'webcit' missing LSB tags and overrides
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `screen-cleanup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `screen-cleanup'
insserv: There is a loop at service plymouth if started
insserv: There is a loop between service webcit and plymouth if started
insserv:  loop involving service plymouth at depth 2
insserv:  loop involving service webcit at depth 1
insserv:  loop involving service rsyslog at depth 1
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package ifupdown (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up clamav-freshclam (0.99.4+addedllvm-0ubuntu0.16.04.1) ...
insserv: warning: script 'K15webcit' missing LSB tags and overrides
insserv: warning: script 'webcit' missing LSB tags and overrides
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `screen-cleanup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `screen-cleanup'
insserv: There is a loop at service plymouth if started
insserv: There is a loop between service webcit and plymouth if started
insserv:  loop involving service plymouth at depth 2
insserv:  loop involving service webcit at depth 1
insserv:  loop involving service rsyslog at depth 1
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package clamav-freshclam (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam (>= 0.99.4+addedllvm) | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.


dpkg: error processing package clamav (--configure):
 dependency problems - leaving unconfigured
Setting up libdigest-hmac-perl (1.03+dfsg-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up libsocket6-perl (0.25-1build2) ...
Setting up libio-socket-inet6-perl (2.72-2) ...
Setting up libnet-ip-perl (1.26-1) ...
Setting up libnet-dns-perl (0.81-2build1) ...
Setting up libnetaddr-ip-perl (4.078+dfsg-1build1) ...
Setting up libmail-spf-perl (2.9.0-4) ...
Setting up libsys-hostname-long-perl (1.5-1) ...
Setting up re2c (0.16-1) ...
Setting up spamassassin (3.4.1-3) ...
Adding system user `debian-spamd' (UID 116) ...
Adding new group `debian-spamd' (GID 123) ...
Adding new user `debian-spamd' (UID 116) with group `debian-spamd' ...
Creating home directory `/var/lib/spamassassin' ...
insserv: warning: script 'K15webcit' missing LSB tags and overrides
insserv: warning: script 'webcit' missing LSB tags and overrides
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `screen-cleanup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `screen-cleanup'
insserv: There is a loop at service plymouth if started
insserv: There is a loop between service webcit and plymouth if started
insserv:  loop involving service plymouth at depth 2
insserv:  loop involving service webcit at depth 1
insserv:  loop involving service rsyslog at depth 1
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting webcit depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package spamassassin (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of sa-compile:
 sa-compile depends on spamassassin; however:
  Package spamassassin is not configured yet.


dpkg: error processing package sa-compile (--configure):
 dependency problems - leaving unconfigured
Setting up spamc (3.4.1-3) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Processing triggers for systemd (229-4ubuntu21.2) ...
Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 ifupdown
 clamav-freshclam
 clamav
 spamassassin
 sa-compile
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

update2: the ubuntu version i am using is 16.04 command line only

---

### Post by TheFu on 2018-05-01
did you **apt-get update** first?
Always update before upgrade.

And if you've manually installed any .deb files outside the normal repos, we need to know about those too.

---

### Post by delfiler on 2018-05-02
yes i did apt-get update first should have mentioned that and well all i did to install citadel groupware was doing the following command
```
[COLOR=#000000]curl http://easyinstall.citadel.org/install | sh[/COLOR]
```
and then follow the the installation

the firewall that i mentioned is a costum one of the company but i helped build it a bit

and i guess this was all the info you wanted to know fu?

---

### Post by TheFu on 2018-05-02
I looked over the citadel  install script.  Nothing inside there should have messed up APT that I can see.  It installs a few dependency packages using  apt-get, but everything else related to Citadel is installed from source code.

With the current issues, I'd remove citadel and fix the apt dependencies which have appeared.  Then try reinstalling it.

---

### Post by delfiler on 2018-05-02
okay did remove it but i am stuck at the part of fixing the apt dependencies as i said earlier i am still new to ubuntu

---

### Post by TheFu on 2018-05-02
Maybe someone else can help better than I.

Thanks for using code tags. Very helpful.  

When posting, please don't make others assume what you have or haven't done. Clarity is very useful.
For example, did you run autoremove yet?  Doing an autoclean wouldn't hurt either.

```
sudo apt autoremove
sudo apt autoclean
sudo apt update
sudo apt dist-upgrade
```

After doing those, did you run the update/upgrade again?  Any interesting output?  Look for errors and warnings.  

I don't see the firewall harming any of the APT stuff. That uses http and https, which seems to be working fine.  Is that correct?

---

### Post by delfiler on 2018-05-02
yes the firewall doesn't block those at all but does check them against a blacklist of bad stuff (worms, trojans, viruses and the bunch). 
i didn't do the autoremove yet so that is still there and i did try the update/upgrade but still same result

edit1: so i did all the lines you suggested and the problems still persist

---

### Post by delfiler on 2018-05-02
UPDATE!: [COLOR=#111111][FONT=Ubuntu] i noticed something in the lines of code that i found odd as i tried to remove citadel, thinking that might be the cause, i noticed a few words that correlated to citadel and after some research and trail and error it seemed to be that citadel wasn't compleetly gone yet so i am trying to track down the remaining parts of it and try to remove them to see what will happen

after a reboot and deleting the correlating files everything word as it should again[/FONT][/COLOR]

---

### Post by TheFu on 2018-05-02
Whenever the kernel or libc are modified, rebooting is recommended.

In theory, there is a file, /var/run/reboot-required, that is created whenever rebooting after a patch is needed.  I guess it is 99% accurate.  I always check if that file exists before deciding whether to reboot or not.

I'm the last person to suggest that rebooting corrects most things.  It generally isn't necessary - Linux isn't Windows - but certain things like misbehaving hardware or new drivers may perform better post-reboot.  For example, there are some network card drivers that appear to need their registers reset in a way that a reboot does. Generally, stuff like this happens on systems where people dual-boot, not Linux-only systems.

The other time to reboot is when lots and lots of packages change.   There isn't any fixed number for "lots and lots" and it would depend on the packages involved.

Glad you got it working.

---

