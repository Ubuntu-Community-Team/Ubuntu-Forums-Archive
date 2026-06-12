---
title: "Can't use apt/aptitude since it crashed during an uninstall!"
date: 2007-04-18
forum: General Help
---

### Post by Dragonmantank on 2007-04-18
I installed psad and then tried to remove it, deciding to wait until I got the machine all set up before I started trying to work with Bastille. Ever since then, I get this error whenever I try to do anything with apt or aptitude:

```
 Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  linux-image-server 
The following packages will be REMOVED:
  psad 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 1745kB will be freed.
Writing extended state information... Done
(Reading database ... 18569 files and directories currently installed.)
Removing psad ...
find: /var/run/psad/: No such file or directory
dpkg: error processing psad (--remove):
 subprocess pre-removal script returned error exit status 1
Starting Port Scan Attack Detector and associated daemons: Can't locate Unix/Syslog.pm in @INC (@INC contains: /usr/lib/psad /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl5/Psad.pm line 22.
BEGIN failed--compilation aborted at /usr/lib/perl5/Psad.pm line 22.
Compilation failed in require at /usr/sbin/psad line 135.
BEGIN failed--compilation aborted at /usr/sbin/psad line 135.
invoke-rc.d: initscript psad, action "start" failed.
Errors were encountered while processing:
 psad
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

I've tried to clean, autoclean, remove it again, purge, etc, but I can't do anything on this machine regarding apt anytmore. What do I do?

---

### Post by bwhite82 on 2007-04-18
Try these two commands:
> 
apt-get install --fix-missing
apt-get install -f

---

### Post by Dragonmantank on 2007-04-18
apt-get install --fix-missing -f worked just fine. Thanks!

---

### Post by heiNey on 2008-04-15
sorry to bring up an old thread, but im having a similar problem...except mine is saying it cant find mail...ive tried clean and autoremove, etc...but cannot seem to remove psad.  anyone know what's going on?

```

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up psad (2.0.7-1) ...
Starting Port Scan Attack Detector and associated daemons: [*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 8564.
invoke-rc.d: initscript psad, action "start" failed.
dpkg: error processing psad (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 psad
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by kesman on 2008-04-15
Maybe try
```

sudo apt-get install --reinstall psad

```
if this doesn't work, try
```

sudo apt-get purge psad
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install psad

```

---

### Post by heiNey on 2008-04-15
doing the first command gives me:

```

$ sudo apt-get install --reinstall psad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up psad (2.0.7-1) ...
Starting Port Scan Attack Detector and associated daemons: [*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 8564.
invoke-rc.d: initscript psad, action "start" failed.
dpkg: error processing psad (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 psad
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

the other commands give:

```

$ sudo apt-get purge psad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnetwork-ipv4addr-perl libdate-calc-perl libcarp-clan-perl
  libunix-syslog-perl libbit-vector-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  psad*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2802kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117323 files and directories currently installed.)
Removing psad ...
find: /var/run/psad/: No such file or directory
dpkg: error processing psad (--purge):
 subprocess pre-removal script returned error exit status 1
Starting Port Scan Attack Detector and associated daemons: [*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 8564.
invoke-rc.d: initscript psad, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 psad
E: Sub-process /usr/bin/dpkg return$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```
```

$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```
```

$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up psad (2.0.7-1) ...
Starting Port Scan Attack Detector and associated daemons: [*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 8564.
invoke-rc.d: initscript psad, action "start" failed.
dpkg: error processing psad (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 psad
E: Sub-process /usr/bin/dpkg returned an error code (1)
ed an error code (1)

```

```

$ sudo apt-get install psad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
psad is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up psad (2.0.7-1) ...
Starting Port Scan Attack Detector and associated daemons: [*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 8564.
invoke-rc.d: initscript psad, action "start" failed.
dpkg: error processing psad (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 psad
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i dont really want to reinstall it, but i did that last command to see if a reinstall would allow a removal...doesnt seem to work

---

### Post by kesman on 2008-04-16
> Starting Port Scan Attack Detector and associated daemons:[*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 8564.
invoke-rc.d: initscript psad, action "start" failed.

Could you please post the contents of that line in that file please or try to run:
```

sudo dpkg-reconfigure psad

```

---

### Post by heiNey on 2008-04-16
that seems to have worked...thanks

---

