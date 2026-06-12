---
title: "Kernal update error"
date: 2012-11-29
forum: General Help
---

### Post by lunaphiles on 2012-11-29
I encountered this problem previously, and resorted to reinstalling to fix it.
I cam across a thread where they asked for this series of commands - still did not work.

Anybody got any ideas on how to fix?

```
guest@netbook:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
guest@netbook:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
guest@netbook:~$ sudo mv /var/lib/dpkg/available /var/lib/dpkg/available-bad
guest@netbook:~$ sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
guest@netbook:~$ sudo rm -rf /var/lib/dpkg/updates/*
guest@netbook:~$ sudo rm -rf /var/lib/apt/lists/*
guest@netbook:~$ sudo mkdir /var/lib/apt/lists/partial
guest@netbook:~$ sudo rm /var/cache/apt/*.bin
guest@netbook:~$ sudo apt-get clean
guest@netbook:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-33-generic-pae but it is not installable
E: Unmet dependencies. Try using -f.
guest@netbook:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease                                                  
Ign http://us.archive.ubuntu.com precise-backports InRelease                                                 
Get:1 http://us.archive.ubuntu.com precise Release.gpg [198 B]                                               
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]                                          
Get:3 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]                                        
Get:4 http://us.archive.ubuntu.com precise Release [49.6 kB]                                                 
Get:5 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]         
Ign http://security.ubuntu.com precise-security InRelease
Ign http://archive.canonical.com precise InRelease
Get:6 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]                                  
Get:7 http://security.ubuntu.com precise-security Release.gpg [198 B]                                  
Get:8 http://archive.canonical.com precise Release.gpg [198 B]                            
Get:9 http://us.archive.ubuntu.com precise/main Sources [934 kB]
Get:10 http://security.ubuntu.com precise-security Release [49.6 kB]                                  
Get:11 http://archive.canonical.com precise Release [7,078 B]                           
Get:12 http://archive.canonical.com precise/partner i386 Packages [5,998 B]                        
Ign http://archive.canonical.com precise/partner TranslationIndex                                               
Get:13 http://security.ubuntu.com precise-security/main Sources [56.2 kB]
Get:14 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]                              
Get:15 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]                                     
Ign http://archive.canonical.com precise/partner Translation-en_US                                              
Ign http://archive.canonical.com precise/partner Translation-en                                                 
Get:16 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]               
Get:17 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]
Get:18 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]             
Get:19 http://security.ubuntu.com precise-security/universe Sources [17.7 kB] 
Get:20 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]                                  
Get:21 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]                                   
Get:22 http://security.ubuntu.com precise-security/multiverse Sources [1,392 B]                                 
Get:23 http://security.ubuntu.com precise-security/main i386 Packages [206 kB]                                  
Get:24 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                                   
Get:25 http://us.archive.ubuntu.com precise/main TranslationIndex [3,706 B]                                     
Get:26 http://us.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]                               
Get:27 http://us.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]                               
Get:28 http://us.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]                                 
Get:29 http://us.archive.ubuntu.com precise-updates/main Sources [193 kB]                                       
Get:30 http://us.archive.ubuntu.com precise-updates/restricted Sources [4,419 B]                                
Get:31 http://us.archive.ubuntu.com precise-updates/universe Sources [65.4 kB]                                  
Get:32 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]                                
Get:33 http://us.archive.ubuntu.com precise-updates/main i386 Packages [443 kB]                                 
Get:34 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]                          
Get:35 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [161 kB]                             
Get:36 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]                          
Get:37 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]                             
Get:38 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]                       
Get:39 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]                       
Get:40 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]                         
Get:41 http://us.archive.ubuntu.com precise-backports/main Sources [2,422 B]                                    
Get:42 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]                                 
Get:43 http://us.archive.ubuntu.com precise-backports/universe Sources [18.7 kB]                                
Get:44 http://us.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]                              
Get:45 http://us.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]                              
Get:46 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                           
Get:47 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [17.6 kB]                          
Get:48 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]                        
Get:49 http://us.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]                              
Get:50 http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]                        
Get:51 http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]                        
Get:52 http://us.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]                          
Get:53 http://us.archive.ubuntu.com precise/main Translation-en [726 kB]                                        
Get:54 http://us.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]                                 
Get:55 http://us.archive.ubuntu.com precise/restricted Translation-en [2,395 B]                                 
Get:56 http://us.archive.ubuntu.com precise/universe Translation-en [3,341 kB]                                  
Get:57 http://us.archive.ubuntu.com precise-updates/main Translation-en [214 kB]                                
Get:58 http://us.archive.ubuntu.com precise-updates/multiverse Translation-en [5,414 B]                         
Get:59 http://us.archive.ubuntu.com precise-updates/restricted Translation-en [2,082 B]                         
Get:60 http://us.archive.ubuntu.com precise-updates/universe Translation-en [95.6 kB]                           
Get:61 http://us.archive.ubuntu.com precise-backports/main Translation-en [1,244 B]                             
Get:62 http://us.archive.ubuntu.com precise-backports/multiverse Translation-en [1,476 B]                       
Get:63 http://us.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]                          
Get:64 http://us.archive.ubuntu.com precise-backports/universe Translation-en [12.3 kB]                         
Get:65 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]                           
Get:66 http://security.ubuntu.com precise-security/universe i386 Packages [58.6 kB]                             
Get:67 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,388 B]                           
Get:68 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:69 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:70 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Get:71 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:72 http://security.ubuntu.com precise-security/main Translation-en [98.6 kB]
Get:73 http://security.ubuntu.com precise-security/multiverse Translation-en [995 B]
Get:74 http://security.ubuntu.com precise-security/restricted Translation-en [978 B]
Get:75 http://security.ubuntu.com precise-security/universe Translation-en [35.2 kB]
Fetched 18.5 MB in 1min 13s (250 kB/s)                                                                          
Reading package lists... Done
guest@netbook:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-33-generic-pae; however:
  Package linux-image-3.2.0-33-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.33.36); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic-pae
 linux-generic-pae
guest@netbook:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-32 linux-headers-3.2.0-32-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.2.0-33-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-33-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 20 not upgraded.
2 not fully installed or removed.
Need to get 38.2 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.2.0-33-generic-pae i386 3.2.0-33.52 [38.2 MB]
Fetched 38.2 MB in 34s (1,113 kB/s)                                                                             
(Reading database ... 232289 files and directories currently installed.)
Unpacking linux-image-3.2.0-33-generic-pae (from .../linux-image-3.2.0-33-generic-pae_3.2.0-33.52_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-33-generic-pae_3.2.0-33.52_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./lib/modules/3.2.0-33-generic-pae/kernel/drivers/isdn/i4l/isdn.ko': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-33-generic-pae /boot/vmlinuz-3.2.0-33-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-33-generic-pae /boot/vmlinuz-3.2.0-33-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-33-generic-pae_3.2.0-33.52_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
guest@netbook:~$ 

```

---

### Post by zvacet on 2012-12-02
It look like your disc is full.>Try with 

```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
```

---

