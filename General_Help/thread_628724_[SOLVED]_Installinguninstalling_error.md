---
title: "[SOLVED] Installing/uninstalling error"
date: 2007-12-01
forum: General Help
---

### Post by TidusBlade on 2007-12-01
Ok so I am running Dapper Drake at the moment and just installed the package called "rtorrent" then after alot of repo changes and everything, I got back the default repos and now I cannot install "rtorrent" from the .deb package because it returns this:
```
root@89-149-240-61:/etc/apt# dpkg -i /root/test/rtorrent_0.7.4-2ubuntu2_i386.deb
Selecting previously deselected package rtorrent.
(Reading database ... 16281 files and directories currently installed.)
Unpacking rtorrent (from .../rtorrent_0.7.4-2ubuntu2_i386.deb) ...
dpkg: dependency problems prevent configuration of rtorrent:
 rtorrent depends on libc6 (>= 2.6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 rtorrent depends on libcurl3 (>= 7.16.2-1); however:
  Version of libcurl3 on system is 7.15.1-1ubuntu2.
 rtorrent depends on libgcc1 (>= 1:4.2-20070516); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 rtorrent depends on libkrb53 (>= 1.6.dfsg.1); however:
  Version of libkrb53 on system is 1.4.3-5ubuntu0.1.
 rtorrent depends on libssl0.9.8 (>= 0.9.8e-1); however:
  Version of libssl0.9.8 on system is 0.9.8a-7build1.
 rtorrent depends on libstdc++6 (>= 4.2-20070516); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
 rtorrent depends on libtorrent10; however:
  Package libtorrent10 is not installed.
dpkg: error processing rtorrent (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rtorrent
root@89-149-240-61:/etc/apt#                           
```
And If I try to remove it using apt-get it returns this:
```
root@89-149-240-61:/etc/apt# apt-get remove rtorrent
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  rtorrent
0 upgraded, 0 newly installed, 1 to remove and 59 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 786kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 16292 files and directories currently installed.)
Removing rtorrent ...
root@89-149-240-61:/etc/apt#                                   
```
And then trying to install it from the command dpkg returns the first error :( 
Probably been asking for way too much help today... so I would gratefully accept any information regarding this :)
Thank you very much ;)
**EDIT: It happens with every single apt-get or .deb I try...**
EDIT: solved, I was very retarded :P

---

### Post by TidusBlade on 2007-12-02
Bump... I really need to fix this :(
EDIT: I tried "**dpkg -l | grep -v ^ii**", it return this:
```
root@89-149-240-61:~/rtorrent-0.7.1# dpkg -l | grep -v ^ii
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                         Version                      Description
+++-============================-============================-============================================
iU  bittorrent                   3.4.2-11ubuntu2              Original BitTorent client - console tools
iU  ctorrent                     1.3.4-dnh3.1-1               BitTorrent Client written in C
iU  python-bittorrent            3.4.2-11ubuntu2              Scatter-gather network file transfer
iU  rtorrent                     0.7.4-2ubuntu2               ncurses BitTorrent client based on LibTorren
```
I dunno if this will help but those are the packages causing me problems, if anyone knows anything I would appreciate any info!
EDIT: Fixed, I was very retarded :P

---

