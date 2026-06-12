---
title: "Trying to install qbittorrent"
date: 2019-12-21
forum: General Help
---

### Post by jgw on 2019-12-21
I consideed putting this in installations but I dawned on me that was probably reserved for ubuntu stuff so I put it here.  If I was wrong please move it to wherever its supposed to be.

I thought I would try another torrent program (qbittorrent).  I failed.  Below is a record of what I did.

```

qbittorrent install directions address:
https://www.linuxbabe.com/ubuntu/install-qbittorrent-ubuntu-18-04-desktop-server

Commands:
1  greg@movies:~$ sudo add-apt-repository ppa:qbittorrent-team/qbittorrent-stable
2  greg@movies:~$ sudo apt install qbittorrent
3  greg@movies:~$ sudo add-apt-repository ppa:qbittorrent-team/qbittorrent-stable
4  greg@movies:~$ sudo apt install qbittorrent-nox
5  greg@movies:~$ sudo adduser --system --group qbittorrent-nox
6  greg@movies:~$ sudo adduser greg qbittorrent-nox
7  greg@movies:~$ sudo nano /etc/systemd/system/qbittorrent-nox.service
8  greg@movies:~$ sudo gedit /etc/systemd/system/qbittorrent-nox.service (change 8080 to 8079)
9  greg@movies:~$ sudo systemctl start qbittorrent-nox
10 greg@movies:~$ sudo systemctl daemon-reload
11 greg@movies:~$ sudo systemctl enable qbittorrent-nox
12 greg@movies:~$ systemctl status qbittorrent-nox

Record of Installation:
1  greg@movies:~$ sudo add-apt-repository ppa:qbittorrent-team/qbittorrent-stable
[sudo] password for greg: 
 Packages for the stable series of qBittorrent
 More info: https://launchpad.net/~qbittorrent-team/+archive/ubuntu/qbittorrent-stable
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 https://download.mono-project.com/repo/ubuntu stable-bionic InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Get:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Hit:5 http://apt.sonarr.tv master InRelease                                    
Hit:6 http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu bionic InRelease
Hit:7 http://archive.canonical.com/ubuntu bionic InRelease                     
Hit:8 http://archive.canonical.com bionic InRelease                            
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Hit:10 http://ppa.launchpad.net/jcfp/nobetas/ubuntu bionic InRelease           
Hit:11 http://ppa.launchpad.net/jcfp/ppa/ubuntu bionic InRelease               
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [817 kB]
Hit:13 http://ppa.launchpad.net/jcfp/sab-addons/ubuntu bionic InRelease        
Get:14 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [38.5 kB]
Hit:15 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic InRelease
Get:16 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [41.5 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [625 kB]
Get:18 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 128x128 Icons [97.7 kB]
Get:19 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu bionic InRelease [15.9 kB]
Get:20 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [42.1 kB]
Get:21 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [16.4 kB]
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [116 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [295 kB]
Get:24 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 128x128 Icons [181 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [73.8 kB]
Hit:26 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu bionic InRelease          
Get:27 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [143 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 128x128 Icons [365 kB]
Get:29 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Hit:30 http://ppa.launchpad.net/transmissionbt/ppa/ubuntu bionic InRelease     
Get:31 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [997 kB]
Hit:32 http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu bionic InRelease
Hit:33 http://ppa.launchpad.net/yg-jensge/shotwell/ubuntu bionic InRelease     
Get:34 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1,033 kB]
Get:35 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu bionic/main i386 Packages [2,740 B]
Get:36 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu bionic/main amd64 Packages [2,740 B]
Get:37 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [264 kB]
Get:38 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [194 kB]
Get:39 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu bionic/main Translation-en [1,388 B]
Get:40 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [430 kB]
Get:41 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 128x128 Icons [973 kB]
Get:42 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:43 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,980 B]
Fetched 7,031 kB in 8s (907 kB/s)                                              
Reading package lists... Done

2 greg@movies:~$ sudo apt install qbittorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgegl-0.3-0 libjs-jquery-metadata libjs-jquery-tablesorter
  libnunit-cil-dev libnunit-console-runner2.6.3-cil
  libnunit-core-interfaces2.6.3-cil libnunit-core2.6.3-cil
  libnunit-framework2.6.3-cil libnunit-mocks2.6.3-cil libnunit-util2.6.3-cil
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libtorrent-rasterbar10
Suggested packages:
  libtorrent-rasterbar-dbg qbittorrent-dbg
The following NEW packages will be installed:
  libtorrent-rasterbar10 qbittorrent
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 6,492 kB of archives.
After this operation, 11.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu bionic/main amd64 libtorrent-rasterbar10 amd64 1.2.3+git20191216.68196dceae-1ppa1~18.04 [939 kB]
Get:2 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu bionic/main amd64 qbittorrent amd64 1:4.2.0.99~201912180418-6819-118af03~ubuntu18.04.1 [5,553 kB]
Fetched 6,492 kB in 8s (848 kB/s)                                              
Selecting previously unselected package libtorrent-rasterbar10.
(Reading database ... 298395 files and directories currently installed.)
Preparing to unpack .../libtorrent-rasterbar10_1.2.3+git20191216.68196dceae-1ppa1~18.04_amd64.deb ...
Unpacking libtorrent-rasterbar10 (1.2.3+git20191216.68196dceae-1ppa1~18.04) ...
Selecting previously unselected package qbittorrent.
Preparing to unpack .../qbittorrent_1%3a4.2.0.99~201912180418-6819-118af03~ubuntu18.04.1_amd64.deb ...
Unpacking qbittorrent (1:4.2.0.99~201912180418-6819-118af03~ubuntu18.04.1) ...
Setting up libtorrent-rasterbar10 (1.2.3+git20191216.68196dceae-1ppa1~18.04) ...
Setting up qbittorrent (1:4.2.0.99~201912180418-6819-118af03~ubuntu18.04.1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...

3 greg@movies:~$ sudo add-apt-repository ppa:qbittorrent-team/qbittorrent-stable
 Packages for the stable series of qBittorrent
 More info: https://launchpad.net/~qbittorrent-team/+archive/ubuntu/qbittorrent-stable
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 https://download.mono-project.com/repo/ubuntu stable-bionic InRelease
Hit:2 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:4 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Hit:5 http://apt.sonarr.tv master InRelease                                    
Hit:6 http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu bionic InRelease
Hit:7 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease           
Hit:8 http://archive.canonical.com/ubuntu bionic InRelease                     
Hit:9 http://archive.canonical.com bionic InRelease                            
Hit:10 http://ppa.launchpad.net/jcfp/nobetas/ubuntu bionic InRelease           
Hit:11 http://ppa.launchpad.net/jcfp/ppa/ubuntu bionic InRelease              
Hit:12 http://ppa.launchpad.net/jcfp/sab-addons/ubuntu bionic InRelease       
Hit:13 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic InRelease
Hit:14 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu bionic InRelease
Hit:15 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu bionic InRelease          
Hit:16 http://ppa.launchpad.net/transmissionbt/ppa/ubuntu bionic InRelease
Hit:17 http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu bionic InRelease
Hit:18 http://ppa.launchpad.net/yg-jensge/shotwell/ubuntu bionic InRelease     
Reading package lists... Done 

4 greg@movies:~$ sudo apt install qbittorrent-nox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgegl-0.3-0 libjs-jquery-metadata libjs-jquery-tablesorter
  libnunit-cil-dev libnunit-console-runner2.6.3-cil
  libnunit-core-interfaces2.6.3-cil libnunit-core2.6.3-cil
  libnunit-framework2.6.3-cil libnunit-mocks2.6.3-cil libnunit-util2.6.3-cil
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  qbittorrent-dbg
The following NEW packages will be installed:
  qbittorrent-nox
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 4,973 kB of archives.
After this operation, 6,491 kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu bionic/main amd64 qbittorrent-nox amd64 1:4.2.0.99~201912180418-6819-118af03~ubuntu18.04.1 [4,973 kB]
Fetched 4,973 kB in 6s (904 kB/s)            
Selecting previously unselected package qbittorrent-nox.
(Reading database ... 298438 files and directories currently installed.)
Preparing to unpack .../qbittorrent-nox_1%3a4.2.0.99~201912180418-6819-118af03~ubuntu18.04.1_amd64.deb ...
Unpacking qbittorrent-nox (1:4.2.0.99~201912180418-6819-118af03~ubuntu18.04.1) ...
Setting up qbittorrent-nox (1:4.2.0.99~201912180418-6819-118af03~ubuntu18.04.1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...

5 greg@movies:~$ sudo adduser --system --group qbittorrent-nox
Adding system user `qbittorrent-nox' (UID 127) ...
Adding new group `qbittorrent-nox' (GID 133) ...
Adding new user `qbittorrent-nox' (UID 127) with group `qbittorrent-nox' ...
Creating home directory `/home/qbittorrent-nox' ...

6 greg@movies:~$ sudo adduser greg qbittorrent-nox
Adding user `greg' to group `qbittorrent-nox' ...
Adding user greg to group qbittorrent-nox
Done.

7 greg@movies:~$ sudo nano /etc/systemd/system/qbittorrent-nox.service
8 greg@movies:~$ sudo gedit /etc/systemd/system/qbittorrent-nox.service

** (gedit:17095): WARNING **: 11:16:11.911: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported

** (gedit:17095): WARNING **: 11:16:11.912: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:17095): WARNING **: 11:16:19.201: Set document metadata failed: Setting attribute metadata::gedit-position not supported

9 greg@movies:~$ sudo systemctl start qbittorrent-nox

10 greg@movies:~$ sudo systemctl daemon-reload

11 greg@movies:~$ sudo systemctl enable qbittorrent-nox
Created symlink /etc/systemd/system/multi-user.target.wants/qbittorrent-nox.service &#8594; /etc/systemd/system/qbittorrent-nox.service.

12 greg@movies:~$ systemctl status qbittorrent-nox
&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor 
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 1min 41
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off tim
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart jo
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeat
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result '
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Clie
lines 1-11/11 (END)

&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor p
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 1min 41s
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off time
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart job
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeate
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result 'e
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Clien
~
lines 1-11/11 (END)

&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor pres
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 1min 41s ag
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off time ov
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart job, r
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeated t
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result 'exit
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Client.
~
lines 1-11/11 (END)

&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor preset: ena
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 1min 41s ago
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off time over, sch
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart job, restart 
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeated too quic
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result 'exit-code'.
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Client.
~
lines 1-11/11 (END)

&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 1min 41s ago
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off time over, scheduling resta
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart job, restart counter is at
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeated too quickly.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result 'exit-code'.
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Client.
~
lines 1-11/11 (END)

&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 1min 41s ago
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off time over, scheduling restart.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart job, restart counter is at 5.
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeated too quickly.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result 'exit-code'.
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Client.
~
lines 1-11/11 (END)

&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 1min 41s ago
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off time over, scheduling restart.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart job, restart counter is at 5.
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeated too quickly.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result 'exit-code'.
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Client.
~
lines 1-11/11 (END)

&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 1min 41s ago
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off time over, scheduling restart.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart job, restart counter is at 5.
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeated too quickly.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result 'exit-code'.
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Client.
~
lines 1-11/11 (END)

&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 1min 41s ago
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off time over, scheduling restart.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart job, restart counter is at 5.
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeated too quickly.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result 'exit-code'.
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Client.
~
lines 1-11/11 (END)

&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 1min 41s ago
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off time over, scheduling restart.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart job, restart counter is at 5.
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeated too quickly.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result 'exit-code'.
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Client.
~

lines 1-11/11 (END)

&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 1min 41s ago
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off time over, scheduling restart.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart job, restart counter is at 5.
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeated too quickly.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result 'exit-code'.
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Client.
~
lines 1-11/11 (END)

**  I went to system monitor and found that qbittorrent was running.  I stopped that and then:
greg@movies:~$ sudo systemctl enable qbittorrent-nox  (started up qbittorrent-nox)
greg@movies:~$ systemctl status qbittorrent-nox       (checked status again - enabled but failed)
&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 50min ago
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off time over, scheduling restar
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart job, restart counter is at 
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeated too quickly.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result 'exit-code'.
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Client.
lines 1-11/11 (END)

```

After the failure this is what I did:
```

**  I went to system monitor and found that qbittorrent was running.  I stopped that and then:
greg@movies:~$ sudo systemctl enable qbittorrent-nox  (started up qbittorrent-nox)
greg@movies:~$ systemctl status qbittorrent-nox       (checked status again - enabled but failed)
&#9679; qbittorrent-nox.service - qBittorrent Command Line Client
   Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2019-12-21 11:17:16 PST; 50min ago
 Main PID: 17340 (code=exited, status=1/FAILURE)

Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Service hold-off time over, scheduling restar
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Scheduled restart job, restart counter is at 
Dec 21 11:17:16 movies systemd[1]: Stopped qBittorrent Command Line Client.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Start request repeated too quickly.
Dec 21 11:17:16 movies systemd[1]: qbittorrent-nox.service: Failed with result 'exit-code'.
Dec 21 11:17:16 movies systemd[1]: Failed to start qBittorrent Command Line Client.
lines 1-11/11 (END)
```

Thank you........................

---

### Post by crip720 on 2019-12-21
Any reason using the ppa and not installing from ubuntu itself(software store or apt)?   Just re-read your post, you did use apt.  Did you purge the ppa?

---

### Post by jgw on 2019-12-21
Thank you for the reply.

I did it this way because, at [https://www.linuxbabe.com/ubuntu/install-qbittorrent-ubuntu-18-04-desktop-server](https://www.linuxbabe.com/ubuntu/install-qbittorrent-ubuntu-18-04-desktop-server) they said that the one available from ubuntu was not the latest and greatest.  On reflection I probably should have done that but, now, I am in the middle of this and should probably finish up with it.

---

### Post by crip720 on 2019-12-21
Mine is 1.4.7.  I would try to purge ppa and apt qbittorrent and try again.

---

### Post by jgw on 2019-12-27
Just for the heck of it I thought I would check my system monitory for qbittorrent - it was there! (apparently running).  So, it automatically starts when it boots.  What is there is just plain qbittorrent.  So, I brought it up from applications.  The program's font its so small its really hard to read.  Told me that the port was already being used.  I think that is because of my setting up of qbittorrent-nox stuff although I don't think that is running (not in system monitor it is reserving the port.

I also tried to have couchpotato deal with qbittorrent.  I got:
```
12-27 11:20:55 ERROR[ couchpotato.api] Failed doing api request "download.qbittorrent.test": Traceback (most recent call last): File "/home/greg/CouchPotatoServer/couchpotato/api.py", line 36, in run_handler res = api[route](**kwargs) File "/home/greg/CouchPotatoServer/couchpotato/core/_base/downloader/main.py", line 179, in _test t = self.test() File "/home/greg/CouchPotatoServer/couchpotato/core/downloaders/qbittorrent_.py", line 46, in test return self.connect() File "/home/greg/CouchPotatoServer/couchpotato/core/downloaders/qbittorrent_.py", line 30, in connect self.qb.logout() File "/home/greg/CouchPotatoServer/libs/qbittorrent/client.py", line 108, in logout response = self._get('logout') File "/home/greg/CouchPotatoServer/libs/qbittorrent/client.py", line 34, in _get return self._request(endpoint, 'get', **kwargs) File "/home/greg/CouchPotatoServer/libs/qbittorrent/client.py", line 62, in _request raise LoginRequired LoginRequired: Please login first. 
```

There was some reference to logging in but there is nothing in their gui to reference that so its a dead end?

Now my question is a bit more simple.  What do I do now?  I suspect I have to get rid of the qbittorrent-nox but have no  idea how.  

Anyway, any thoughts would be appreciated - thank you.........................

---

### Post by jgw on 2020-01-04
I thought I would make another run at transmission and its now working just fine with couchpotato.  qbittorrent may be a better product but I think I will abandon it.  I have it installed but the nox thing confuses althought the plain qbittorrent seems to be almost working (have it up in my browser, etc. but its just not doing anything.  The fonts, incidentally, suddenly got bigger and readable.  I also found some fairly recent postings on getting it going but I am lazy and transmission is now working fine so..............

Thank you for the replies....................   (can't mark this as solved as I have been told it must be solved first and this is not)

---

### Post by mastablasta on 2020-01-06
if this is on server, then yes transmission is the one to go with.

if it is for desktop, then qbitorrent works fine. i installed the one from the repositories. latest software or hardware is not always a good choice and it often means that it is not tested well.

---

### Post by jgw on 2020-01-06
Thank you for the reply.

I have always been confused as to what a desktop is and what a server is.  When doing a computer I simply download ubuntu, put it on a cd, and then install it.  I just went to ubuntu to see what was available for download and it had two, one for the desktop and one for a server.  Up to now I just downloaded ubuntu.  I suspect I probably have a desktop as I have never even bothered to setup a network between my computers (I have 6 computers, one is for windows 10 (my wife's computer) and all the rest are ubuntu.  Right now there are 4 of the computers running. (including this one.  I can see them when I click on 'other' in files)

---

### Post by jgw on 2020-01-20
I went back to transmission and its running just fine.  That being the case I will ignore bittorrent (uninstall it) and just stick with what I have working right now.  My apologies for this topic as it was unnecessary and time I am sure could have been better used.

I can't mark this as solved - wish there was something I could mark this, something like "waste of time" or similar.

---

### Post by mastablasta on 2020-01-21
click "thread tools" in the first thread (upper right corner in grey area) and select "mark this thread as solved".

there are two editions one is desktop (which has graphical user interface) and the other one is server which is meant for "headless" computers (i.e. no monitor) and comes with command line only interface. one can install transmission on server and access it through web. i think it is the same with desktop version, but you need to open the port. then you can set a download  from the other side of the world. :-)

---

