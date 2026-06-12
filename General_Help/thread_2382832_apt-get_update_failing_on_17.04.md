---
title: "apt-get update failing on 17.04"
date: 2018-01-17
forum: General Help
---

### Post by amresh3 on 2018-01-17
Hi,

I am trying to do an apt-get update on my Ubuntu 17.04 laptop and it is failing on the Ubuntu URLs. I can reach the URLs using command-line and the browser, but don't know why apt-get update is failing. Here is the output (below).

Laptop was recently installed with 17.04.

```
foo@foobar:~$ sudo apt-get update
[sudo] password for foo: 
Hit:1 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                           
Ign:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty InRelease                                                              
Ign:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease    
Hit:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Hit:6 [https://deb.nodesource.com/node_9.x](https://deb.nodesource.com/node_9.x) zesty InRelease                
Ign:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates InRelease        
Err:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security Release           
  404  Not Found [IP: 91.189.91.23 80]
Ign:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-backports InRelease
Err:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty Release
  404  Not Found [IP: 91.189.91.26 80]
Err:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates Release
  404  Not Found [IP: 91.189.91.26 80]
Err:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-backports Release
  404  Not Found [IP: 91.189.91.26 80]
Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu zesty-backports Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
foo@foobar:~$ echo $?
100
foo@foobar:~$
```

---

### Post by ian-weisser on 2018-01-17
17.04 reached End of Life last week.
The 17.04 repositories have been closed and withdrawn. That is why you cannot reach them.

Time for you to upgrade to 17.10.

---

### Post by DuckHook on 2018-01-17
Instructions for upgrading EoL versions: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by fluffy12 on 2018-01-21
> **DuckHook said:**
> Instructions for upgrading EoL versions: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Unfortunately those instructions are completely wrong and worthless for 17.04 to 17.10.  Because the repos are gone, neither aptitude nor apt-get paths work.  Pray that you were fairly up to date and try do-release-upgrade.

---

### Post by QIII on 2018-01-21
@fluffy12:

Are you saying that ```
http://old-releases.ubuntu.com/ubuntu/dists/zesty
``` does not exist?

If it doesn't it may not yet have been prepared.  That would be worth a mention on launchpad.

---

### Post by howefield on 2018-01-21
> **fluffy12 said:**
> Unfortunately those instructions are completely wrong and worthless for 17.04 to 17.10.  Because the repos are gone, neither aptitude nor apt-get paths work.  Pray that you were fairly up to date and try do-release-upgrade.

Instructions seem valid enough to me..

Here is the output using the page to upgrade 17.04 to 17.10  :

Initial errors out due to repositories having been moved to old-releases.
```
hugh@zesty-laptop:~$  sudo apt update
[sudo] password for hugh: 
Get:1 http://archive.canonical.com/ubuntu zesty InRelease [10.2 kB]
Ign:2 http://gb.archive.ubuntu.com/ubuntu zesty InRelease                       
Get:3 http://ppa.launchpad.net/nextcloud-devs/client/ubuntu zesty InRelease [15.9 kB]
Ign:4 http://gb.archive.ubuntu.com/ubuntu zesty-updates InRelease                    
Ign:5 http://gb.archive.ubuntu.com/ubuntu zesty-backports InRelease
Err:6 http://gb.archive.ubuntu.com/ubuntu zesty Release
  404  Not Found [IP: 2001:67c:1360:8001::17 80]
Err:7 http://gb.archive.ubuntu.com/ubuntu zesty-updates Release
  404  Not Found [IP: 2001:67c:1360:8001::17 80]
Err:8 http://gb.archive.ubuntu.com/ubuntu zesty-backports Release
  404  Not Found [IP: 2001:67c:1360:8001::17 80]
Get:9 http://ppa.launchpad.net/nextcloud-devs/client/ubuntu zesty/main i386 Packages [2,064 B]
Get:10 http://ppa.launchpad.net/nextcloud-devs/client/ubuntu zesty/main amd64 Packages [2,056 B]
Ign:11 http://security.ubuntu.com/ubuntu zesty-security InRelease
Err:12 http://security.ubuntu.com/ubuntu zesty-security Release
  404  Not Found [IP: 2001:67c:1360:8001::17 80]
Reading package lists... Done
E: The repository 'http://gb.archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```
Change repositories to point to..
```
hugh@zesty-laptop:~$  sudo nano /etc/apt/sources.list
```
```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ zesty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ zesty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ zesty-security main restricted universe multiverse
```
Update
```
hugh@zesty-laptop:~$  sudo apt update
Get:1 http://old-releases.ubuntu.com/ubuntu zesty InRelease [243 kB]
Hit:2 http://ppa.launchpad.net/nextcloud-devs/client/ubuntu zesty InRelease
Get:3 http://old-releases.ubuntu.com/ubuntu zesty-updates InRelease [89.2 kB]
Get:4 http://old-releases.ubuntu.com/ubuntu zesty-security InRelease [89.2 kB]
Get:5 http://old-releases.ubuntu.com/ubuntu zesty/main i386 Packages [1,204 kB]
Get:6 http://old-releases.ubuntu.com/ubuntu zesty/main amd64 Packages [1,207 kB]
Get:7 http://old-releases.ubuntu.com/ubuntu zesty/main Translation-en_GB [495 kB]
Get:8 http://old-releases.ubuntu.com/ubuntu zesty/main Translation-en [577 kB]
Get:9 http://old-releases.ubuntu.com/ubuntu zesty/main amd64 DEP-11 Metadata [536 kB]
Get:10 http://old-releases.ubuntu.com/ubuntu zesty/restricted amd64 Packages [8,672 B]
Get:11 http://old-releases.ubuntu.com/ubuntu zesty/restricted i386 Packages [8,648 B]
Get:12 http://old-releases.ubuntu.com/ubuntu zesty/restricted Translation-en_GB [2,464 B]
Get:13 http://old-releases.ubuntu.com/ubuntu zesty/restricted Translation-en [2,724 B]
Get:14 http://old-releases.ubuntu.com/ubuntu zesty/restricted amd64 DEP-11 Metadata [185 B]
Get:15 http://old-releases.ubuntu.com/ubuntu zesty/universe amd64 Packages [8,068 kB]
Get:16 http://old-releases.ubuntu.com/ubuntu zesty/universe i386 Packages [8,037 kB]
Get:17 http://old-releases.ubuntu.com/ubuntu zesty/universe Translation-en [4,671 kB]                                                      
Get:18 http://old-releases.ubuntu.com/ubuntu zesty/universe Translation-en_GB [4,116 kB]                                                   
Get:19 http://old-releases.ubuntu.com/ubuntu zesty/universe amd64 DEP-11 Metadata [2,713 kB]                                               
Get:20 http://old-releases.ubuntu.com/ubuntu zesty/multiverse i386 Packages [147 kB]                                                       
Get:21 http://old-releases.ubuntu.com/ubuntu zesty/multiverse amd64 Packages [154 kB]                                                      
Get:22 http://old-releases.ubuntu.com/ubuntu zesty/multiverse Translation-en [109 kB]                                                      
Get:23 http://old-releases.ubuntu.com/ubuntu zesty/multiverse Translation-en_GB [85.7 kB]                                                  
Get:24 http://old-releases.ubuntu.com/ubuntu zesty/multiverse amd64 DEP-11 Metadata [43.3 kB]                                              
Get:25 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 Packages [257 kB]                                                    
Get:26 http://old-releases.ubuntu.com/ubuntu zesty-updates/main i386 Packages [253 kB]                                                     
Get:27 http://old-releases.ubuntu.com/ubuntu zesty-updates/main Translation-en [118 kB]                                                    
Get:28 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 DEP-11 Metadata [55.2 kB]                                            
Get:29 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted amd64 Packages [2,460 B]                                             
Get:30 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted i386 Packages [2,452 B]                                              
Get:31 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted Translation-en [1,352 B]                                             
Get:32 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted amd64 DEP-11 Metadata [193 B]                                        
Get:33 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe amd64 Packages [170 kB]                                                
Get:34 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe i386 Packages [170 kB]                                                 
Get:35 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe Translation-en [95.6 kB]                                               
Get:36 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe amd64 DEP-11 Metadata [203 kB]                                         
Get:37 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse amd64 Packages [11.8 kB]                                             
Get:38 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse i386 Packages [12.0 kB]                                              
Get:39 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse Translation-en [6,280 B]                                             
Get:40 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse amd64 DEP-11 Metadata [5,840 B]                                      
Get:41 http://old-releases.ubuntu.com/ubuntu zesty-security/main amd64 Packages [180 kB]                                                   
Get:42 http://old-releases.ubuntu.com/ubuntu zesty-security/main i386 Packages [176 kB]                                                    
Get:43 http://old-releases.ubuntu.com/ubuntu zesty-security/main Translation-en [82.0 kB]                                                  
Get:44 http://old-releases.ubuntu.com/ubuntu zesty-security/main amd64 DEP-11 Metadata [15.1 kB]                                           
Get:45 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted i386 Packages [2,452 B]                                             
Get:46 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted amd64 Packages [2,460 B]                                            
Get:47 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted Translation-en [1,352 B]                                            
Get:48 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted amd64 DEP-11 Metadata [192 B]                                       
Get:49 http://old-releases.ubuntu.com/ubuntu zesty-security/universe amd64 Packages [91.6 kB]                                              
Get:50 http://old-releases.ubuntu.com/ubuntu zesty-security/universe i386 Packages [91.7 kB]                                               
Get:51 http://old-releases.ubuntu.com/ubuntu zesty-security/universe Translation-en [59.6 kB]                                              
Get:52 http://old-releases.ubuntu.com/ubuntu zesty-security/universe amd64 DEP-11 Metadata [27.4 kB]                                       
Get:53 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse amd64 Packages [2,976 B]                                            
Get:54 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse i386 Packages [3,132 B]                                             
Get:55 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse Translation-en [1,744 B]                                            
Get:56 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse amd64 DEP-11 Metadata [208 B]                                       
Fetched 34.7 MB in 17s (2,022 kB/s)                                                                                                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
25 packages can be upgraded. Run 'apt list --upgradable' to see them.
```
Upgrade existing packages
```
hugh@zesty-laptop:~$  sudo apt upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apport apport-gtk distro-info-data firefox firefox-locale-en gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0 libgweather-3-6
  libgweather-common libjavascriptcoregtk-4.0-18 libnextcloudsync0 libpoppler-glib8 libpoppler-qt5-1 libpoppler64 libwebkit2gtk-4.0-37
  libxml2 nextcloud-client nextcloud-client-l10n nplan poppler-utils python3-apport python3-problem-report resolvconf snapd squashfs-tools
25 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 74.1 MB of archives.
After this operation, 2,238 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 distro-info-data all 0.33ubuntu0.4 [4,392 B]
Get:2 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 resolvconf all 1.79ubuntu4.1 [51.5 kB]
Get:3 http://ppa.launchpad.net/nextcloud-devs/client/ubuntu zesty/main amd64 nextcloud-client-l10n all 2.3.3-20171224.060956~zesty1 [362 kB]
Get:4 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 libxml2 amd64 2.9.4+dfsg1-2.2ubuntu0.3 [698 kB]
Get:5 http://ppa.launchpad.net/nextcloud-devs/client/ubuntu zesty/main amd64 nextcloud-client amd64 2.3.3-20171224.060956~zesty1 [1,082 kB]
Get:6 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 nplan amd64 0.32~17.04.1 [40.1 kB]
Get:7 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 python3-problem-report all 2.20.4-0ubuntu4.10 [9,928 B]
Get:8 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 python3-apport all 2.20.4-0ubuntu4.10 [79.5 kB]
Get:9 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 apport all 2.20.4-0ubuntu4.10 [122 kB]
Get:10 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 apport-gtk all 2.20.4-0ubuntu4.10 [9,522 B]
Get:11 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 firefox amd64 57.0.4+build1-0ubuntu0.17.04.1 [44.0 MB]
Get:12 http://ppa.launchpad.net/nextcloud-devs/client/ubuntu zesty/main amd64 libnextcloudsync0 amd64 2.3.3-20171224.060956~zesty1 [417 kB]
Get:13 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 firefox-locale-en amd64 57.0.4+build1-0ubuntu0.17.04.1 [692 kB]      
Get:14 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 libwebkit2gtk-4.0-37 amd64 2.18.5-0ubuntu0.17.04.1 [11.2 MB]         
Get:15 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 libjavascriptcoregtk-4.0-18 amd64 2.18.5-0ubuntu0.17.04.1 [4,068 kB] 
Get:16 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 gir1.2-webkit2-4.0 amd64 2.18.5-0ubuntu0.17.04.1 [68.0 kB]           
Get:17 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 gir1.2-javascriptcoregtk-4.0 amd64 2.18.5-0ubuntu0.17.04.1 [21.0 kB] 
Get:18 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 libgweather-common all 3.24.1-0ubuntu0.2 [146 kB]                    
Get:19 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 libgweather-3-6 amd64 3.24.1-0ubuntu0.2 [50.9 kB]                    
Get:20 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 libpoppler-qt5-1 amd64 0.48.0-2ubuntu2.5 [122 kB]                    
Get:21 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 poppler-utils amd64 0.48.0-2ubuntu2.5 [136 kB]                       
Get:22 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 libpoppler-glib8 amd64 0.48.0-2ubuntu2.5 [105 kB]                    
Get:23 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 libpoppler64 amd64 0.48.0-2ubuntu2.5 [778 kB]                        
Get:24 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 squashfs-tools amd64 1:4.3-3ubuntu2.17.04.1 [111 kB]                 
Get:25 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 snapd amd64 2.29.4.2+17.04 [9,755 kB]                                
Fetched 74.1 MB in 31s (2,327 kB/s)                                                                                                        
Preconfiguring packages ...
(Reading database ... 207073 files and directories currently installed.)
Preparing to unpack .../00-distro-info-data_0.33ubuntu0.4_all.deb ...
Unpacking distro-info-data (0.33ubuntu0.4) over (0.33ubuntu0.3) ...
Preparing to unpack .../01-resolvconf_1.79ubuntu4.1_all.deb ...
Unpacking resolvconf (1.79ubuntu4.1) over (1.79ubuntu4) ...
Preparing to unpack .../02-libxml2_2.9.4+dfsg1-2.2ubuntu0.3_amd64.deb ...
Unpacking libxml2:amd64 (2.9.4+dfsg1-2.2ubuntu0.3) over (2.9.4+dfsg1-2.2ubuntu0.2) ...
Preparing to unpack .../03-nplan_0.32~17.04.1_amd64.deb ...
Unpacking nplan (0.32~17.04.1) over (0.23~17.04.1) ...
Preparing to unpack .../04-python3-problem-report_2.20.4-0ubuntu4.10_all.deb ...
Unpacking python3-problem-report (2.20.4-0ubuntu4.10) over (2.20.4-0ubuntu4.9) ...
Preparing to unpack .../05-python3-apport_2.20.4-0ubuntu4.10_all.deb ...
Unpacking python3-apport (2.20.4-0ubuntu4.10) over (2.20.4-0ubuntu4.9) ...
Preparing to unpack .../06-apport_2.20.4-0ubuntu4.10_all.deb ...
Unpacking apport (2.20.4-0ubuntu4.10) over (2.20.4-0ubuntu4.9) ...
Preparing to unpack .../07-apport-gtk_2.20.4-0ubuntu4.10_all.deb ...
Unpacking apport-gtk (2.20.4-0ubuntu4.10) over (2.20.4-0ubuntu4.9) ...
Preparing to unpack .../08-firefox_57.0.4+build1-0ubuntu0.17.04.1_amd64.deb ...
Unpacking firefox (57.0.4+build1-0ubuntu0.17.04.1) over (57.0.1+build2-0ubuntu0.17.04.1) ...
Preparing to unpack .../09-firefox-locale-en_57.0.4+build1-0ubuntu0.17.04.1_amd64.deb ...
Unpacking firefox-locale-en (57.0.4+build1-0ubuntu0.17.04.1) over (57.0.1+build2-0ubuntu0.17.04.1) ...
Preparing to unpack .../10-libwebkit2gtk-4.0-37_2.18.5-0ubuntu0.17.04.1_amd64.deb ...
Unpacking libwebkit2gtk-4.0-37:amd64 (2.18.5-0ubuntu0.17.04.1) over (2.18.3-0ubuntu0.17.04.1) ...
Preparing to unpack .../11-libjavascriptcoregtk-4.0-18_2.18.5-0ubuntu0.17.04.1_amd64.deb ...
Unpacking libjavascriptcoregtk-4.0-18:amd64 (2.18.5-0ubuntu0.17.04.1) over (2.18.3-0ubuntu0.17.04.1) ...
Preparing to unpack .../12-gir1.2-webkit2-4.0_2.18.5-0ubuntu0.17.04.1_amd64.deb ...
Unpacking gir1.2-webkit2-4.0:amd64 (2.18.5-0ubuntu0.17.04.1) over (2.18.3-0ubuntu0.17.04.1) ...
Preparing to unpack .../13-gir1.2-javascriptcoregtk-4.0_2.18.5-0ubuntu0.17.04.1_amd64.deb ...
Unpacking gir1.2-javascriptcoregtk-4.0:amd64 (2.18.5-0ubuntu0.17.04.1) over (2.18.3-0ubuntu0.17.04.1) ...
Preparing to unpack .../14-libgweather-common_3.24.1-0ubuntu0.2_all.deb ...
Unpacking libgweather-common (3.24.1-0ubuntu0.2) over (3.24.1-0ubuntu0.1) ...
Preparing to unpack .../15-libgweather-3-6_3.24.1-0ubuntu0.2_amd64.deb ...
Unpacking libgweather-3-6:amd64 (3.24.1-0ubuntu0.2) over (3.24.1-0ubuntu0.1) ...
Preparing to unpack .../16-nextcloud-client-l10n_2.3.3-20171224.060956~zesty1_all.deb ...
Unpacking nextcloud-client-l10n (2.3.3-20171224.060956~zesty1) over (2.3.2-20170823.130651~zesty1) ...
Preparing to unpack .../17-nextcloud-client_2.3.3-20171224.060956~zesty1_amd64.deb ...
Unpacking nextcloud-client (2.3.3-20171224.060956~zesty1) over (2.3.2-20170823.130651~zesty1) ...
Preparing to unpack .../18-libnextcloudsync0_2.3.3-20171224.060956~zesty1_amd64.deb ...
Unpacking libnextcloudsync0 (2.3.3-20171224.060956~zesty1) over (2.3.2-20170823.130651~zesty1) ...
Preparing to unpack .../19-libpoppler-qt5-1_0.48.0-2ubuntu2.5_amd64.deb ...
Unpacking libpoppler-qt5-1:amd64 (0.48.0-2ubuntu2.5) over (0.48.0-2ubuntu2.4) ...
Preparing to unpack .../20-poppler-utils_0.48.0-2ubuntu2.5_amd64.deb ...
Unpacking poppler-utils (0.48.0-2ubuntu2.5) over (0.48.0-2ubuntu2.4) ...
Preparing to unpack .../21-libpoppler-glib8_0.48.0-2ubuntu2.5_amd64.deb ...
Unpacking libpoppler-glib8:amd64 (0.48.0-2ubuntu2.5) over (0.48.0-2ubuntu2.4) ...
Preparing to unpack .../22-libpoppler64_0.48.0-2ubuntu2.5_amd64.deb ...
Unpacking libpoppler64:amd64 (0.48.0-2ubuntu2.5) over (0.48.0-2ubuntu2.4) ...
Preparing to unpack .../23-squashfs-tools_1%3a4.3-3ubuntu2.17.04.1_amd64.deb ...
Unpacking squashfs-tools (1:4.3-3ubuntu2.17.04.1) over (1:4.3-3ubuntu2) ...
Preparing to unpack .../24-snapd_2.29.4.2+17.04_amd64.deb ...
Warning: Stopping snapd.service, but it can still be activated by:
  snapd.socket
Unpacking snapd (2.29.4.2+17.04) over (2.28.5+17.04) ...
Setting up libnextcloudsync0 (2.3.3-20171224.060956~zesty1) ...
Setting up firefox-locale-en (57.0.4+build1-0ubuntu0.17.04.1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils (0.23-1ubuntu2) ...
Setting up libpoppler64:amd64 (0.48.0-2ubuntu2.5) ...
Processing triggers for libglib2.0-0:amd64 (2.52.0-1) ...
Setting up distro-info-data (0.33ubuntu0.4) ...
Setting up libgweather-common (3.24.1-0ubuntu0.2) ...
Setting up libxml2:amd64 (2.9.4+dfsg1-2.2ubuntu0.3) ...
Setting up gir1.2-javascriptcoregtk-4.0:amd64 (2.18.5-0ubuntu0.17.04.1) ...
Processing triggers for bamfdaemon (0.5.3+17.04.20170406-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up python3-problem-report (2.20.4-0ubuntu4.10) ...
Setting up squashfs-tools (1:4.3-3ubuntu2.17.04.1) ...
Setting up nextcloud-client-l10n (2.3.3-20171224.060956~zesty1) ...
Processing triggers for libc-bin (2.24-9ubuntu2.2) ...
Setting up nplan (0.32~17.04.1) ...
Processing triggers for systemd (232-21ubuntu7.1) ...
Setting up firefox (57.0.4+build1-0ubuntu0.17.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Processing triggers for man-db (2.7.6.1-2) ...
Setting up resolvconf (1.79ubuntu4.1) ...
Setting up libjavascriptcoregtk-4.0-18:amd64 (2.18.5-0ubuntu0.17.04.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Processing triggers for hicolor-icon-theme (0.15-1) ...
Setting up nextcloud-client (2.3.3-20171224.060956~zesty1) ...
Setting up libpoppler-glib8:amd64 (0.48.0-2ubuntu2.5) ...
Setting up poppler-utils (0.48.0-2ubuntu2.5) ...
Setting up libpoppler-qt5-1:amd64 (0.48.0-2ubuntu2.5) ...
Setting up libgweather-3-6:amd64 (3.24.1-0ubuntu0.2) ...
Setting up libwebkit2gtk-4.0-37:amd64 (2.18.5-0ubuntu0.17.04.1) ...
Setting up python3-apport (2.20.4-0ubuntu4.10) ...
Setting up snapd (2.29.4.2+17.04) ...
Installing new version of config file /etc/apparmor.d/usr.lib.snapd.snap-confine.real ...
snapd.refresh.service is a disabled or a static unit, not starting it.
snapd.snap-repair.service is a disabled or a static unit, not starting it.
Setting up apport (2.20.4-0ubuntu4.10) ...
Setting up gir1.2-webkit2-4.0:amd64 (2.18.5-0ubuntu0.17.04.1) ...
Setting up apport-gtk (2.20.4-0ubuntu4.10) ...
Processing triggers for resolvconf (1.79ubuntu4.1) ...
Processing triggers for libc-bin (2.24-9ubuntu2.2) ...
```
```
hugh@zesty-laptop:~$  sudo apt dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```
Upgrade to 17.10
```
hugh@zesty-laptop:~$  sudo do-release-upgrade 
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

Get:1 Upgrade tool signature [819 B]                                                                                                       
Get:2 Upgrade tool [1,247 kB]                                                                                                              
Fetched 1,247 kB in 0s (0 B/s)                                                                                                             
authenticate 'artful.tar.gz' against 'artful.tar.gz.gpg' 
extracting 'artful.tar.gz'

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Hit http://ppa.launchpad.net/nextcloud-devs/client/ubuntu zesty InRelease                                                                  
Hit http://old-releases.ubuntu.com/ubuntu zesty InRelease                                                                                  
Hit http://old-releases.ubuntu.com/ubuntu zesty-updates InRelease                                                                          
Hit http://old-releases.ubuntu.com/ubuntu zesty-security InRelease                                                                         
Fetched 0 B in 0s (0 B/s)                                                                                                                  
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

Updating repository information

Third party sources disabled 

Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 

To continue please press [ENTER]
Get:1 http://gb.archive.ubuntu.com/ubuntu artful InRelease [237 kB]                                                                        
Get:2 http://gb.archive.ubuntu.com/ubuntu artful-updates InRelease [78.6 kB]                                                               
Get:3 http://gb.archive.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]                                                              
Get:4 http://gb.archive.ubuntu.com/ubuntu artful/main i386 Packages [1,067 kB]                                                             
Get:5 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 Packages [1,071 kB]                                                            
Get:6 http://gb.archive.ubuntu.com/ubuntu artful/main Translation-en_GB [71.1 kB]                                                          
Get:7 http://gb.archive.ubuntu.com/ubuntu artful/main Translation-en [542 kB]                                                              
Get:8 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 DEP-11 Metadata [397 kB]                                                       
Get:9 http://gb.archive.ubuntu.com/ubuntu artful/restricted amd64 Packages [8,852 B]                                                       
Get:10 http://gb.archive.ubuntu.com/ubuntu artful/restricted i386 Packages [8,876 B]                                                       
Get:11 http://gb.archive.ubuntu.com/ubuntu artful/restricted Translation-en_GB [2,464 B]                                                   
Get:12 http://gb.archive.ubuntu.com/ubuntu artful/restricted Translation-en [2,788 B]                                                      
Get:13 http://gb.archive.ubuntu.com/ubuntu artful/universe i386 Packages [8,066 kB]                                                        
Get:14 http://gb.archive.ubuntu.com/ubuntu artful/universe amd64 Packages [8,103 kB]                                                       
Get:15 http://gb.archive.ubuntu.com/ubuntu artful/universe Translation-en_GB [9,260 B]                                                     
Get:16 http://gb.archive.ubuntu.com/ubuntu artful/universe Translation-en [4,789 kB]                                                       
Get:17 http://gb.archive.ubuntu.com/ubuntu artful/universe amd64 DEP-11 Metadata [2,845 kB]                                                
Get:18 http://gb.archive.ubuntu.com/ubuntu artful/multiverse amd64 Packages [150 kB]                                                       
Get:19 http://gb.archive.ubuntu.com/ubuntu artful/multiverse i386 Packages [143 kB]                                                        
Get:20 http://gb.archive.ubuntu.com/ubuntu artful/multiverse Translation-en [108 kB]                                                       
Get:21 http://gb.archive.ubuntu.com/ubuntu artful/multiverse Translation-en_GB [82.0 kB]                                                   
Get:22 http://gb.archive.ubuntu.com/ubuntu artful/multiverse amd64 DEP-11 Metadata [43.8 kB]                                               
Get:23 http://gb.archive.ubuntu.com/ubuntu artful-updates/main amd64 Packages [153 kB]                                                     
Get:24 http://gb.archive.ubuntu.com/ubuntu artful-updates/main i386 Packages [152 kB]                                                      
Get:25 http://gb.archive.ubuntu.com/ubuntu artful-updates/main Translation-en [68.4 kB]                                                    
Get:26 http://gb.archive.ubuntu.com/ubuntu artful-updates/main amd64 DEP-11 Metadata [68.5 kB]                                             
Get:27 http://gb.archive.ubuntu.com/ubuntu artful-updates/restricted amd64 Packages [2,192 B]                                              
Get:28 http://gb.archive.ubuntu.com/ubuntu artful-updates/restricted i386 Packages [2,180 B]                                               
Get:29 http://gb.archive.ubuntu.com/ubuntu artful-updates/restricted Translation-en [1,284 B]                                              
Get:30 http://gb.archive.ubuntu.com/ubuntu artful-updates/universe i386 Packages [56.0 kB]                                                 
Get:31 http://gb.archive.ubuntu.com/ubuntu artful-updates/universe amd64 Packages [56.6 kB]                                                
Get:32 http://gb.archive.ubuntu.com/ubuntu artful-updates/universe Translation-en [32.8 kB]                                                
Get:33 http://gb.archive.ubuntu.com/ubuntu artful-updates/universe amd64 DEP-11 Metadata [48.5 kB]                                         
Get:34 http://gb.archive.ubuntu.com/ubuntu artful-updates/multiverse i386 Packages [1,988 B]                                               
Get:35 http://gb.archive.ubuntu.com/ubuntu artful-updates/multiverse amd64 Packages [1,828 B]                                              
Get:36 http://gb.archive.ubuntu.com/ubuntu artful-updates/multiverse Translation-en [1,124 B]                                              
Get:37 http://gb.archive.ubuntu.com/ubuntu artful-security/main i386 Packages [67.7 kB]                                                    
Get:38 http://gb.archive.ubuntu.com/ubuntu artful-security/main amd64 Packages [69.0 kB]                                                   
Get:39 http://gb.archive.ubuntu.com/ubuntu artful-security/main Translation-en [32.1 kB]                                                   
Get:40 http://gb.archive.ubuntu.com/ubuntu artful-security/main amd64 DEP-11 Metadata [2,924 B]                                            
Get:41 http://gb.archive.ubuntu.com/ubuntu artful-security/restricted i386 Packages [2,180 B]                                              
Get:42 http://gb.archive.ubuntu.com/ubuntu artful-security/restricted amd64 Packages [2,192 B]                                             
Get:43 http://gb.archive.ubuntu.com/ubuntu artful-security/restricted Translation-en [1,284 B]                                             
Get:44 http://gb.archive.ubuntu.com/ubuntu artful-security/universe amd64 Packages [23.9 kB]                                               
Get:45 http://gb.archive.ubuntu.com/ubuntu artful-security/universe i386 Packages [23.8 kB]                                                
Get:46 http://gb.archive.ubuntu.com/ubuntu artful-security/universe Translation-en [14.8 kB]                                               
Get:47 http://gb.archive.ubuntu.com/ubuntu artful-security/universe amd64 DEP-11 Metadata [10.4 kB]                                        
Get:48 http://gb.archive.ubuntu.com/ubuntu artful-security/multiverse amd64 Packages [1,828 B]                                             
Get:49 http://gb.archive.ubuntu.com/ubuntu artful-security/multiverse i386 Packages [1,988 B]                                              
Get:50 http://gb.archive.ubuntu.com/ubuntu artful-security/multiverse Translation-en [1,124 B]                                             
Fetched 28.8 MB in 6s (2,085 kB/s)                                                                                                         

Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

Calculating the changes

Calculating the changes

Do you want to start the upgrade? 


16 installed packages are no longer supported by Canonical. You can 
still get support from the community. 

36 packages are going to be removed. 261 new packages are going to be 
installed. 1249 packages are going to be upgraded. 

You have to download a total of 855 M. This download should take 
about 5 minutes with your connection. 

Installing the upgrade can take several hours. Once the download has 
finished, the process cannot be cancelled. 

 Continue [yN]  Details [d]y
```
and off it goes...
```
Fetching
Get:1 http://gb.archive.ubuntu.com/ubuntu artful-updates/main amd64 locales all 2.26-0ubuntu2.1 [3,128 kB]                                 
Get:2 http://gb.archive.ubuntu.com/ubuntu artful-updates/main amd64 libc-dev-bin amd64 2.26-0ubuntu2.1 [69.5 kB]                           
Get:3 http://gb.archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-libc-dev amd64 4.13.0-25.29 [963 kB] etc, ect
```

---

### Post by DuckHook on 2018-01-21
> **fluffy12 said:**
> Unfortunately those instructions are completely wrong and worthless for 17.04 to 17.10.  Because the repos are gone, neither aptitude nor apt-get paths work.  Pray that you were fairly up to date and try do-release-upgrade.
:confused:
Rather than just jumping to unsupported conclusion that instructions are "wrong and worthless", or that "repos are gone", you should start your own thread with your problems and post what steps you took. The strong likelihood is that you didn't follow instructions properly. Start your own thread to receive help with proper steps.
> **QIII said:**
> @fluffy12:

Are you saying that ```
http://old-releases.ubuntu.com/ubuntu/ zesty
``` does not exist?

If it doesn't it may not yet have been prepared.  That would be worth a mention on launchpad.
The zesty directory exists, along with all of the old ones.

EDIT:
ninja'd by howefield.

---

### Post by Johnny English on 2018-01-27
Thank you for the comprehensive response to this, but I have a dumb question. Do I simply append this

```
[COLOR=#000000]## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-security main restricted universe multiverse
[/COLOR]
```

to the end of the sources.list file?

---

### Post by deadflowr on 2018-01-27
> **Johnny English said:**
> Thank you for the comprehensive response to this, but I have a dumb question. Do I simply append this

```
[COLOR=#000000]## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-security main restricted universe multiverse
[/COLOR]
```

to the end of the sources.list file?

No, you completely replace your current sources with that.
It won't work if you still have your original entries.

---

### Post by Johnny English on 2018-01-27
> **deadflowr said:**
> No, you completely replace your current sources with that.
It won't work if you still have your original entries.

So just remove all of this completely?

```

# deb cdrom:[Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu zesty main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ zesty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu zesty-updates main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ zesty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu zesty universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ zesty universe
deb http://archive.ubuntu.com/ubuntu zesty-updates universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ zesty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu ## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu zesty multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ zesty multiverse
deb http://archive.ubuntu.com/ubuntu zesty-updates multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ zesty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu zesty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ zesty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu zesty partner
# deb-src http://archive.canonical.com/ubuntu zesty partner


deb http://archive.ubuntu.com/ubuntu zesty-security main restricted
# deb-src http://security.ubuntu.com/ubuntu zesty-security main restricted
deb http://archive.ubuntu.com/ubuntu zesty-security universe
# deb-src http://security.ubuntu.com/ubuntu zesty-security universe
deb http://archive.ubuntu.com/ubuntu zesty-security multiverse
# deb-src http://security.ubuntu.com/ubuntu zesty-security multiverse
```

and replace it with this

```
[COLOR=#000000][FONT=&amp]## EOL upgrade sources.list[/FONT][/COLOR][COLOR=#000000]# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-updates main restricted universe multiverse 
[/COLOR][COLOR=#000000][FONT=&amp]deb [/FONT][/COLOR][http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)[COLOR=#000000][FONT=&amp] zesty-security main restricted universe multiverse[/FONT][/COLOR]
```

?

---

### Post by deadflowr on 2018-01-27
^ Yes

Edit: To add if you feel unsafe in replacing it all, then first copy the original to a backup like so
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
then you can delete the contents of the original and replace it with the old releases lines with a safety net in place if that's what you want.

---

### Post by Johnny English on 2018-01-27
> **deadflowr said:**
> ^ Yes

Edit: To add if you feel unsafe in replacing it all, then first copy the original to a backup like so
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
then you can delete the contents of the original and replace it with the old releases lines with a safety net in place if that's what you want.

Awesome. Thank you for your help and apologies for dumb questions!

---

### Post by sirgatsen on 2018-01-29
Hi there, I just finished the upgrade from 17.04 to 17.10, how do I get my sources.list back to normal (pointing to the current release of 17.10)? It currently has those three lines pointing to "old-releases".

---

### Post by ian-weisser on 2018-01-29
Simply choose a different mirror in your Software & Updates control panel, or [edit manually]("https://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main").

---

### Post by CrusoeTP on 2018-01-30
Seems dumb to me that such a 'easy to use' distro breaks all upgrades by renaming the repos, then requires users to manually edit the sources file.

Goofy.

---

### Post by cruzer001 on 2018-01-30
@CrusoeTP

This is a necessary process if you do not maintian (update) your system.  This standard and necessary procedure will update a version that has reached end of life and is no longer supported by the regular sources.

Nothing goofy about it.

---

### Post by alanhoyle on 2018-02-04
If possible, it would be better if there was a warning about the EoL when it tries to do the apt update.  It would be better if there was something that told me what was happening 
 or suggested the "do-release-upgrade" instead of me needing to google the error message (which is what brought me to this thread for the solution). 

I certainly try to stay updated in general.  I encountered this error when I rebooted to my Ubuntu MATE partition on a laptop that mostly runs another OS, but once every month or two runs Linux. And, more to the point, this error is probably only encountered by people who are actively trying to do an update/upgrade of some kind. 

I actually didn't seem to need to update the sources.list, but running the do-release upgrade has started a big download/install.  

It would be much better if there was something that noticed the EoL and then popped up the "Hey, you're running an EoL version of Ubuntu.  Click here to upgrade to a newer release, or maybe consider switching to an LTS version in the future?

---

### Post by alanhoyle on 2018-02-04
> **alanhoyle said:**
> I actually didn't seem to need to update the sources.list, but running the do-release-upgrade has started a big download/install.  


cat /etc/lsb-release does indeed tell me that I'm now running 17.10 FWIW, after just running do-release-upgrade once or twice.

---

### Post by coffeecat on 2018-02-04
The OP hasn't been back since the day they started this thread, so we can safely assume they've lost interest. Since then, the thread has suffered two marginal trolling attempts and has been hijacked more than once. Time to close it.

If anyone needs help with failed updates, or upgrades to a supported version of Ubuntu, please start your own new thread.

Thread closed.

---

