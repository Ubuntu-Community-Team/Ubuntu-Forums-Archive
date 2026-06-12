---
title: "After installing alsa-tools to access hda-verb from the terminal (see below) Ubuntu c"
date: 2014-12-04
forum: General Help
---

### Post by Douglas_H_Campbell on 2014-12-04
[SIZE=2]After installing alsa-tools to access hda-verb from  the terminal (see below) Ubuntu can't find hda-verb.
[/SIZE]
[SIZE=2] [/SIZE][SIZE=2]What happened to it?  Thanks. [/SIZE]

[SIZE=2] [/SIZE][SIZE=2]
[/SIZE]
[SIZE=2] [/SIZE][SIZE=2]
[/SIZE]
[SIZE=2] [/SIZE][SIZE=2]The program 'hda-verb' is currently not installed. You can install it by typing:  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]sudo apt-get install alsa-tools  
[/SIZE]
[SIZE=2] [/SIZE][SIZE=2]doug@doug-Ubuntu:~$ sudo apt-get install alsa-tools  
[/SIZE]
[SIZE=2] [/SIZE][SIZE=2][sudo] password for doug:  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]Reading package lists... Done  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]Building dependency tree        [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]Reading state information... Done  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]The following packages were automatically installed and are no longer required:  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]Use 'apt-get autoremove' to remove them.  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]The following NEW packages will be installed:  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]  alsa-tools  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.  [/SIZE]

[SIZE=2] [/SIZE][SIZE=2]Need to get 50.4 kB of archives.  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]After this operation, 216 kB of additional disk space will be used.  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty/universe alsa-tools amd64 1.0.27-2ubuntu3 [50.4 kB]  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]Fetched 50.4 kB in 0s (74.3 kB/s)    [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]Selecting previously unselected package alsa-tools.  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2](Reading database ... 284326 files and directories currently installed.)  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]Preparing to unpack .../alsa-tools_1.0.27-2ubuntu3_amd64.deb ...  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]Unpacking alsa-tools (1.0.27-2ubuntu3) ...  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]Processing triggers for man-db (2.6.7.1-1ubuntu1) ...  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]Setting up alsa-tools (1.0.27-2ubuntu3) ...  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]doug@doug-Ubuntu:~$  hda-verb /dev/snd/hwC0D2 0x20 SET_COEF_INDEX 0x07  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]**open: No such file or directory**  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]doug@doug-Ubuntu:~$  [/SIZE]

---

