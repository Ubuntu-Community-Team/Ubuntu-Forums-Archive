---
title: "broken package"
date: 2016-10-12
forum: General Help
---

### Post by czgirb on 2016-10-12
today, i update my 14.04 and my network was error in a middle.
how can i fix this? please guide me ...
thank you in advance

I've tried:
```
czgirb@ubuntu:~$ sudo apt-get update
[sudo] password for czgirb: 
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://id.archive.ubuntu.com trusty InRelease                              
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:1 http://security.ubuntu.com trusty-security InRelease [65.9 kB]           
Hit http://archive.canonical.com trusty Release.gpg                            
Get:2 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Get:3 http://id.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.getdeb.net trusty-getdeb InRelease                          
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Get:4 http://security.ubuntu.com trusty-security/main Sources [120 kB]         
Hit http://id.archive.ubuntu.com trusty-backports InRelease                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                 
Hit http://id.archive.ubuntu.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:5 http://id.archive.ubuntu.com trusty-updates/main Sources [383 kB]        
Get:6 http://security.ubuntu.com trusty-security/restricted Sources [4,064 B]  
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:7 http://security.ubuntu.com trusty-security/universe Sources [44.3 kB]    
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:8 http://security.ubuntu.com trusty-security/multiverse Sources [3,201 B]  
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:9 http://id.archive.ubuntu.com trusty-updates/restricted Sources [5,360 B] 
Get:10 http://security.ubuntu.com trusty-security/main i386 Packages [497 kB]  
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:11 http://id.archive.ubuntu.com trusty-updates/universe Sources [166 kB]   
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Get:12 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:13 http://security.ubuntu.com trusty-security/universe i386 Packages [140 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US             
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                
Get:14 http://id.archive.ubuntu.com trusty-updates/multiverse Sources [7,511 B]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:15 http://id.archive.ubuntu.com trusty-updates/main i386 Packages [866 kB] 
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:16 http://security.ubuntu.com trusty-security/multiverse i386 Packages [5,348 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:17 http://id.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:18 http://id.archive.ubuntu.com trusty-updates/universe i386 Packages [377 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:19 http://id.archive.ubuntu.com trusty-updates/multiverse i386 Packages [15.4 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://id.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://id.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://id.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://id.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://id.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://id.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://id.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://id.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://id.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://id.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://id.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://id.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://id.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://id.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://id.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://id.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://id.archive.ubuntu.com trusty Release                                
Hit http://id.archive.ubuntu.com trusty/main Sources                           
Hit http://id.archive.ubuntu.com trusty/restricted Sources                     
Hit http://id.archive.ubuntu.com trusty/universe Sources                       
Hit http://id.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://id.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://id.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://id.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://id.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://id.archive.ubuntu.com trusty/main Translation-en                    
Hit http://id.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://id.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://id.archive.ubuntu.com trusty/universe Translation-en                
Ign http://id.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://id.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://id.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://id.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 2,795 kB in 24s (113 kB/s)                                             
Reading package lists... Done

czgirb@ubuntu:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

czgirb@ubuntu:~$ sudo apt-get clean

czgirb@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.13.0-98-generic but it is not installed
E: Unmet dependencies. Try using -f.

czgirb@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.13.0-98 linux-headers-3.13.0-98-generic
The following NEW packages will be installed:
  linux-headers-3.13.0-98 linux-headers-3.13.0-98-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 9,568 kB of archives.
After this operation, 76.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://id.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-98 all 3.13.0-98.145 [8,878 kB]
Get:2 http://id.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-98-generic i386 3.13.0-98.145 [690 kB]
Fetched 9,568 kB in 11s (843 kB/s)                                             
(Reading database ... 1187720 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.13.0-98_3.13.0-98.145_all.deb ...
Unpacking linux-headers-3.13.0-98 (3.13.0-98.145) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-98_3.13.0-98.145_all.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.13.0-98/arch/blackfin/mach-bf527/boards': No space left on device
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-headers-3.13.0-98-generic_3.13.0-98.145_i386.deb ...
Unpacking linux-headers-3.13.0-98-generic (3.13.0-98.145) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-98-generic_3.13.0-98.145_i386.deb (--unpack):
 error creating symbolic link `./usr/src/linux-headers-3.13.0-98-generic/include/linux/if_pppox.h': No space left on device
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.13.0-98_3.13.0-98.145_all.deb
 /var/cache/apt/archives/linux-headers-3.13.0-98-generic_3.13.0-98.145_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
czgirb@ubuntu:~$ 

```

---

### Post by Bashing-om on 2016-10-12
czgirb; Hello;

Indications are that you have filled up the /boot space allotment.

> 
/arch/blackfin/mach-bf527/boards': No space left on device

As no space left to work in, can not install the latest kernel.

show:
```

df -h
df -i
dpkg -l | grep linux-
ls -al /boot/

```
And we see what must be done to get some elbow room.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2016-10-12
What dose the terminal report with these two commands..(Paste back both please)
```
df -h
```
And this also
```
dpkg -l | grep linux-image
```
Ninjed by Bashing-om;)

---

### Post by czgirb on 2016-10-12
as I remembered.
the item which want to be installed is 62MB, currently there is still 2.3GB empty space left in my "/"
it should enough right?


as requested

```
czgirb@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            981M  4.0K  981M   1% /dev
tmpfs           199M  1.3M  197M   1% /run
/dev/sda1        19G   16G  2.0G  89% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            991M  1.3M  989M   1% /run/shm
none            100M   60K  100M   1% /run/user
/dev/sda4       190G  171G  9.6G  95% /media/czgirb/207GB
/dev/sdb1       459G  435G  533M 100% /media/czgirb/500GB

czgirb@ubuntu:~$ dpkg -l | grep linux-image
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-51-generic                         3.13.0-51.84                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-53-generic                         3.13.0-53.89                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-54-generic                         3.13.0-54.91                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.106                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-77-generic                         3.13.0-77.121                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-79-generic                         3.13.0-79.123                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-83-generic                         3.13.0-83.127                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-85-generic                         3.13.0-85.129                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-86-generic                         3.13.0-86.131                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-87-generic                         3.13.0-87.133                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-88-generic                         3.13.0-88.135                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-91-generic                         3.13.0-91.138                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-92-generic                         3.13.0-92.139                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-93-generic                         3.13.0-93.140                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-95-generic                         3.13.0-95.142                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-96-generic                         3.13.0-96.143                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-98-generic                         3.13.0-98.145                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic                   3.13.0-51.84                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                   3.13.0-53.89                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                   3.13.0-54.91                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.106                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                   3.13.0-77.121                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                   3.13.0-79.123                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic                   3.13.0-83.127                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-85-generic                   3.13.0-85.129                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-86-generic                   3.13.0-86.131                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-87-generic                   3.13.0-87.133                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-88-generic                   3.13.0-88.135                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-91-generic                   3.13.0-91.138                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-92-generic                   3.13.0-92.139                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-93-generic                   3.13.0-93.140                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-95-generic                   3.13.0-95.142                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-96-generic                   3.13.0-96.143                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-98-generic                   3.13.0-98.145                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                   3.13.0.98.106                                       i386         Generic Linux kernel image
czgirb@ubuntu:~$ 

```

---

### Post by howefield on 2016-10-13
Try running 

```
sudo apt-get autoremove
```

If you are lucky it will remove some of those old kernels, if you are not lucky they will need to be removed manually, not difficult but try the easy autoremove first.

---

### Post by Impavidus on 2016-10-13
You may have run out of inodes. The file system not only has a limit for the total size of the files, but also for the number of files. As Bashing-om suggested, run```
df -i
``` to check.

You have accumulated a lot of old kernels and, probably, header packages. You may be able to autoremove them with```
sudo apt-get autoremove
```else, use```
dpkg -l | grep -E 'linux-(headers|image)'
```to get a list of those old packages and we can help you with a way to remove them using the lower-level dpkg command.

---

### Post by czgirb on 2016-10-14
> **howefield said:**
> Try running 

```
sudo apt-get autoremove
```

If you are lucky it will remove some of those old kernels, if you are not lucky they will need to be removed manually, not difficult but try the easy autoremove first.

as requested:
```

czgirb@ubuntu:~$ sudo apt-get autoremove
[sudo] password for czgirb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.13.0-98-generic but it is not installed
E: Unmet dependencies. Try using -f.

czgirb@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.13.0-98 linux-headers-3.13.0-98-generic
The following NEW packages will be installed:
  linux-headers-3.13.0-98 linux-headers-3.13.0-98-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/9,568 kB of archives.
After this operation, 76.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 1187720 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.13.0-98_3.13.0-98.145_all.deb ...
Unpacking linux-headers-3.13.0-98 (3.13.0-98.145) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-98_3.13.0-98.145_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.13.0-98/arch/avr32/mach-at32ap/include/mach/init.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-98/arch/avr32/mach-at32ap/include/mach/init.h'): No space left on device
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-headers-3.13.0-98-generic_3.13.0-98.145_i386.deb ...
Unpacking linux-headers-3.13.0-98-generic (3.13.0-98.145) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-98-generic_3.13.0-98.145_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.13.0-98-generic/include/config/media/tuner/tea5767.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-98-generic/include/config/media/tuner/tea5767.h'): No space left on device
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.13.0-98_3.13.0-98.145_all.deb
 /var/cache/apt/archives/linux-headers-3.13.0-98-generic_3.13.0-98.145_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
czgirb@ubuntu:~$ 

```

---

### Post by czgirb on 2016-10-14
> **Impavidus said:**
> You may have run out of inodes. The file system not only has a limit for the total size of the files, but also for the number of files. As Bashing-om suggested, run```
df -i
``` to check.

You have accumulated a lot of old kernels and, probably, header packages. You may be able to autoremove them with```
sudo apt-get autoremove
```else, use```
dpkg -l | grep -E 'linux-(headers|image)'
```to get a list of those old packages and we can help you with a way to remove them using the lower-level dpkg command.

as requested
sorry for a late reply

```

czgirb@ubuntu:~$ df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             215364     546   214818    1% /dev
tmpfs            220173     578   219595    1% /run
/dev/sda1       1222992 1216153     6839  100% /
none             220173       2   220171    1% /sys/fs/cgroup
none             220173       3   220170    1% /run/lock
none             220173       9   220164    1% /run/shm
none             220173      32   220141    1% /run/user
/dev/sda4      12664832   26635 12638197    1% /media/czgirb/207GB
/dev/sdb1      30531584   47290 30484294    1% /media/czgirb/500GB

czgirb@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.13.0-98-generic but it is not installed
E: Unmet dependencies. Try using -f.

czgirb@ubuntu:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

czgirb@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.13.0-98 linux-headers-3.13.0-98-generic
The following NEW packages will be installed:
  linux-headers-3.13.0-98 linux-headers-3.13.0-98-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/9,568 kB of archives.
After this operation, 76.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 1187720 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.13.0-98_3.13.0-98.145_all.deb ...
Unpacking linux-headers-3.13.0-98 (3.13.0-98.145) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-98_3.13.0-98.145_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.13.0-98/arch/avr32/mm/Makefile.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-98/arch/avr32/mm/Makefile'): No space left on device
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-headers-3.13.0-98-generic_3.13.0-98.145_i386.deb ...
Unpacking linux-headers-3.13.0-98-generic (3.13.0-98.145) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-98-generic_3.13.0-98.145_i386.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.13.0-98-generic/include/config/media/digital/tv': No space left on device
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.13.0-98_3.13.0-98.145_all.deb
 /var/cache/apt/archives/linux-headers-3.13.0-98-generic_3.13.0-98.145_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

czgirb@ubuntu:~$ dpkg -l | grep -E 'linux-(headers|image)'
ii  linux-headers-3.13.0-37                               3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                       3.13.0-37.64                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-39                               3.13.0-39.66                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                       3.13.0-39.66                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-40                               3.13.0-40.69                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic                       3.13.0-40.69                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-43                               3.13.0-43.72                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                       3.13.0-43.72                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-44                               3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                       3.13.0-44.73                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-45                               3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                       3.13.0-45.74                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.83                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.83                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-51                               3.13.0-51.84                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                       3.13.0-51.84                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                               3.13.0-52.86                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.86                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                               3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                       3.13.0-53.89                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-54                               3.13.0-54.91                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                       3.13.0-54.91                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                               3.13.0-55.94                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.94                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                               3.13.0-57.95                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                       3.13.0-57.95                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-58                               3.13.0-58.97                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                       3.13.0-58.97                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-59                               3.13.0-59.98                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                       3.13.0-59.98                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                               3.13.0-61.100                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                       3.13.0-61.100                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-62                               3.13.0-62.102                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                       3.13.0-62.102                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.106                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.106                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-66                               3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                       3.13.0-66.108                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-77                               3.13.0-77.121                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                       3.13.0-77.121                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-79                               3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                       3.13.0-79.123                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-83                               3.13.0-83.127                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic                       3.13.0-83.127                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-85                               3.13.0-85.129                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic                       3.13.0-85.129                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-86                               3.13.0-86.131                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic                       3.13.0-86.131                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-87                               3.13.0-87.133                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-87-generic                       3.13.0-87.133                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-88                               3.13.0-88.135                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-88-generic                       3.13.0-88.135                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-91                               3.13.0-91.138                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-91-generic                       3.13.0-91.138                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-92                               3.13.0-92.139                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-92-generic                       3.13.0-92.139                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-93                               3.13.0-93.140                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-93-generic                       3.13.0-93.140                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-95                               3.13.0-95.142                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-95-generic                       3.13.0-95.142                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-96                               3.13.0-96.143                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-96-generic                       3.13.0-96.143                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
iU  linux-headers-generic                                 3.13.0.98.106                                       i386         Generic Linux kernel headers
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-51-generic                         3.13.0-51.84                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-53-generic                         3.13.0-53.89                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-54-generic                         3.13.0-54.91                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.106                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-77-generic                         3.13.0-77.121                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-79-generic                         3.13.0-79.123                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-83-generic                         3.13.0-83.127                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-85-generic                         3.13.0-85.129                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-86-generic                         3.13.0-86.131                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-87-generic                         3.13.0-87.133                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-88-generic                         3.13.0-88.135                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-91-generic                         3.13.0-91.138                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-92-generic                         3.13.0-92.139                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-93-generic                         3.13.0-93.140                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-95-generic                         3.13.0-95.142                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-96-generic                         3.13.0-96.143                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-98-generic                         3.13.0-98.145                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic                   3.13.0-51.84                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                   3.13.0-53.89                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                   3.13.0-54.91                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.106                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                   3.13.0-77.121                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                   3.13.0-79.123                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic                   3.13.0-83.127                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-85-generic                   3.13.0-85.129                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-86-generic                   3.13.0-86.131                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-87-generic                   3.13.0-87.133                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-88-generic                   3.13.0-88.135                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-91-generic                   3.13.0-91.138                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-92-generic                   3.13.0-92.139                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-93-generic                   3.13.0-93.140                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-95-generic                   3.13.0-95.142                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-96-generic                   3.13.0-96.143                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-98-generic                   3.13.0-98.145                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                   3.13.0.98.106                                       i386         Generic Linux kernel image
czgirb@ubuntu:~$ 

```

---

### Post by Impavidus on 2016-10-14
So, you indeed ran out of inodes. That's caused by the header packages. Get rid of a bunch of old header packages:```

sudo dpkg --purge linux-headers-3.13.0-{37,39,40,43,44,45,46}{,-generic}
```Then try fixing the package manager:```

sudo apt-get -f install
```If that works, try autoremove:```
sudo apt-get autoremove --purge
```That should get rid of most of your old headers and kernels. Run```
dpkg -l | grep -E 'linux-(headers|image)'
```to check.

---

### Post by czgirb on 2016-10-15
here is the outcome ... please let me know the result

```

czgirb@ubuntu:~$ sudo dpkg --purge linux-headers-3.13.0-{37,39,40,43,44,45,46}{,-generic}
[sudo] password for czgirb: 
(Reading database ... 1187719 files and directories currently installed.)
Removing linux-headers-3.13.0-37-generic (3.13.0-37.64) ...
Removing linux-headers-3.13.0-39-generic (3.13.0-39.66) ...
Removing linux-headers-3.13.0-40-generic (3.13.0-40.69) ...
Removing linux-headers-3.13.0-43-generic (3.13.0-43.72) ...
Removing linux-headers-3.13.0-44-generic (3.13.0-44.73) ...
Removing linux-headers-3.13.0-45-generic (3.13.0-45.74) ...
Removing linux-headers-3.13.0-46-generic (3.13.0-46.79) ...
Removing linux-headers-3.13.0-37 (3.13.0-37.64) ...
Removing linux-headers-3.13.0-39 (3.13.0-39.66) ...
Removing linux-headers-3.13.0-40 (3.13.0-40.69) ...
Removing linux-headers-3.13.0-43 (3.13.0-43.72) ...
Removing linux-headers-3.13.0-44 (3.13.0-44.73) ...
Removing linux-headers-3.13.0-45 (3.13.0-45.74) ...
Removing linux-headers-3.13.0-46 (3.13.0-46.79) ...

czgirb@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.13.0-98 linux-headers-3.13.0-98-generic
The following NEW packages will be installed:
  linux-headers-3.13.0-98 linux-headers-3.13.0-98-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/9,568 kB of archives.
After this operation, 76.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 1013199 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.13.0-98_3.13.0-98.145_all.deb ...
Unpacking linux-headers-3.13.0-98 (3.13.0-98.145) ...
Preparing to unpack .../linux-headers-3.13.0-98-generic_3.13.0-98.145_i386.deb ...
Unpacking linux-headers-3.13.0-98-generic (3.13.0-98.145) ...
Setting up linux-headers-3.13.0-98 (3.13.0-98.145) ...
Setting up linux-headers-3.13.0-98-generic (3.13.0-98.145) ...
Setting up linux-headers-generic (3.13.0.98.106) ...
Setting up linux-generic (3.13.0.98.106) ...

czgirb@ubuntu:~$ sudo apt-get autoremove --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

czgirb@ubuntu:~$ dpkg -l | grep -E 'linux-(headers|image)'
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.83                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.83                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-51                               3.13.0-51.84                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                       3.13.0-51.84                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                               3.13.0-52.86                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.86                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                               3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                       3.13.0-53.89                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-54                               3.13.0-54.91                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                       3.13.0-54.91                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                               3.13.0-55.94                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.94                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                               3.13.0-57.95                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                       3.13.0-57.95                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-58                               3.13.0-58.97                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                       3.13.0-58.97                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-59                               3.13.0-59.98                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                       3.13.0-59.98                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                               3.13.0-61.100                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                       3.13.0-61.100                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-62                               3.13.0-62.102                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                       3.13.0-62.102                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.106                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.106                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-66                               3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                       3.13.0-66.108                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-77                               3.13.0-77.121                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                       3.13.0-77.121                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-79                               3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                       3.13.0-79.123                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-83                               3.13.0-83.127                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic                       3.13.0-83.127                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-85                               3.13.0-85.129                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic                       3.13.0-85.129                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-86                               3.13.0-86.131                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic                       3.13.0-86.131                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-87                               3.13.0-87.133                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-87-generic                       3.13.0-87.133                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-88                               3.13.0-88.135                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-88-generic                       3.13.0-88.135                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-91                               3.13.0-91.138                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-91-generic                       3.13.0-91.138                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-92                               3.13.0-92.139                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-92-generic                       3.13.0-92.139                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-93                               3.13.0-93.140                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-93-generic                       3.13.0-93.140                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-95                               3.13.0-95.142                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-95-generic                       3.13.0-95.142                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-96                               3.13.0-96.143                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-96-generic                       3.13.0-96.143                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-98                               3.13.0-98.145                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-98-generic                       3.13.0-98.145                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.98.106                                       i386         Generic Linux kernel headers
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-51-generic                         3.13.0-51.84                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-53-generic                         3.13.0-53.89                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-54-generic                         3.13.0-54.91                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.106                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-77-generic                         3.13.0-77.121                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-79-generic                         3.13.0-79.123                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-83-generic                         3.13.0-83.127                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-85-generic                         3.13.0-85.129                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-86-generic                         3.13.0-86.131                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-87-generic                         3.13.0-87.133                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-88-generic                         3.13.0-88.135                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-91-generic                         3.13.0-91.138                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-92-generic                         3.13.0-92.139                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-93-generic                         3.13.0-93.140                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-95-generic                         3.13.0-95.142                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-96-generic                         3.13.0-96.143                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-98-generic                         3.13.0-98.145                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic                   3.13.0-51.84                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                   3.13.0-53.89                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                   3.13.0-54.91                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.106                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                   3.13.0-77.121                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                   3.13.0-79.123                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic                   3.13.0-83.127                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-85-generic                   3.13.0-85.129                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-86-generic                   3.13.0-86.131                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-87-generic                   3.13.0-87.133                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-88-generic                   3.13.0-88.135                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-91-generic                   3.13.0-91.138                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-92-generic                   3.13.0-92.139                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-93-generic                   3.13.0-93.140                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-95-generic                   3.13.0-95.142                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-96-generic                   3.13.0-96.143                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-98-generic                   3.13.0-98.145                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                   3.13.0.98.106                                       i386         Generic Linux kernel image
czgirb@ubuntu:~$ 

```

---

### Post by Impavidus on 2016-10-15
That fixed your package manager, but it didn't autoremove the old packages. Try it manually:```

sudo apt-get purge linux-image{,-extra}-3.13.0-{37,39,40,43,44,45,46}-generic
sudo apt-get purge linux-headers-3.13.0-{48,49,51,52,53,54,55,57,58,59}{,-generic}
sudo apt-get purge linux-image{,-extra}-3.13.0-{48,49,51,52,53,54,55,57,58,59}-generic
sudo apt-get purge linux-headers-3.13.0-{61,62,63,65,66,77,79,83,85}{,-generic}
sudo apt-get purge linux-image{,-extra}-3.13.0-{61,62,63,65,66,77,79,83,85}-generic
sudo apt-get purge linux-headers-3.13.0-{86,87,88,91,92,93,95}{,-generic}
sudo apt-get purge linux-image{,-extra}-3.13.0-{86,87,88,91,92,93,95}-generic
```
This will take a while. I used shell expansion to get the names of all packages, but spread them over a few lines to prevent errors about too many arguments. I've seen those happen.

---

