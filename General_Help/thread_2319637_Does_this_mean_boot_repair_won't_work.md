---
title: "Does this mean boot repair won't work?"
date: 2016-04-06
forum: General Help
---

### Post by jackyhughes on 2016-04-06
As usual, I have no idea what I am doing....

```
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ sudo add-apt-repository -y ppa:yannubuntu/boot-repair; \
> sudo apt-get update; \
> 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.J1aP1DMto1 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 3C48D16124B50277AF10D27F32B18A1260D8DA0B
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise InRelease
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted TranslationIndex
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease [55.7 kB]            
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease [13.3 kB]                     
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [1,098 B]                  
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]                    
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [1,965 B]            
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex [199 B]           
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]                      
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en [2,123 B]           
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [1,045 kB]  
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease [55.7 kB]         
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [16.1 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [208 B] 
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [202 B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages [1,274 kB]         
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [657 kB] 
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]    
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex [3,706 B]       
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B] 
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en [414 kB]  
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en [3,869 B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en [726 kB]          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [11.6 kB]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [208 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [202 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [252 kB]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [2,976 B]
Fetched 4,598 kB in 6s (666 kB/s)                                              
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-extra efibootmgr gawk glade2script libsigsegv2
Suggested packages:
  lvm2 mbr mdadm clean-ubiquity boot-info os-uninstaller
Recommended packages:
  pastebinit
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra efibootmgr gawk glade2script libsigsegv2
0 upgraded, 7 newly installed, 0 to remove and 754 not upgraded.
Need to get 1,094 kB of archives.
After this operation, 4,713 kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) precise/main glade2script all 3.2.2~ppa45~precise [42.3 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libsigsegv2 i386 2.9-4ubuntu2 [14.4 kB]
Get:3 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) precise/main boot-sav all 4ppa35 [414 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gawk i386 1:3.1.8+dfsg-0.1ubuntu1 [438 kB]
Get:5 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) precise/main boot-repair all 4ppa35 [11.6 kB]
Get:6 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) precise/main boot-sav-extra all 4ppa35 [142 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main efibootmgr i386 0.5.4-2ubuntu1.1 [31.8 kB]
Fetched 1,094 kB in 0s (3,400 kB/s)
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously unselected package libsigsegv2.
(Reading database ... 150248 files and directories currently installed.)
Unpacking libsigsegv2 (from .../libsigsegv2_2.9-4ubuntu2_i386.deb) ...
Setting up libsigsegv2 (2.9-4ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package gawk.
(Reading database ... 150256 files and directories currently installed.)
Unpacking gawk (from .../gawk_1%3a3.1.8+dfsg-0.1ubuntu1_i386.deb) ...
Selecting previously unselected package glade2script.
Unpacking glade2script (from .../glade2script_3.2.2~ppa45~precise_all.deb) ...
Selecting previously unselected package boot-sav.
Unpacking boot-sav (from .../boot-sav_4ppa35_all.deb) ...
Selecting previously unselected package boot-repair.
Unpacking boot-repair (from .../boot-repair_4ppa35_all.deb) ...
Selecting previously unselected package boot-sav-extra.
Unpacking boot-sav-extra (from .../boot-sav-extra_4ppa35_all.deb) ...
Selecting previously unselected package efibootmgr.
Unpacking efibootmgr (from .../efibootmgr_0.5.4-2ubuntu1.1_i386.deb) ...
Processing triggers for man-db ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$
```

I did get boot repair to work, but this is the report. 

[http://paste.ubuntu.com/15642400/](http://paste.ubuntu.com/15642400/)

---

### Post by oldfred on 2016-04-06
Boot-Repair cannot fix a Linux that does not exist.

You are showing a large unallocated space then the extended with swap.
I assume the unallocated then was a Linux partition?

       [http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

These are all where Windows upgrade deleted the partition, but the use of parted rescue or testdisk is the same as what you need to try.

 [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by jackyhughes on 2016-04-06
I replied on another thread concerning how the problem got solved. I wish I had seen this as I solved things by using the unallocated space.

---

