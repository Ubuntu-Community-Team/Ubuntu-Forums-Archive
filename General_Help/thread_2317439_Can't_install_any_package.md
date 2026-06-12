---
title: "Can't install any package"
date: 2016-03-16
forum: General Help
---

### Post by Augusto_Csar_Sil on 2016-03-16
Hello!
So when i try to install any package I get the following error:

```

[B]vagrant@lucid32:~$ sudo apt-get install vim                                                   
[/B]Reading package lists... Done                                                                 
Building dependency tree                                                                      
Reading state information... Done                                                             
You might want to run `apt-get -f install' to correct these:                                  
The following packages have unmet dependencies:                                               
  bsdmainutils: Depends: cpp but it is not going to be installed                              
  cpp-4.4: Depends: libgmp10 but it is not going to be installed                              
  gcc-4.4: Depends: binutils (>= 2.20.1-15~) but 2.20.1-3ubuntu7.3 is to be installed         
           Depends: libgcc1 (>= 1:4.4.7-1ubuntu2) but 1:4.4.3-4ubuntu5.1 is to be installed   
           Depends: libgomp1 (>= 4.4.7-1ubuntu2) but 4.4.3-4ubuntu5.1 is to be installed      
           Recommends: libc6-dev (>= 2.13-0ubuntu6) but it is not going to be installed       
  libgcc1: Depends: gcc-4.4-base (= 4.4.3-4ubuntu5.1) but 4.4.7-1ubuntu2 is to be installed   
  libgomp1: Depends: gcc-4.4-base (= 4.4.3-4ubuntu5.1) but 4.4.7-1ubuntu2 is to be installed  
  libmpfr4: Depends: libgmp10 but it is not going to be installed                             
  libncurses5-dev: Depends: libc-dev                                                          
  libnih1: Depends: libc6 (< 2.12) but 2.19-0ubuntu6 is to be installed                       
  libstdc++6: Depends: gcc-4.4-base (= 4.4.3-4ubuntu5.1) but 4.4.7-1ubuntu2 is to be installed
  vim: Depends: vim-common (= 2:7.4.052-1ubuntu3) but 2:7.2.330-1ubuntu3.1 is to be installed 
       Depends: vim-runtime (= 2:7.4.052-1ubuntu3) but it is not going to be installed        
       Depends: libacl1 (>= 2.2.51-8) but 2.2.49-2 is to be installed                         
       Depends: libpython2.7 (>= 2.7) but it is not going to be installed                     
       Depends: libtinfo5 but it is not going to be installed                                 
  zlib1g-dev: Depends: libc6-dev but it is not going to be installed or                       
                       libc-dev                                                               
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).     

```

So I do the following:

```

vagrant@lucid32:~$ sudo apt-get -f install                                                                                                                                                        
Reading package lists... Done                                                                                                                                                                     
Building dependency tree                                                                                                                                                                          
Reading state information... Done                                                                                                                                                                 
Correcting dependencies... Done                                                                                                                                                                   
The following packages were automatically installed and are no longer required:                                                                                                                   
  php5-gd wwwconfig-common libmcrypt4 libjs-mootools libt1-5 libxpm4 libgd2-xpm php5-mcrypt javascript-common dbconfig-common                                                                     
Use 'apt-get autoremove' to remove them.                                                                                                                                                          
The following extra packages will be installed:                                                                                                                                                   
  binutils bsdmainutils gcc-4.8-base gcc-4.9-base libc-dev-bin libc6-dev libgcc1 libgmp10 libgomp1 liblzma5 libncurses5 libncurses5-dev libnih-dbus1 libnih1 libstdc++6 libtinfo-dev libtinfo5    
  libxml2 ncurses-bin zlib1g zlib1g-dev                                                                                                                                                           
Suggested packages:                                                                                                                                                                               
  binutils-doc cpp wamerican wordlist whois vacation glibc-doc ncurses-doc                                                                                                                        
The following NEW packages will be installed:                                                                                                                                                     
  gcc-4.8-base gcc-4.9-base libc-dev-bin libc6-dev libgmp10 liblzma5 libtinfo-dev libtinfo5                                                                                                       
The following packages will be upgraded:                                                                                                                                                          
  binutils bsdmainutils libgcc1 libgomp1 libncurses5 libncurses5-dev libnih-dbus1 libnih1 libstdc++6 libxml2 ncurses-bin zlib1g zlib1g-dev                                                        
13 upgraded, 8 newly installed, 0 to remove and 363 not upgraded.                                                                                                                                 
3 not fully installed or removed.                                                                                                                                                                 
Need to get 1,611kB/5,995kB of archives.                                                                                                                                                          
After this operation, 6,671kB of additional disk space will be used.                                                                                                                              
Do you want to continue [Y/n]? y                                                                                                                                                                  
Get:1 http://55.archive.ubuntu.com/ubuntu/ trusty/main liblzma5 5.1.1alpha+20120614-2ubuntu2 [84.2kB]                                                                                             
Get:2 http://55.archive.ubuntu.com/ubuntu/ trusty/main libxml2 2.9.1+dfsg1-3ubuntu4 [555kB]                                                                                                       
Get:3 http://55.archive.ubuntu.com/ubuntu/ trusty/main zlib1g-dev 1:1.2.8.dfsg-1ubuntu1 [181kB]                                                                                                   
Get:4 http://55.archive.ubuntu.com/ubuntu/ trusty/main zlib1g 1:1.2.8.dfsg-1ubuntu1 [57.5kB]                                                                                                      
Get:5 http://55.archive.ubuntu.com/ubuntu/ trusty/main libtinfo5 5.9+20140118-1ubuntu1 [70.8kB]                                                                                                   
Get:6 http://55.archive.ubuntu.com/ubuntu/ trusty/main ncurses-bin 5.9+20140118-1ubuntu1 [135kB]                                                                                                  
Get:7 http://55.archive.ubuntu.com/ubuntu/ trusty/main libtinfo-dev 5.9+20140118-1ubuntu1 [71.2kB]                                                                                                
Get:8 http://55.archive.ubuntu.com/ubuntu/ trusty/main libncurses5-dev 5.9+20140118-1ubuntu1 [166kB]                                                                                              
Get:9 http://55.archive.ubuntu.com/ubuntu/ trusty/main libncurses5 5.9+20140118-1ubuntu1 [93.8kB]                                                                                                 
Get:10 http://55.archive.ubuntu.com/ubuntu/ trusty/main bsdmainutils 9.0.5ubuntu1 [197kB]                                                                                                         
Fetched 1,611kB in 1s (1,270kB/s)                                                                                                                                                                 
(Reading database ...                                                                                                                                                                             
dpkg: warning: files list file for package `libio-string-perl' missing, assuming package has no files currently installed.                                                                        
                                                                                                                                                                                                  
dpkg: warning: files list file for package `wwwconfig-common' missing, assuming package has no files currently installed.                                                                         
                                                                                                                                                                                                  
/* HERE GOES HOUNDREDS OF ERRORS LIKE THESE */                                                                              
                                                                                                                                                                                                  
dpkg: warning: files list file for package `debconf' missing, assuming package has no files currently installed.                                                                                  
                                                                                                                                                                                                  
dpkg: warning: files list file for package `libtext-wrapi18n-perl' missing, assuming package has no files currently installed.                                                                    
                                                                                                                                                                                                  
dpkg: warning: files list file for package `mysql-client-core-5.1' missing, assuming package has no files currently installed.                                                                    
                                                                                                                                                                                                  
dpkg: warning: files list file for package `libxml-libxml-perl' missing, assuming package has no files currently installed.                                                                       
(Reading database ... 43 files and directories currently installed.)                                                                                                                              
Unpacking libgmp10 (from .../libgmp10_2%3a5.1.3+dfsg-1ubuntu1_i386.deb) ...                                                                                                                       
dpkg-deb: file `/var/cache/apt/archives/libgmp10_2%3a5.1.3+dfsg-1ubuntu1_i386.deb' contains ununderstood data member data.tar.xz     , giving up                                                  
dpkg: error processing /var/cache/apt/archives/libgmp10_2%3a5.1.3+dfsg-1ubuntu1_i386.deb (--unpack):                                                                                              
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2                                                                                                                                  
Unpacking liblzma5 (from .../liblzma5_5.1.1alpha+20120614-2ubuntu2_i386.deb) ...                                                                                                                  
dpkg-deb: file `/var/cache/apt/archives/liblzma5_5.1.1alpha+20120614-2ubuntu2_i386.deb' contains ununderstood data member data.tar.xz     , giving up                                             
dpkg: error processing /var/cache/apt/archives/liblzma5_5.1.1alpha+20120614-2ubuntu2_i386.deb (--unpack):                                                                                         
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2                                                                                                                                  
Preparing to replace libxml2 2.7.6.dfsg-1ubuntu1.15 (using .../libxml2_2.9.1+dfsg1-3ubuntu4_i386.deb) ...                                                                                         
Unpacking replacement libxml2 ...                                                                                                                                                                 
dpkg-deb: file `/var/cache/apt/archives/libxml2_2.9.1+dfsg1-3ubuntu4_i386.deb' contains ununderstood data member data.tar.xz     , giving up                                                      
dpkg: error processing /var/cache/apt/archives/libxml2_2.9.1+dfsg1-3ubuntu4_i386.deb (--unpack):                                                                                                  
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2                                                                                                                                  
Selecting previously deselected package libc-dev-bin.                                                                                                                                             
Unpacking libc-dev-bin (from .../libc-dev-bin_2.19-0ubuntu6_i386.deb) ...                                                                                                                         
dpkg-deb: file `/var/cache/apt/archives/libc-dev-bin_2.19-0ubuntu6_i386.deb' contains ununderstood data member data.tar.xz     , giving up                                                        
dpkg: error processing /var/cache/apt/archives/libc-dev-bin_2.19-0ubuntu6_i386.deb (--unpack):                                                                                                    
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2                                                                                                                                  
No apport report written because MaxReports is reached already                                                                                                                                    
Selecting previously deselected package libc6-dev.                                                                                                                                                
Unpacking libc6-dev (from .../libc6-dev_2.19-0ubuntu6_i386.deb) ...                                                                                                                               
dpkg-deb: file `/var/cache/apt/archives/libc6-dev_2.19-0ubuntu6_i386.deb' contains ununderstood data member data.tar.xz     , giving up                                                           
dpkg: error processing /var/cache/apt/archives/libc6-dev_2.19-0ubuntu6_i386.deb (--unpack):                                                                                                       
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2                                                                                                                                  
No apport report written because MaxReports is reached already                                                                                                                                    
Preparing to replace zlib1g-dev 1:1.2.3.3.dfsg-15ubuntu1 (using .../zlib1g-dev_1%3a1.2.8.dfsg-1ubuntu1_i386.deb) ...                                                                              
Unpacking replacement zlib1g-dev ...                                                                                                                                                              
dpkg: considering deconfiguration of libxml2, which would be broken by installation of zlib1g ...                                                                                                 
dpkg: yes, will deconfigure libxml2 (broken by zlib1g).                                                                                                                                           
Preparing to replace zlib1g 1:1.2.3.3.dfsg-15ubuntu1 (using .../zlib1g_1%3a1.2.8.dfsg-1ubuntu1_i386.deb) ...                                                                                      
De-configuring libxml2 ...                                                                                                                                                                        
Unpacking replacement zlib1g ...                                                                                                                                                                  
Processing triggers for man-db ...                                                                                                                                                                
Errors were encountered while processing:                                                                                                                                                         
 /var/cache/apt/archives/libgmp10_2%3a5.1.3+dfsg-1ubuntu1_i386.deb                                                                                                                                
 /var/cache/apt/archives/liblzma5_5.1.1alpha+20120614-2ubuntu2_i386.deb                                                                                                                           
 /var/cache/apt/archives/libxml2_2.9.1+dfsg1-3ubuntu4_i386.deb                                                                                                                                    
 /var/cache/apt/archives/libc-dev-bin_2.19-0ubuntu6_i386.deb                                                                                                                                      
 /var/cache/apt/archives/libc6-dev_2.19-0ubuntu6_i386.deb                                                                                                                                         
E: Sub-process /usr/bin/dpkg returned an error code (1)                                                                                                                                           

```


What should I do?

---

### Post by ian-weisser on 2016-03-16
> **Augusto_Csar_Sil said:**
> vim: Depends: vim-common (= **2:7.4**.052-1ubuntu3) but **2:7.2**.330-1ubuntu3.1 is to be installed 

You seem to be trying to install much older software onto a Trusty (14.04) system. Unwise.
This often indicates a poor choice of software sources. Do not use non-Trusty sources. Remove all non-14.04 sources that you have added.

Your hundreds of lines of dpkg warnings occur most frequently to users who have manually tampered with the package database. Don't do that. It causes more problems than it solves.
One safe solution is to reinstall each of those packages, so the package database reflects reality again.
Another solution is to backup your data and reinstall Ubuntu.

---

