---
title: "Error Code (1) Terminal"
date: 2014-09-09
forum: General Help
---

### Post by George_Baskharon on 2014-09-09
Hi, this is my first post and i'm hoping i'm in the right place. Recently i've been getting this error code every time I try to upgrade or repair or even install new packages.

Could anyone help me with this ? Thanks.


```
george@BaskharonPC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: Perl may be unconfigured (Can't locate IPC/Open2.pm in @INC (you may need to install the IPC::Open2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/ConfModule.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/ConfModule.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
Compilation failed in require at (eval 1) line 8.
BEGIN failed--compilation aborted at (eval 1) line 8.
) -- aborting
Setting up libpam-systemd:amd64 (204-5ubuntu20.6) ...
Can't locate IPC/Open2.pm in @INC (you may need to install the IPC::Open2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/ConfModule.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/ConfModule.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
Compilation failed in require at /usr/share/debconf/frontend line 8.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 8.
dpkg: error processing package libpam-systemd:amd64 (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up man-db (2.6.7.1-1) ...
Can't locate IPC/Open2.pm in @INC (you may need to install the IPC::Open2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/ConfModule.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/ConfModule.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
Compilation failed in require at /usr/share/debconf/frontend line 8.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 8.
dpkg: error processing package man-db (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up update-notifier-common (0.154.1) ...
Can't locate IPC/Open2.pm in @INC (you may need to install the IPC::Open2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/ConfModule.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/ConfModule.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
Compilation failed in require at /usr/bin/debconf-communicate line 8.
BEGIN failed--compilation aborted at /usr/bin/debconf-communicate line 8.
Traceback (most recent call last):
File "/usr/lib/update-notifier/package-data-downloader", line 301, in <module>
process_download_requests()
File "/usr/lib/update-notifier/package-data-downloader", line 224, in process_download_requests
db = debconf.DebconfCommunicator('update-notifier')
File "/usr/lib/python2.7/dist-packages/debconf.py", line 129, in __init__
write=self.dccomm.stdin)
File "/usr/lib/python2.7/dist-packages/debconf.py", line 50, in __init__
self.setUp(title)
File "/usr/lib/python2.7/dist-packages/debconf.py", line 53, in setUp
self.version = self.version(2)
File "/usr/lib/python2.7/dist-packages/debconf.py", line 62, in <lambda>
lambda *args, **kw: self.command(command, *args, **kw))
File "/usr/lib/python2.7/dist-packages/debconf.py", line 83, in command
status = int(status)
ValueError: invalid literal for int() with base 10: ''
dpkg: error processing package update-notifier-common (--configure):
subprocess installed post-installation script returned error exit status 1
Setting up cups (1.7.2-0ubuntu1.2) ...
Can't locate IPC/Open2.pm in @INC (you may need to install the IPC::Open2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/ConfModule.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/ConfModule.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
Compilation failed in require at /usr/share/debconf/frontend line 8.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 8.
dpkg: error processing package cups (--configure):
subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of flashplugin-installer:
flashplugin-installer depends on update-notifier-common (>= 0.119ubuntu2); however:
Package update-notifier-common is not configured yet.


dpkg: error processing package flashplugin-installer (--configure):
dependency problems - leaving unconfigured
Setting up cups-bsd (1.7.2-0ubuntu1.2) ...
No apport report written because MaxReports is reached already
Can't locate IPC/Open2.pm in @INC (you may need to install the IPC::Open2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/ConfModule.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/ConfModule.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
Compilation failed in require at /usr/share/debconf/frontend line 8.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 8.
dpkg: error processing package cups-bsd (--configure):
subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Errors were encountered while processing:
libpam-systemd:amd64
man-db
update-notifier-common
cups
flashplugin-installer
cups-bsd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

