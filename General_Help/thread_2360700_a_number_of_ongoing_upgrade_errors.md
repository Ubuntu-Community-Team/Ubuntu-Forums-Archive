---
title: "a number of ongoing upgrade errors"
date: 2017-05-07
forum: General Help
---

### Post by s9032g@comcast.net on 2017-05-07
I have been having problems with upgrade/update errors for some time. using Synaptic as well as terminal commands. Any suggestions?
```
steven@steven-Latitude-E7240:~$ sudo apt-get update
[sudo] password for steven: 
Hit:1 [http://ppa.launchpad.net/jtaylor/keepass/ubuntu](http://ppa.launchpad.net/jtaylor/keepass/ubuntu) xenial InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Get:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release [1,189 B]           
Get:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg [916 B]         
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                    
Get:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable/main amd64 Packages [1,454 B]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]       
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [527 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [513 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [214 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [289 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [187 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [460 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [446 kB]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [160 kB]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [188 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [257 kB]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main i386 Packages [245 kB]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main Translation-en [109 kB]
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [54.7 kB]
Get:25 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [50.3 kB]
Get:26 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [32.2 kB]
Get:27 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Get:28 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Fetched 4,085 kB in 8s (475 kB/s)                                     
Reading package lists... Done
steven@steven-Latitude-E7240:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  login passwd
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1,085 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 login amd64 1:4.2-3.1ubuntu5.2 [305 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 passwd amd64 1:4.2-3.1ubuntu5.2 [780 kB]
Fetched 1,085 kB in 7s (138 kB/s)
(Reading database ... 225919 files and directories currently installed.)
Preparing to unpack .../login_1%3a4.2-3.1ubuntu5.2_amd64.deb ...
Unpacking login (1:4.2-3.1ubuntu5.2) over (1:4.2-3.1ubuntu5) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up login (1:4.2-3.1ubuntu5.2) ...
(Reading database ... 225919 files and directories currently installed.)
Preparing to unpack .../passwd_1%3a4.2-3.1ubuntu5.2_amd64.deb ...
Unpacking passwd (1:4.2-3.1ubuntu5.2) over (1:4.2-3.1ubuntu5) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Setting up passwd (1:4.2-3.1ubuntu5.2) ...
Setting up amavisd-new (1:2.10.1-2ubuntu1) ...
Creating/updating amavis user account...
Job for amavis.service failed because the control process exited with error code. See "systemctl status amavis.service" and "journalctl -xe" for details.
invoke-rc.d: initscript amavis, action "start" failed.
&#9679; amavis.service - LSB: Starts amavisd-new mailfilter
   Loaded: loaded (/etc/init.d/amavis; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2017-05-07 10:00:42 MST; 4ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 5889 ExecStart=/etc/init.d/amavis start (code=exited, status=1/FAILURE)
```

```
May 07 10:00:42 steven-Latitude-E7240 amavis[5889]:   The value of variable $...
May 07 10:00:42 steven-Latitude-E7240 amavis[5889]:   a fully qualified domai...
May 07 10:00:42 steven-Latitude-E7240 amavis[5889]:   You must explicitly ass...
May 07 10:00:42 steven-Latitude-E7240 amavis[5889]:   in /etc/amavis/conf.d/0...
May 07 10:00:42 steven-Latitude-E7240 amavis[5889]:   network name!
May 07 10:00:42 steven-Latitude-E7240 amavis[5889]: (failed).
May 07 10:00:42 steven-Latitude-E7240 systemd[1]: amavis.service: Control pro...
May 07 10:00:42 steven-Latitude-E7240 systemd[1]: Failed to start LSB: Starts...
May 07 10:00:42 steven-Latitude-E7240 systemd[1]: amavis.service: Unit entere...
May 07 10:00:42 steven-Latitude-E7240 systemd[1]: amavis.service: Failed with...
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package amavisd-new (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 amavisd-new
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by #&amp;thj^% on 2017-05-07
Thanks deadflowr for the Code tags.:)
There are a ton of bug reports on this...with no solution.
But for myself, all I had to do was:
1)
```
sudo apt remove amavisd-new
```

and then

2)
```
sudo apt autoremove
```

then it was necessary to run:
```
sudo dpkg --configure -a
```

And reinstall "amavisd-new"
Hope that helps you also.

---

### Post by s9032g@comcast.net on 2017-05-08
Thanks. Please expand on this final step. I did the rest

And reinstall "amavisd-new"
Hope that helps you also.

---

### Post by s9032g@comcast.net on 2017-05-08
1fallen

So I ran this
sudo apt-get install amavisd-new spamassassin clamav-daemon

and I seem to be back to all the errors that I had before. amybe the spam assassin part was wrong??

```
steven@steven-Latitude-E7240:~$ sudo apt-get install amavisd-new spamassassin clamav-daemon
[sudo] password for steven: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clamav-daemon is already the newest version (0.99.2+dfsg-0ubuntu0.16.04.1).
The following additional packages will be installed:
  libberkeleydb-perl libconvert-binhex-perl libconvert-tnef-perl
  libconvert-uulib-perl liberror-perl libio-multiplex-perl libio-stringy-perl
  libmail-dkim-perl libmail-spf-perl libmime-tools-perl libnet-cidr-perl
  libnet-server-perl libnetaddr-ip-perl libunix-syslog-perl pax re2c
  sa-compile spamc
Suggested packages:
  apt-listchanges arj dspam lhasa libdbi-perl libnet-ldap-perl libsnmp-perl
  libzeromq-perl lzop nomarch p7zip rpm unrar altermime ripole
  liblog-log4perl-perl razor pyzor libencode-detect-perl
Recommended packages:
  libnet-patricial-perl
The following NEW packages will be installed:
  amavisd-new libberkeleydb-perl libconvert-binhex-perl libconvert-tnef-perl
  libconvert-uulib-perl liberror-perl libio-multiplex-perl libio-stringy-perl
  libmail-dkim-perl libmail-spf-perl libmime-tools-perl libnet-cidr-perl
  libnet-server-perl libnetaddr-ip-perl libunix-syslog-perl pax re2c
  sa-compile spamassassin spamc
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,221 kB of archives.
After this operation, 11.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libberkeleydb-perl amd64 0.55-1build1 [109 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libconvert-binhex-perl all 1.125-1 [29.7 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libio-stringy-perl all 2.110-5 [93.5 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libmime-tools-perl all 5.507-1 [207 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libconvert-tnef-perl all 0.18-1 [19.7 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libconvert-uulib-perl amd64 1:1.4~dfsg-1build5 [88.9 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 liberror-perl all 0.17-1.2 [19.6 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libio-multiplex-perl all 1.16-1 [20.5 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libmail-dkim-perl all 0.40-1 [117 kB]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libnetaddr-ip-perl amd64 4.078+dfsg-1build1 [81.2 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libmail-spf-perl all 2.9.0-4 [115 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libnet-cidr-perl all 0.17-1 [14.8 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libnet-server-perl all 2.008-2 [180 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libunix-syslog-perl amd64 1.1-2build7 [21.6 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 pax amd64 1:20151013-1 [78.8 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 re2c amd64 0.16-1 [220 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 spamassassin all 3.4.1-3 [1,116 kB]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 sa-compile all 3.4.1-3 [13.8 kB]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 spamc amd64 3.4.1-3 [51.8 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 amavisd-new all 1:2.10.1-2ubuntu1 [624 kB]
Fetched 3,221 kB in 1s (2,687 kB/s)   
Selecting previously unselected package libberkeleydb-perl.
(Reading database ... 225524 files and directories currently installed.)
Preparing to unpack .../libberkeleydb-perl_0.55-1build1_amd64.deb ...
Unpacking libberkeleydb-perl (0.55-1build1) ...
Selecting previously unselected package libconvert-binhex-perl.
Preparing to unpack .../libconvert-binhex-perl_1.125-1_all.deb ...
Unpacking libconvert-binhex-perl (1.125-1) ...
Selecting previously unselected package libio-stringy-perl.
Preparing to unpack .../libio-stringy-perl_2.110-5_all.deb ...
Unpacking libio-stringy-perl (2.110-5) ...
Selecting previously unselected package libmime-tools-perl.
Preparing to unpack .../libmime-tools-perl_5.507-1_all.deb ...
Unpacking libmime-tools-perl (5.507-1) ...
Selecting previously unselected package libconvert-tnef-perl.
Preparing to unpack .../libconvert-tnef-perl_0.18-1_all.deb ...
Unpacking libconvert-tnef-perl (0.18-1) ...
Selecting previously unselected package libconvert-uulib-perl.
Preparing to unpack .../libconvert-uulib-perl_1%3a1.4~dfsg-1build5_amd64.deb ...
Unpacking libconvert-uulib-perl (1:1.4~dfsg-1build5) ...
Selecting previously unselected package liberror-perl.
Preparing to unpack .../liberror-perl_0.17-1.2_all.deb ...
Unpacking liberror-perl (0.17-1.2) ...
Selecting previously unselected package libio-multiplex-perl.
Preparing to unpack .../libio-multiplex-perl_1.16-1_all.deb ...
Unpacking libio-multiplex-perl (1.16-1) ...
Selecting previously unselected package libmail-dkim-perl.
Preparing to unpack .../libmail-dkim-perl_0.40-1_all.deb ...
Unpacking libmail-dkim-perl (0.40-1) ...
Selecting previously unselected package libnetaddr-ip-perl.
Preparing to unpack .../libnetaddr-ip-perl_4.078+dfsg-1build1_amd64.deb ...
Unpacking libnetaddr-ip-perl (4.078+dfsg-1build1) ...
Selecting previously unselected package libmail-spf-perl.
Preparing to unpack .../libmail-spf-perl_2.9.0-4_all.deb ...
Unpacking libmail-spf-perl (2.9.0-4) ...
Selecting previously unselected package libnet-cidr-perl.
Preparing to unpack .../libnet-cidr-perl_0.17-1_all.deb ...
Unpacking libnet-cidr-perl (0.17-1) ...
Selecting previously unselected package libnet-server-perl.
Preparing to unpack .../libnet-server-perl_2.008-2_all.deb ...
Unpacking libnet-server-perl (2.008-2) ...
Selecting previously unselected package libunix-syslog-perl.
Preparing to unpack .../libunix-syslog-perl_1.1-2build7_amd64.deb ...
Unpacking libunix-syslog-perl (1.1-2build7) ...
Selecting previously unselected package pax.
Preparing to unpack .../pax_1%3a20151013-1_amd64.deb ...
Unpacking pax (1:20151013-1) ...
Selecting previously unselected package re2c.
Preparing to unpack .../archives/re2c_0.16-1_amd64.deb ...
Unpacking re2c (0.16-1) ...
Selecting previously unselected package spamassassin.
Preparing to unpack .../spamassassin_3.4.1-3_all.deb ...
Unpacking spamassassin (3.4.1-3) ...
Selecting previously unselected package sa-compile.
Preparing to unpack .../sa-compile_3.4.1-3_all.deb ...
Unpacking sa-compile (3.4.1-3) ...
Selecting previously unselected package spamc.
Preparing to unpack .../spamc_3.4.1-3_amd64.deb ...
Unpacking spamc (3.4.1-3) ...
Selecting previously unselected package amavisd-new.
Preparing to unpack .../amavisd-new_1%3a2.10.1-2ubuntu1_all.deb ...
Unpacking amavisd-new (1:2.10.1-2ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for doc-base (0.10.7) ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for systemd (229-4ubuntu17) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Setting up libberkeleydb-perl (0.55-1build1) ...
Setting up libconvert-binhex-perl (1.125-1) ...
Setting up libio-stringy-perl (2.110-5) ...
Setting up libmime-tools-perl (5.507-1) ...
Setting up libconvert-tnef-perl (0.18-1) ...
Setting up libconvert-uulib-perl (1:1.4~dfsg-1build5) ...
Setting up liberror-perl (0.17-1.2) ...
Setting up libio-multiplex-perl (1.16-1) ...
Setting up libmail-dkim-perl (0.40-1) ...
Setting up libnetaddr-ip-perl (4.078+dfsg-1build1) ...
Setting up libmail-spf-perl (2.9.0-4) ...
Setting up libnet-cidr-perl (0.17-1) ...
Setting up libnet-server-perl (2.008-2) ...
Setting up libunix-syslog-perl (1.1-2build7) ...
Setting up pax (1:20151013-1) ...
Setting up re2c (0.16-1) ...
Setting up spamassassin (3.4.1-3) ...
Setting up sa-compile (3.4.1-3) ...
Running sa-compile (may take a long time)
Setting up spamc (3.4.1-3) ...
Setting up amavisd-new (1:2.10.1-2ubuntu1) ...
Creating/updating amavis user account...
Job for amavis.service failed because the control process exited with error code. See "systemctl status amavis.service" and "journalctl -xe" for details.
invoke-rc.d: initscript amavis, action "start" failed.
&#9679; amavis.service - LSB: Starts amavisd-new mailfilter
   Loaded: loaded (/etc/init.d/amavis; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2017-05-08 05:32:02 MST; 4ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 8323 ExecStart=/etc/init.d/amavis start (code=exited, status=1/FAILURE)

May 08 05:32:02 steven-Latitude-E7240 amavis[8323]:   The value of variable $...
May 08 05:32:02 steven-Latitude-E7240 amavis[8323]:   a fully qualified domai...
May 08 05:32:02 steven-Latitude-E7240 amavis[8323]:   You must explicitly ass...
May 08 05:32:02 steven-Latitude-E7240 amavis[8323]:   in /etc/amavis/conf.d/0...
May 08 05:32:02 steven-Latitude-E7240 amavis[8323]:   network name!
May 08 05:32:02 steven-Latitude-E7240 amavis[8323]: (failed).
May 08 05:32:02 steven-Latitude-E7240 systemd[1]: amavis.service: Control pro...
May 08 05:32:02 steven-Latitude-E7240 systemd[1]: Failed to start LSB: Starts...
May 08 05:32:02 steven-Latitude-E7240 systemd[1]: amavis.service: Unit entere...
May 08 05:32:02 steven-Latitude-E7240 systemd[1]: amavis.service: Failed with...
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package amavisd-new (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for systemd (229-4ubuntu17) ...
Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 amavisd-new
E: Sub-process /usr/bin/dpkg returned an error code (1)
steven@steven-Latitude-E7240:~$
```

---

### Post by #&amp;thj^% on 2017-05-08
Pretty Please use [**CODE **]("https://ubuntuforums.org/showthread.php?p=12776168#post12776168")Tags with long outputs...much easier on us the folks that try to help here.

Your hint here in>> The value of variable $...a fully qualified domai...You must explicitly ass...in /etc/amavis/conf.d/0...network name!

"$yourhostname" wasn't being set. A quick edit to /etc/amavis/conf.d/05-node_id so the hostname was set and away it went.

---

### Post by s9032g@comcast.net on 2017-05-09
Sorry but this is getting beyond me. What do I need to do?

---

### Post by #&amp;thj^% on 2017-05-09
It should be set in:
```
/etc/amavis/conf.d/50-user
```
Is this the first time using amavisd-new?
Forgive me here but will you even use this?
> **amavisd-new** is a high-performance interface between mailer (MTA) and content checkers: virus scanners, and/or SpamAssassin. It is written in Perl for maintainability, without paying a significant price for speed. It talks to MTA via (E)SMTP or LMTP, or by using helper programs. Best with Postfix, fine with dual-sendmail setup and Exim v4, works with sendmail/milter, or with any MTA as a SMTP relay. For Courier and qmail MTA integration there is a patch in the distributed package.
Here is what a fresh install would look like:
```
Name            : amavisd-new
Version         : 2.11.0-1
Description     : High-performance interface between mailer (MTA) and content
                  checkers
Architecture    : any
URL             : http://www.ijs.si/software/amavisd/
Licenses        : GPL
Groups          : None
Provides        : None
Depends On      : perl>=5.8.2  perl-archive-zip>=1.14  perl-convert-tnef
                  perl-convert-uulib>=1.4-5  perl-mime-tools
                  perl-mailtools>=1.58  perl-net-libidn  perl-net-server>=0.88
                  perl-io-socket-inet6  perl-io-stringy
                  perl-unix-syslog>=1.1-4  perl-mail-dkim>=0.31
                  perl-berkeleydb>=0.42  bzip2  gzip
Optional Deps   : perl-file-libmagic
                  arc: Decoder for: .arc
                  arj: Decoder for: .arj .exe
                  lrzip: Decoder for: .lrz [installed]
                  lz4: Decoder for: .lz4 [installed]
                  lzo: Decoder for: .lzo [installed]
                  p7zip: Decoder for: .7z [installed]
                  unrar: Decoder for: .rar [installed]
                  rpmextract: Decoder for: .rpm
Required By     : None
Optional For    : None
Conflicts With  : None
Replaces        : None
Installed Size  : 1927.00 KiB
Packager        : Unknown Packager
Build Date      : Tue 09 May 2017 03:08:47 PM MDT
Install Date    : Tue 09 May 2017 03:08:48 PM MDT
Install Reason  : Explicitly installed
Install Script  : Yes
Validated By    : None
Backup Files    :
UNMODIFIED    /etc/amavisd/amavisd.conf
UNMODIFIED    /etc/amavisd/amavisd-custom.conf


```
And These three are the changes needed or suited to your usage.... you just have to edit them by hand....IE Domain Name>> Hostname>>
If using a domain name use that.....if just using a hostname use that. (I hope this is clear or understandable)
```
Backup Files    :
UNMODIFIED    /etc/amavisd/amavisd.conf
UNMODIFIED    /etc/amavisd/amavisd-custom.conf
```

---

### Post by s9032g@comcast.net on 2017-05-12
Thanks, Sorry but I still don't understand. Based on all the terminal results that I sent earlier (I don't know what "code tags" are could you give a more specific suggestions for the necessary terminal commands?
Sorry to be a burden

---

### Post by #&amp;thj^% on 2017-05-12
No burden at all Glad you asked.:)
See this for the best set of instructions: [https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)

This may also help with amavisd-new for some understanding and suggestions/clues on setting it up:
[https://www.linuxbabe.com/mail-server/ubuntu-16-04-iredmail-server-installation](https://www.linuxbabe.com/mail-server/ubuntu-16-04-iredmail-server-installation)

---

### Post by s9032g@comcast.net on 2017-05-16
Seems that the first set of instructions has to do with "code tags". In the future I will refer to it. However I already sent my output this time.

The second suggestions have to do with email in Linux. I don't have that problem as my mail program is fine.
I still need to know how to solve my errors.

---

### Post by #&amp;thj^% on 2017-05-16
> **s9032g@comcast.net said:**
> Seems that the first set of instructions has to do with "code tags". In the future I will refer to it. However I already sent my output this time.

The second suggestions have to do with email in Linux. I don't have that problem as my mail program is fine.
_**I still need to know how to solve my errors.**_
That was in response to:
> (I don't know what "code tags" are could you give a more specific suggestions for the necessary terminal commands?
Sorry to be a burden

Well as it seems, we are just talking past each other here (And no offense meant) I would simply uninstall amavisd-new.
As it's primary service is for severs (IE:mail severs or just daily severs)
See my post #2 for a clean uninstall.
And after that is complete run:
```
sudo apt update
sudo apt upgrade
```
All should be good now...if not post back the errors from the terminal using the code tags.
Thanks

---

### Post by s9032g@comcast.net on 2017-06-10
I have found in bug reports that this is an unresolved problem that is being worked on.

---

