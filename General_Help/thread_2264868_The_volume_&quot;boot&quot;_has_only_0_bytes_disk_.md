---
title: "The volume &quot;boot&quot; has only 0 bytes disk space remaining"
date: 2015-02-10
forum: General Help
---

### Post by dave-borkowskijr-z on 2015-02-10
I know others have posted this, I have read and read and I really need some help.


Here is some (not even close) to all I have done, to try to fix this.  I have lost track of what I have done so here is a start I supose.

OK so I have been getting this 0 bytes available in /boot for a while aI I have been trying to fix it.



```
sudo apt-get autoremove

dave@dave-Satellite-A135:~$ sudo apt-get autoremove 
[sudo] password for dave:  
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
You might want to run 'apt-get -f install' to correct these. 
The following packages have unmet dependencies: 
 linux-image-extra-3.13.0-45-generic : Depends: linux-image-3.13.0-45-generic but it is not installed 
 linux-image-generic : Depends: linux-image-3.13.0-45-generic but it is not installed 
E: Unmet dependencies. Try using -f. 

so then I ran this 
dave@dave-Satellite-A135:~$ sudo apt-get -f install 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Correcting dependencies... Done 
The following extra packages will be installed: 
  linux-image-3.13.0-45-generic 
Suggested packages: 
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools 
The following NEW packages will be installed: 
  linux-image-3.13.0-45-generic 
0 upgraded, 1 newly installed, 0 to remove and 51 not upgraded. 
4 not fully installed or removed. 
Need to get 0 B/14.7 MB of archives. 
After this operation, 32.6 MB of additional disk space will be used. 
Do you want to continue? [Y/n] y 
(Reading database ... 425218 files and directories currently installed.) 
Preparing to unpack .../linux-image-3.13.0-45-generic_3.13.0-45.74_i386.deb ... 
Done. 
Unpacking linux-image-3.13.0-45-generic (3.13.0-45.74) ... 
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-45-generic_3.13.0-45.74_i386.deb (--unpack): 
 cannot copy extracted data for './boot/System.map-3.13.0-45-generic' to '/boot/System.map-3.13.0-45-generic.dpkg-new': failed to write (No space left on device) 
No apport report written because the error message indicates a disk full error 
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-image-3.13.0-45-generic_3.13.0-45.74_i386.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
ad get the error code (1) I would assume because its trying toinstall the newest one but has no room.

So then I tried this 
sudo apt-get autoremove
dave@dave-Satellite-A135:~$ sudo apt-get autoremove 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
You might want to run 'apt-get -f install' to correct these. 
The following packages have unmet dependencies: 
 linux-image-extra-3.13.0-45-generic : Depends: linux-image-3.13.0-45-generic but it is not installed 
 linux-image-generic : Depends: linux-image-3.13.0-45-generic but it is not installed 
E: Unmet dependencies. Try using -f. 


dave@dave-Satellite-A135:~$ df -h 
Filesystem                   Size  Used Avail Use% Mounted on 
/dev/mapper/ubuntu--vg-root  456G  111G  322G  26% / 
none                         4.0K     0  4.0K   0% /sys/fs/cgroup 
udev                         1.5G  4.0K  1.5G   1% /dev 
tmpfs                        303M  1.3M  301M   1% /run 
none                         5.0M     0  5.0M   0% /run/lock 
none                         1.5G  260K  1.5G   1% /run/shm 
none                         100M   68K  100M   1% /run/user 
/dev/sda1                    236M  233M     0 100% /boot 




in the end here is what I still have 
dave@dave-Satellite-A135:~$ df -h 
Filesystem                   Size  Used Avail Use% Mounted on 
/dev/mapper/ubuntu--vg-root  456G  111G  322G  26% / 
none                         4.0K     0  4.0K   0% /sys/fs/cgroup 
udev                         1.5G  4.0K  1.5G   1% /dev 
tmpfs                        303M  1.3M  301M   1% /run 
none                         5.0M     0  5.0M   0% /run/lock 
none                         1.5G  260K  1.5G   1% /run/shm 
none                         100M   76K  100M   1% /run/user 
/dev/sda1                    236M  233M     0 100% /boot 
dave@dave-Satellite-A135:~$
```

---

### Post by Yellow Pasque on 2015-02-10
Get rid of old kernels. Autoremove won't do it for you.

---

### Post by Bashing-om on 2015-02-10
dave-borkowskijr-z; Hello '

Temüjin is the faster on the draw.
Looks like apt-get does not have any operating head room at 100% capacity ... a big no no !
If ya need help on ^^.
Post back the output of terminal command - Between Code Tags :
```

dpkg -l | grep linux-image-

```
the additional push in the right direction will be provided.

[INDENT][INDENT]10 pounds of salt
[INDENT][INDENT][INDENT]in a 8 pound sack
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dave-borkowskijr-z on 2015-02-10
dave@dave-Satellite-A135:~$ dpkg -l | grep linux-image-
ii  linux-image-3.13.0-32-generic                               3.13.0-32.57                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-34-generic                               3.13.0-34.60                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-37-generic                               3.13.0-37.64                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-39-generic                               3.13.0-39.66                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-40-generic                               3.13.0-40.69                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-43-generic                               3.13.0-43.72                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                               3.13.0-44.73                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                         3.13.0-32.57                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                         3.13.0-37.64                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                         3.13.0-39.66                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                         3.13.0-40.69                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                         3.13.0-43.72                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
iF  linux-image-extra-3.13.0-44-generic                         3.13.0-44.73                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
iU  linux-image-extra-3.13.0-45-generic                         3.13.0-45.74                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
iU  linux-image-generic                                         3.13.0.45.52                                        i386         Generic Linux kernel image
dave@dave-Satellite-A135:~$ 


Thank you

---

### Post by Bashing-om on 2015-02-10
dave-borkowskijr-z; Hey:

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Try;  maybe dpkg can operate:
```

sudo dpkg -P linux-image-3.13.0-{32,34,35,37,39,40}-generic
sudo dpkg -P linux-image-extra-3.13.0-{32,34,35,37,39,40}-generic
sudo dpkg -P linux-headers-3.13.0-{32,34,35,37,39,40}-generic
sudo dpkg -P linux-headers-3.13.0-{32,34,35,37,39,40}

```

IF you are able to remove these images, see now if the package manager can operate:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
see if that -45 kernel does install with the 'dist-upgrade' directive.
Else we get the more directive for 'apt-get' to get.

[INDENT][INDENT]maybe YES
[/INDENT][/INDENT]

---

### Post by dave-borkowskijr-z on 2015-02-10
```
ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
17% [Waiting for headers] [Waiting for headers] [Waiting for header                                                                   Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease
19% [Waiting for headers] [Waiting for headers] [Waiting for header                                                                   Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
21% [Waiting for headers] [Waiting for headers] [Waiting for header                                                                   Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]
91% [Waiting for headers] [Waiting for headers] [Waiting for header                                                                   Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease
91% [Waiting for headers] [Waiting for headers] [Waiting for header                                                                   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
91% [Waiting for headers] [Waiting for headers] [Waiting for header                                                                   Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
99% [Waiting for headers] [Waiting for headers] [Waiting for header                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg
99% [Waiting for headers] [Waiting for headers] [Waiting for header                                                                   Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg
99% [Waiting for headers] [Waiting for headers] [Waiting for header                                                                   Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release
99% [Waiting for headers] [Waiting for headers] [Waiting for header                                                                   Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]
100% [Waiting for headers] [Waiting for headers] [Waiting for heade100% [Release gpgv 11.9 kB] [Waiting for headers] [Waiting for head                                                                   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release
100% [Release gpgv 11.9 kB] [Waiting for headers] [Waiting for head                                                                   Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [62.0 kB]
5% [Release gpgv 11.9 kB] [Waiting for headers] [4 Release 1,139 B/                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg
25% [Release gpgv 11.9 kB] [4 Release 14.2 kB/62.0 kB 23%] [Waiting                                                                   Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release
25% [Release gpgv 11.9 kB] [Waiting for headers] [4 Release 14.2 kB                                                                   25% [Release gpgv 15.1 kB] [Waiting for headers] [4 Release 14.2 kB                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release
25% [Release gpgv 15.1 kB] [Waiting for headers] [4 Release 14.2 kB25% [Waiting for headers] [4 Release 14.2 kB/62.0 kB 23%] [Waiting 25% [Release gpgv 9,359 B] [Waiting for headers] [4 Release 14.2 kB43% [Waiting for headers] [4 Release 25.8 kB/62.0 kB 42%] [Waiting 43% [Release gpgv 58.5 kB] [Waiting for headers] [4 Release 25.8 kB                                                                   Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [62.0 kB]
26% [Release gpgv 58.5 kB] [5 Release 1,155 B/62.0 kB 2%] [4 Releas31% [5 Release 6,947 B/62.0 kB 11%] [4 Release 30.1 kB/62.0 kB 49%]                                                                   Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources
37% [5 Release 14.2 kB/62.0 kB 23%] [4 Release 30.1 kB/62.0 kB 49%]                                                                   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
37% [5 Release 14.2 kB/62.0 kB 23%] [4 Release 30.1 kB/62.0 kB 49%]37% [Sources 0 B] [5 Release 14.2 kB/62.0 kB 23%] [4 Release 30.1 k37% [5 Release 14.2 kB/62.0 kB 23%] [4 Release 30.1 kB/62.0 kB 49%]37% [Packages 914 B] [5 Release 14.2 kB/62.0 kB 23%] [4 Release 30.37% [5 Release 14.2 kB/62.0 kB 23%] [4 Release 30.1 kB/62.0 kB 49%]                                                                   Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources
71% [5 Release 34.5 kB/62.0 kB 56%] [4 Release 53.3 kB/62.0 kB 86%]71% [Sources 36.1 kB] [5 Release 34.5 kB/62.0 kB 56%] [4 Release 5378% [5 Release 34.5 kB/62.0 kB 56%] [4 Release 53.3 kB/62.0 kB 86%]                                                                   Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages
86% [5 Release 40.3 kB/62.0 kB 65%] [4 Release 60.5 kB/62.0 kB 98%]86% [5 Release 40.3 kB/62.0 kB 65%] [4 Release 60.5 kB/62.0 kB 98%]                                                                   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
91% [5 Release 48.9 kB/62.0 kB 79%] [4 Release 60.5 kB/62.0 kB 98%]91% [Translation-en 811 B] [5 Release 48.9 kB/62.0 kB 79%] [4 Relea91% [5 Release 48.9 kB/62.0 kB 79%] [4 Release 60.5 kB/62.0 kB 98%]92% [5 Release 48.9 kB/62.0 kB 79%] [Waiting for headers] [Waiting 92% [4 Release gpgv 62.0 kB] [5 Release 48.9 kB/62.0 kB 79%] [Waiti92% [5 Release 48.9 kB/62.0 kB 79%] [Waiting for headers] [Waiting 100% [Waiting for headers] [Waiting for headers] [Waiting for heade100% [5 Release gpgv 62.0 kB] [Waiting for headers] [Waiting for he100% [Waiting for headers] [Waiting for headers] [Waiting for heade                                                                   Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages
100% [Waiting for headers] [Waiting for headers] [Waiting for heade100% [Waiting for headers] [Waiting for headers] [Waiting for heade                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release
                                                                   100% [Waiting for headers] [Waiting for headers] [Waiting for heade                                                                   100% [Release gpgv 62.0 kB] [Waiting for headers] [Waiting for head                                                                   Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [65.2 kB]
74% [Release gpgv 62.0 kB] [Waiting for headers] [6 Sources 1,104 B77% [Waiting for headers] [6 Sources 8,344 B/65.2 kB 13%] [Waiting                                                                    Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources
88% [6 Sources 34.4 kB/65.2 kB 53%] [Waiting for headers] [Waiting 88% [Sources 5,000 kB] [Waiting for headers] [6 Sources 34.4 kB/65.                                                                   Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en
89% [Sources 5,000 kB] [Waiting for headers] [6 Sources 37.3 kB/65.                                                                   Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty InRelease
89% [Sources 5,000 kB] [Waiting for headers] [6 Sources 38.8 kB/65.                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources
89% [Sources 5,000 kB] [Waiting for headers] [6 Sources 38.8 kB/65.                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release.gpg           
100% [6 Sources bzip2 0 B] [Sources 5,000 kB] [Waiting for headers]                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources
100% [6 Sources bzip2 0 B] [Sources 5,000 kB] [Waiting for headers]100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers]                                                                   Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [2,061 B]
100% [Sources 5,000 kB] [Waiting for headers] [7 Sources 1,106 B/2,100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers]100% [7 Sources bzip2 0 B] [Sources 5,000 kB] [Waiting for headers]100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers]                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers]                                                                   Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers]100% [Sources 5,000 kB] [Release gpgv 14.0 kB] [Waiting for headers100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers]                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers]                                                                   Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [1,896 B]
100% [Sources 5,000 kB] [Waiting for headers] [8 Sources 1,106 B/1,100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers]100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers]                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages
100% [Sources 5,000 kB] [Waiting for headers] [Waiting for headers]                                                                   100% [Waiting for headers] [Waiting for headers] [Waiting for heade                                                                   100% [Translation-en 14.0 kB] [Waiting for headers] [Waiting for he                                                                   100% [Waiting for headers] [Waiting for headers] [Waiting for heade                                                                   100% [Sources 22.9 kB] [Waiting for headers] [Waiting for headers]                                                                    100% [Waiting for headers] [Waiting for headers] [Waiting for heade                                                                   100% [Sources 711 kB] [Waiting for headers] [Waiting for headers] [                                                                   Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [17.5 kB]
100% [Sources 711 kB] [Waiting for headers] [9 Sources 1,104 B/17.5                                                                   Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main i386 Packages  
100% [9 Sources bzip2 0 B] [Sources 711 kB] [Waiting for headers] [100% [Sources 711 kB] [Waiting for headers] [Waiting for headers] [                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages
100% [Sources 711 kB] [Waiting for headers] [Waiting for headers] [                                                                   100% [Waiting for headers] [Waiting for headers] [Waiting for heade                                                                   100% [Sources 27.9 MB] [Waiting for headers] [Waiting for headers]                                                                    Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [191 kB]
97% [Sources 27.9 MB] [Waiting for headers] [10 Packages 1,102 B/19                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en
98% [Sources 27.9 MB] [Waiting for headers] [10 Packages 41.6 kB/19                                                                   Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US
                                                                   99% [Sources 27.9 MB] [Waiting for headers] [10 Packages 121 kB/191                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en
                                                                   99% [Sources 27.9 MB] [Waiting for headers] [10 Packages 123 kB/191                                                                   Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
                                                                   100% [Sources 27.9 MB] [Waiting for headers] [10 Packages 163 kB/19                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
100% [Sources 27.9 MB] [Waiting for headers] [10 Packages 178 kB/19                                                                   100% [10 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
                                                                   100% [10 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers                                                                   Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8,846 B]
                                                                   100% [10 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers100% [10 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers                                                                   Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [177 kB]
97% [10 Packages bzip2 0 B] [Sources 27.9 MB] [12 Sources 1,118 B/1                                                                   98% [Sources 27.9 MB] [12 Sources 34.4 kB/177 kB 19%] [Waiting for                                                                    98% [11 Packages bzip2 0 B] [Sources 27.9 MB] [12 Sources 34.4 kB/1                                                                   98% [Sources 27.9 MB] [12 Sources 44.6 kB/177 kB 25%] [Waiting for                                                                    Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3,624 B]
                                                                   98% [Sources 27.9 MB] [12 Sources 53.2 kB/177 kB 30%] [13 Packages                                                                    98% [Sources 27.9 MB] [12 Sources 53.2 kB/177 kB 30%] [Waiting for                                                                    98% [13 Packages bzip2 0 B] [Sources 27.9 MB] [12 Sources 53.2 kB/1                                                                   98% [Sources 27.9 MB] [12 Sources 72.1 kB/177 kB 41%] [Waiting for                                                                    Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [85.6 kB]
                                                                   98% [Sources 27.9 MB] [12 Sources 105 kB/177 kB 60%] [14 Packages 1                                                                   100% [14 Packages bzip2 0 B] [Sources 27.9 MB] [12 Sources 171 kB/1                                                                   Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en_US
                                                                   100% [14 Packages bzip2 0 B] [Sources 27.9 MB] [12 Sources 176 kB/1100% [14 Packages bzip2 0 B] [Sources 27.9 MB] [Waiting for headers                                                                   100% [12 Sources bzip2 0 B] [Sources 27.9 MB] [Waiting for headers]                                                                   Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [2,061 B]
100% [12 Sources bzip2 0 B] [Sources 27.9 MB] [15 Sources 1,122 B/2100% [12 Sources bzip2 0 B] [Sources 27.9 MB] [Waiting for headers]                                                                   Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
100% [12 Sources bzip2 0 B] [Sources 27.9 MB] [Waiting for headers]                                                                   Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en
100% [12 Sources bzip2 0 B] [Sources 27.9 MB] [Waiting for headers]                                                                   Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [4,463 B]
100% [12 Sources bzip2 0 B] [Sources 27.9 MB] [16 Sources 1,121 B/4100% [12 Sources bzip2 0 B] [Sources 27.9 MB] [Waiting for headers]                                                                   Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [102 kB]
98% [12 Sources bzip2 0 B] [Sources 27.9 MB] [17 Sources 1,118 B/10                                                                   99% [Sources 27.9 MB] [17 Sources 17.0 kB/102 kB 17%] [Waiting for                                                                    99% [15 Sources bzip2 0 B] [Sources 27.9 MB] [17 Sources 25.7 kB/10                                                                   99% [Sources 27.9 MB] [17 Sources 25.7 kB/102 kB 25%] [Waiting for                                                                    99% [16 Sources bzip2 0 B] [Sources 27.9 MB] [17 Sources 25.7 kB/10                                                                   99% [Sources 27.9 MB] [17 Sources 25.7 kB/102 kB 25%] [Waiting for                                                                    Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
                                                                   Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
100% [Sources 27.9 MB] [17 Sources 86.5 kB/102 kB 85%] [Waiting for                                                                   Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [426 kB]
94% [17 Sources bzip2 0 B] [Sources 27.9 MB] [18 Packages 2,566 B/4                                                                   94% [Sources 27.9 MB] [18 Packages 17.0 kB/426 kB 4%] [Waiting for                                                                    Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
                                                                   Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [8,846 B]
100% [18 Packages bzip2 0 B] [Packages 8,205 kB] [19 Packages 1,121                                                                   100% [18 Packages bzip2 0 B] [Packages 8,205 kB] [Waiting for heade                                                                   Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [11.3 kB]
                                                                   100% [18 Packages bzip2 0 B] [Packages 8,205 kB] [20 Packages 1,120                                                                   100% [18 Packages bzip2 0 B] [Packages 8,205 kB] [Waiting for heade                                                                   Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [250 kB]
                                                                   99% [18 Packages bzip2 0 B] [Packages 8,205 kB] [21 Packages 1,118                                                                    100% [18 Packages bzip2 0 B] [Packages 185 kB] [21 Packages 51.8 kB100% [18 Packages bzip2 0 B] [21 Packages 66.3 kB/250 kB 27%]     7100% [18 Packages bzip2 0 B] [Packages 674 kB] [21 Packages 66.3 kB100% [18 Packages bzip2 0 B] [21 Packages 88.0 kB/250 kB 35%]     7100% [18 Packages bzip2 0 B] [Packages 1,199 B] [21 Packages 88.0 k100% [18 Packages bzip2 0 B] [21 Packages 88.0 kB/250 kB 35%]     7100% [18 Packages bzip2 0 B] [Packages 31.7 MB] [21 Packages 88.0 k100% [Packages 31.7 MB] [21 Packages 118 kB/250 kB 47%]           7100% [19 Packages bzip2 0 B] [Packages 31.7 MB] [21 Packages 118 kB100% [Packages 31.7 MB] [21 Packages 127 kB/250 kB 51%]           7100% [20 Packages bzip2 0 B] [Packages 31.7 MB] [21 Packages 127 kB100% [Packages 31.7 MB] [21 Packages 131 kB/250 kB 53%]           7100% [Packages 31.7 MB]                                           7100% [21 Packages bzip2 0 B] [Packages 31.7 MB]                   7                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en
                                                                   100% [21 Packages bzip2 0 B] [Packages 31.7 MB] [Waiting for header                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
100% [21 Packages bzip2 0 B] [Packages 31.7 MB] [Waiting for header                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
100% [21 Packages bzip2 0 B] [Packages 31.7 MB] [Waiting for header                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
100% [21 Packages bzip2 0 B] [Packages 31.7 MB] [Waiting for header                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources
100% [21 Packages bzip2 0 B] [Packages 31.7 MB] [Waiting for header                                                                   100% [Packages 31.7 MB] [Waiting for headers]                     7                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources
100% [Packages 31.7 MB] [Waiting for headers]                     7                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources
100% [Packages 31.7 MB] [Waiting for headers]                     7                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
100% [Packages 31.7 MB] [Waiting for headers]                     7                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
100% [Packages 31.7 MB] [Waiting for headers]                     7                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
100% [Packages 31.7 MB] [Waiting for headers]                     7                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
100% [Packages 31.7 MB] [Waiting for headers]                     7                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
100% [Packages 31.7 MB] [Waiting for headers]                     7                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
100% [Packages 31.7 MB] [Waiting for headers]                     7                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
100% [Packages 31.7 MB] [Waiting for headers]                     7                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
100% [Packages 31.7 MB] [Waiting for headers]                     7                                                                   Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
100% [Packages 31.7 MB] [Waiting for headers]                     7100% [Packages 31.7 MB] [Waiting for headers]                     7                                                                   Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
100% [Packages 31.7 MB]                                           7                                                                   Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
100% [Packages 31.7 MB]                                           7                                                                   Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
100% [Packages 31.7 MB]                                           7                                                                   Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
100% [Packages 31.7 MB]                                           7100% [Packages 31.7 MB]                                           7100% [Working]                                                    7100% [Translation-en 4,149 kB]                                    7100% [Working]                                                    7100% [Translation-en 409 kB]                                      7100% [Working]                                                    7100% [Translation-en 21.2 kB]                                     7100% [Working]                                                    7100% [Translation-en 18.6 MB]                                     7100% [Translation-en 18.6 MB]                                     7100% [Translation-en 18.6 MB]                                     7100% [Translation-en 18.6 MB]                                     7100% [Working]                                                    7100% [Translation-en 1,027 kB]                                    7100% [Working]                                                    7100% [Translation-en 5,539 B]                                     7100% [Working]                                                    7100% [Translation-en 15.4 kB]                                     7100% [Working]                                                    7100% [Translation-en 244 kB]                                      7100% [Working]                                                    7100% [Translation-en 1,705 kB]                                    7100% [Working]                                                    7100% [Translation-en 18.8 kB]                                     7100% [Working]                                                    7100% [Translation-en 15.4 kB]                                     7100% [Working]                                                    7100% [Translation-en 646 kB]                                      7100% [Working]                                                    7100% [Sources 13.1 kB]                                            7100% [Working]                                                    7100% [Sources 0 B]                                                7100% [Working]                                                    7100% [Sources 73.6 kB]                                            7100% [Working]                                                    7100% [Sources 4,444 B]                                            7100% [Working]                                                    7100% [Packages 19.3 kB]                                           7100% [Working]                                                    7100% [Packages 0 B]                                               7100% [Working]                                                    7100% [Packages 113 kB]                                            7100% [Working]                                                    7100% [Packages 2,465 B]                                           7100% [Working]                                                    7100% [Translation-en 10.6 kB]                                     7100% [Working]                                                    7100% [Translation-en 1,407 B]                                     7100% [Working]                                                    7100% [Translation-en 0 B]                                         7100% [Working]                                                    7100% [Translation-en 83.5 kB]                                     7100% [Working]                                                    7                                                                   Fetched 1,483 kB in 11s (127 kB/s)
Reading package lists... Done
dave@dave-Satellite-A135:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-45-generic : Depends: linux-image-3.13.0-45-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-45-generic but it is not installed
E: Unmet dependencies. Try using -f.
dave@dave-Satellite-A135:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-45-generic : Depends: linux-image-3.13.0-45-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-45-generic but it is not installed
E: Unmet dependencies. Try using -f.
dave@dave-Satellite-A135:~$ cd/
bash: cd/: No such file or directory
dave@dave-Satellite-A135:~$ cd /
dave@dave-Satellite-A135:/$ cd boot
dave@dave-Satellite-A135:/boot$ ls
abi-3.13.0-32-generic         initrd.img-3.13.0-44-generic
abi-3.13.0-34-generic         memtest86+.bin
abi-3.13.0-35-generic         memtest86+.elf
abi-3.13.0-37-generic         memtest86+_multiboot.bin
abi-3.13.0-39-generic         System.map-3.13.0-32-generic
abi-3.13.0-40-generic         System.map-3.13.0-34-generic
abi-3.13.0-43-generic         System.map-3.13.0-35-generic
abi-3.13.0-44-generic         System.map-3.13.0-37-generic
config-3.13.0-32-generic      System.map-3.13.0-39-generic
config-3.13.0-34-generic      System.map-3.13.0-40-generic
config-3.13.0-35-generic      System.map-3.13.0-43-generic
config-3.13.0-37-generic      System.map-3.13.0-44-generic
config-3.13.0-39-generic      vmlinuz-3.13.0-32-generic
config-3.13.0-40-generic      vmlinuz-3.13.0-34-generic
config-3.13.0-43-generic      vmlinuz-3.13.0-35-generic
config-3.13.0-44-generic      vmlinuz-3.13.0-37-generic
grub                          vmlinuz-3.13.0-39-generic
initrd.img-3.13.0-39-generic  vmlinuz-3.13.0-40-generic
initrd.img-3.13.0-40-generic  vmlinuz-3.13.0-43-generic
initrd.img-3.13.0-43-generic  vmlinuz-3.13.0-44-generic
dave@dave-Satellite-A135:/boot$ 
```





Thank you,
I know have 95.2 MB available in boot,

---

### Post by Bashing-om on 2015-02-10
dave-borkowskijr-z; Hey;

Please , code tags .. Have you any idea how many postings we read in a days work !
The use of code tags retains the formatting to promote the readability of the 'code' .
Please edit your last to enable my tired poor eyes to see, and my overloaded mind to comprehend what I can see.
a [noparse]```
[/noparse] at the start
a[noparse]
```[/noparse] at the end
will do that nicely.

[INDENT][INDENT]then we carry on
[/INDENT][/INDENT]

---

### Post by dave-borkowskijr-z on 2015-02-10
every time i try to reply my browser crashes 

one more try with less info

you are fixing it
thank you

software update ran succsesfully now

currently 
```

 dpkg -l | grep linux-image-

```
pi  linux-image-3.13.0-32-generic                               3.13.0-32.57                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
pi  linux-image-3.13.0-34-generic                               3.13.0-34.60                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
pi  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
pi  linux-image-3.13.0-37-generic                               3.13.0-37.64                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
pi  linux-image-3.13.0-39-generic                               3.13.0-39.66                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
pi  linux-image-3.13.0-40-generic                               3.13.0-40.69                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-43-generic                               3.13.0-43.72                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                               3.13.0-44.73                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-45-generic                               3.13.0-45.74                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                         3.13.0-43.72                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                         3.13.0-44.73                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                         3.13.0-45.74                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                         3.13.0.45.52                                        i386         Generic Linux kernel image

---

### Post by dave-borkowskijr-z on 2015-02-10
do i want to do something like this now
```


linux-image-3.13.0-{43,44,45,72}-generic sudo dpkg -P
linux-image-extra-3.13.0-{43,44,45,72}-generic sudo dpkg -P
linux-headers-3.13.0-{43,44,45,72}-generic sudo dpkg -P
linux-headers-3.13.0-{43,44,45,72}

```

---

### Post by Bashing-om on 2015-02-10
dave-borkowskijr-z; OK;

Looking better. (thanks, code tags do help).

From what I can gather in your post #6 still do not have enough head room to operate with,
and we still have these to deal with:
```

pi linux-image-3.13.0-32-generic 3.13.0-32.57 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP
pi linux-image-3.13.0-34-generic 3.13.0-34.60 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP
pi linux-image-3.13.0-35-generic 3.13.0-35.62 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP
pi linux-image-3.13.0-37-generic 3.13.0-37.64 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP
pi linux-image-3.13.0-39-generic 3.13.0-39.66 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP
pi linux-image-3.13.0-40-generic 3.13.0-40.69 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP

```

Before we go on, what kernel are your booting presently? Post back - Between code tags - :
```

uname -r

```

This looks real good, to have the latest kernel fully installed !
```

ii linux-image-3.13.0-45-generic 3.13.0-45.74 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP

```
And what now results with terminal command:
```

sudo apt-get autoremove

```

[INDENT][INDENT]look'n better alla the time - maybe justa bit of clean up
[INDENT][INDENT][INDENT]we will get there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dave-borkowskijr-z on 2015-02-10
```

  pi linux-image-3.13.0-32-generic 3.13.0-32.57 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 
```
 The program 'pi' is currently not installed. You can install it by typing: 
 sudo apt-get install pi 
 

 ```

 pi linux-image-3.13.0-34-generic 3.13.0-34.60 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 
```
 The program 'pi' is currently not installed. You can install it by typing: 
 sudo apt-get install pi 
 

 ```

  pi linux-image-3.13.0-35-generic 3.13.0-35.62 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 
```
 The program 'pi' is currently not installed. You can install it by typing: 
 sudo apt-get install pi 
 

 ```
pi linux-image-3.13.0-37-generic 3.13.0-37.64 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 
```
 The program 'pi' is currently not installed. You can install it by typing: 
 sudo apt-get install pi 
 

 ```
 pi linux-image-3.13.0-39-generic 3.13.0-39.66 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 

 
```
 The program 'pi' is currently not installed. You can install it by typing: 
 sudo apt-get install pi 
 ```

 pi linux-image-3.13.0-40-generic 3.13.0-40.69 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP
 
``` 
 The program 'pi' is currently not installed. You can install it by typing: 
 sudo apt-get install pi 
 ```
uname -r 
```
 3.13.0-45-generic 
   ```

 ii linux-image-3.13.0-45-generic 3.13.0-45.74
i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
```
 This seems to do nothing  there was no output and I have to “control C” to get my cursor back
 

 

  
 ```

 sudo apt-get autoremove 
```
  [sudo] password for dave:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.

---

### Post by Bashing-om on 2015-02-10
dave-borkowskijr-z; Hey, hey.

Easy now, sorry if I confused you.
--------------------------
clear and reset;
--------------------------------
OK, we are at a good point:
up and running on the latest kernel.
There is still this condition:
> 
0 upgraded, 0 newly installed, 0 to remove and [color=red]14 not upgraded[/color].

Let's get a fresh look at things;
Post back now:
```

df -h
dpkg -l | grep linux-
ls -al /boot

```
I have a procedure in mind .. depending on the status of the system.

[INDENT][INDENT]almost home free
[/INDENT][/INDENT]

---

### Post by dave-borkowskijr-z on 2015-02-10
I let this run for about 10 minutes and it came back with this


```

ii linux-image-3.13.0-45-generic 3.13.0-45.74 i386 Linux kernel image for version 3.13.0 on 32 bit x86 SMP

```

ii: remote host closed connection: File exists

---

### Post by Yellow Pasque on 2015-02-10
You seem to be struggling mightily with the command line. (You're copying/pasting everything in sight and trying to run it as a command) 

I suggest using Synaptic, which will require a couple of commands to install:
```
sudo apt-get install -y --no-install-recommends synaptic gksu
gksu synaptic
```

Now you can search for "linux-image" (no quotes), and click the "Installed Version" column header once or twice to bring all those old kernels to the top of the list. From there, you can right-click them and mark them for removal. Just make sure you don't try to remove your current kernel (-45).

---

### Post by dave-borkowskijr-z on 2015-02-10
```

 df -h 
```
 Filesystem                   Size  Used Avail Use% Mounted on 
 /dev/mapper/ubuntu--vg-root  456G  110G  323G  26% / 
 none                         4.0K     0  4.0K   0% /sys/fs/cgroup 
 udev                         1.5G  4.0K  1.5G   1% /dev 
 tmpfs                        303M  1.3M  301M   1% /run 
 none                         5.0M     0  5.0M   0% /run/lock 
 none                         1.5G  156K  1.5G   1% /run/shm 
 none                         100M   32K  100M   1% /run/user 
 /dev/sda1                    236M  161M   63M  72% /boot 
 dave@dave-Satellite-A135:~$  
 ```

 dpkg -l | grep linux- 
```
 ii  linux-firmware                                              1.127.11                                            all          Firmware for Linux kernel drivers 
 ii  linux-generic                                               3.13.0.45.52                                        i386         Complete Generic Linux kernel and headers 
 ii  linux-headers-3.13.0-43                                     3.13.0-43.72                                        all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-43-generic                             3.13.0-43.72                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP 
 ii  linux-headers-3.13.0-44                                     3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-44-generic                             3.13.0-44.73                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP 
 ii  linux-headers-3.13.0-45                                     3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-45-generic                             3.13.0-45.74                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP 
 ii  linux-headers-generic                                       3.13.0.45.52                                        i386         Generic Linux kernel headers 
 pi  linux-image-3.13.0-32-generic                               3.13.0-32.57                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 pi  linux-image-3.13.0-34-generic                               3.13.0-34.60                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 pi  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 pi  linux-image-3.13.0-37-generic                               3.13.0-37.64                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 pi  linux-image-3.13.0-39-generic                               3.13.0-39.66                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 pi  linux-image-3.13.0-40-generic                               3.13.0-40.69                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 ii  linux-image-3.13.0-43-generic                               3.13.0-43.72                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 ii  linux-image-3.13.0-44-generic                               3.13.0-44.73                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 ii  linux-image-3.13.0-45-generic                               3.13.0-45.74                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
 ii  linux-image-extra-3.13.0-43-generic                         3.13.0-43.72                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP 
 ii  linux-image-extra-3.13.0-44-generic                         3.13.0-44.73                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP 
 ii  linux-image-extra-3.13.0-45-generic                         3.13.0-45.74                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP 
 ii  linux-image-generic                                         3.13.0.45.52                                        i386         Generic Linux kernel image 
 ii  linux-libc-dev:i386                                         3.13.0-45.74                                        i386         Linux Kernel Headers for development 
 ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems 
 ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files) 
 ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies 
 dave@dave-Satellite-A135:~$  
 ```

 ls -al /boot 
```
 total 157893 
 drwxr-xr-x  4 root root     4096 Feb 10 19:46 . 
 drwxr-xr-x 22 root root     4096 Feb 10 19:45 .. 
 -rw-r--r--  1 root root  1166929 Jul 15  2014 abi-3.13.0-32-generic 
 -rw-r--r--  1 root root  1166929 Aug 13 12:58 abi-3.13.0-34-generic 
 -rw-r--r--  1 root root  1168075 Aug 14 23:09 abi-3.13.0-35-generic 
 -rw-r--r--  1 root root  1168706 Sep 22 18:42 abi-3.13.0-37-generic 
 -rw-r--r--  1 root root  1168764 Oct 28 10:43 abi-3.13.0-39-generic 
 -rw-r--r--  1 root root  1168726 Nov 13 14:03 abi-3.13.0-40-generic 
 -rw-r--r--  1 root root  1168937 Dec  8 15:38 abi-3.13.0-43-generic 
 -rw-r--r--  1 root root  1168937 Dec 15 20:27 abi-3.13.0-44-generic 
 -rw-r--r--  1 root root  1169184 Jan 13 15:23 abi-3.13.0-45-generic 
 -rw-r--r--  1 root root   169732 Jul 15  2014 config-3.13.0-32-generic 
 -rw-r--r--  1 root root   169732 Aug 13 12:58 config-3.13.0-34-generic 
 -rw-r--r--  1 root root   169722 Aug 14 23:09 config-3.13.0-35-generic 
 -rw-r--r--  1 root root   169782 Sep 22 18:42 config-3.13.0-37-generic 
 -rw-r--r--  1 root root   169782 Oct 28 10:43 config-3.13.0-39-generic 
 -rw-r--r--  1 root root   169815 Nov 13 14:03 config-3.13.0-40-generic 
 -rw-r--r--  1 root root   169815 Dec  8 15:38 config-3.13.0-43-generic 
 -rw-r--r--  1 root root   169818 Dec 15 20:27 config-3.13.0-44-generic 
 -rw-r--r--  1 root root   169818 Jan 13 15:23 config-3.13.0-45-generic 
 drwxr-xr-x  5 root root     1024 Feb 10 19:46 grub 
 -rw-r--r--  1 root root  6480281 Feb 10 19:36 initrd.img-3.13.0-39-generic 
 -rw-r--r--  1 root root  6481946 Feb 10 19:36 initrd.img-3.13.0-40-generic 
 -rw-r--r--  1 root root 19563739 Jan  6 17:17 initrd.img-3.13.0-43-generic 
 -rw-r--r--  1 root root 19563336 Feb 10 19:46 initrd.img-3.13.0-44-generic 
 -rw-r--r--  1 root root 19571478 Feb 10 19:45 initrd.img-3.13.0-45-generic 
 drwx------  2 root root     1024 Feb 10 20:46 lost+found 
 -rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin 
 -rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf 
 -rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin 
 -rw-------  1 root root  2693057 Jul 15  2014 System.map-3.13.0-32-generic 
 -rw-------  1 root root  2693057 Aug 13 12:58 System.map-3.13.0-34-generic 
 -rw-------  1 root root  2697306 Aug 14 23:09 System.map-3.13.0-35-generic 
 -rw-------  1 root root  2697489 Sep 22 18:42 System.map-3.13.0-37-generic 
 -rw-------  1 root root  2697539 Oct 28 10:43 System.map-3.13.0-39-generic 
 -rw-------  1 root root  2697648 Nov 13 14:03 System.map-3.13.0-40-generic 
 -rw-------  1 root root  2699011 Dec  8 15:38 System.map-3.13.0-43-generic 
 -rw-------  1 root root  2699036 Dec 15 20:27 System.map-3.13.0-44-generic 
 -rw-------  1 root root  2699380 Jan 13 15:23 System.map-3.13.0-45-generic 
 -rw-r--r--  1 root root  5820336 Jul 22  2014 vmlinuz-3.13.0-32-generic 
 -rw-------  1 root root  5820592 Aug 13 12:58 vmlinuz-3.13.0-34-generic 
 -rw-------  1 root root  5826864 Aug 14 23:09 vmlinuz-3.13.0-35-generic 
 -rw-------  1 root root  5828976 Sep 22 18:42 vmlinuz-3.13.0-37-generic 
 -rw-------  1 root root  5828720 Oct 28 10:43 vmlinuz-3.13.0-39-generic 
 -rw-------  1 root root  5830128 Nov 13 14:03 vmlinuz-3.13.0-40-generic 
 -rw-------  1 root root  5833296 Dec  8 15:38 vmlinuz-3.13.0-43-generic 
 -rw-------  1 root root  5833648 Dec 15 20:27 vmlinuz-3.13.0-44-generic 
 -rw-------  1 root root  5833648 Jan 13 15:23 vmlinuz-3.13.0-45-generic

---

### Post by dave-borkowskijr-z on 2015-02-10
yes i do strugle with terminal commands.  At one point before KDE and YAST I could struggle through.  That being said i apriciate all you have done for me tongiht.
If you ever find a time that you need help with Fanuc robotics, I'm your man, look me up.

That being said...

```

gksu synaptic

```
asks me for root password and I don't recall ever setting one.  

I have always had this problem with 
```

su

```

---

### Post by Yellow Pasque on 2015-02-10
It's just your user's password.

> If you ever find a time that you need help with Fanuc robotics
Heh, I once operated some Fanuc machines (milling and lathe). I miss that job :(

---

### Post by Bashing-om on 2015-02-10
dave-borkowskijr-z;  Hey !

Panic not. Just proceed in a calm and orderly fashion.

Following Temüjin's lead to use 'synaptic' as an easier alternative to the command line.
The password that you will use is the password you set when you installed the operating system initially.
You were asked to provide a "username"
and next the 'password'. then had to confirm that 'password'. Remember ?

That is the password that you must use for all administrative functions.

Back harping on code tags:
re read:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
We want not only the terminal command, but more importantly, the outputs of terminal commands enclosed in code tags .

Happy to oblige 
[INDENT][INDENT]make t[/INDENT][/INDENT]

---

### Post by dave-borkowskijr-z on 2015-02-11
OK so funny thing about that password problem

if I su and type in my user password I get this
```
 
dave@dave-Satellite-A135:~$ su
Password: 
su: Authentication failure

```

but if i sudo su and use the same user password i get there.
```

dave@dave-Satellite-A135:~$ sudo su
[sudo] password for dave: 
root@dave-Satellite-A135:/home/dave# sudo gksu synaptic

```

So I will go out reading documentation involving synaptic.

Thank you

further update.
synaptic removed all the rest of of my kernal files with the exception of the current and one single previous one,
I now have about 165MB available in /boot.

Thanks again.

---

### Post by Yellow Pasque on 2015-02-11
Mark the thread solved (under the thread tools menu above the first post).

> if I su and type in my user password I get this
Root account is disabled by default: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

