---
title: "Can't finish the sudo apt-get update."
date: 2015-05-09
forum: General Help
---

### Post by Ezekiel_V._dela_Pe on 2015-05-09
[COLOR=#111111][FONT=Ubuntu]I have a problem with [/FONT][/COLOR]sudo apt-get update[COLOR=#111111][FONT=Ubuntu] that I can't seem to fix[/FONT][/COLOR]

```
ezekielvdp@ezekielvdp:~$ sudo apt-get updateIgn http://ppa.launchpad.net trusty InRelease
Ign http://dl.google.com stable InRelease                                      
Ign http://ph.archive.ubuntu.com trusty InRelease                              
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:2 http://dl.google.com stable Release [1,347 B]                            
Ign http://ph.archive.ubuntu.com trusty-updates InRelease                      
Get:3 http://dl.google.com stable/main amd64 Packages [1,181 B]                
Get:4 http://ppa.launchpad.net trusty Release.gpg [316 B]                      
Get:5 http://dl.google.com stable/main i386 Packages [1,186 B]                 
Ign http://ph.archive.ubuntu.com trusty-backports InRelease                    
Get:6 http://ppa.launchpad.net trusty Release.gpg [316 B]                      
Get:7 http://ph.archive.ubuntu.com trusty Release.gpg [933 B]                  
Get:8 http://ppa.launchpad.net trusty Release [15.1 kB]                        
Get:9 http://ph.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Get:10 http://ph.archive.ubuntu.com trusty-backports Release.gpg [933 B]       
Get:11 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:12 http://ph.archive.ubuntu.com trusty Release [58.5 kB]                   
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://security.ubuntu.com trusty-security InRelease                       
Get:13 http://ph.archive.ubuntu.com trusty-updates Release [63.5 kB]           
Get:14 http://ppa.launchpad.net trusty/main amd64 Packages [6,204 B]           
Get:15 http://security.ubuntu.com trusty-security Release.gpg [933 B]          
Get:16 http://security.ubuntu.com trusty-security Release [63.5 kB]            
Get:17 http://ph.archive.ubuntu.com trusty-backports Release [63.5 kB]         
Get:18 http://ppa.launchpad.net trusty/main i386 Packages [6,250 B]            
Get:19 http://security.ubuntu.com trusty-security/main Sources [80.3 kB]       
Get:20 http://ppa.launchpad.net trusty/main Translation-en [3,365 B]           
Get:21 http://ph.archive.ubuntu.com trusty/main Sources [1,064 kB]             
Ign http://dl.google.com stable/main Translation-en_PH                         
Get:22 http://ppa.launchpad.net trusty/main amd64 Packages [7,624 B]           
Get:23 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B] 
Ign http://dl.google.com stable/main Translation-en                            
Get:24 http://security.ubuntu.com trusty-security/universe Sources [21.9 kB]   
Get:25 http://repository.spotify.com stable InRelease [2,983 B]                
Get:26 http://ppa.launchpad.net trusty/main i386 Packages [7,626 B]            
Get:27 http://security.ubuntu.com trusty-security/multiverse Sources [2,334 B] 
Get:28 http://repository.spotify.com stable/non-free amd64 Packages [1,431 B]  
Get:29 http://repository.spotify.com stable/non-free i386 Packages [20 B]      
Get:30 http://security.ubuntu.com trusty-security/main amd64 Packages [267 kB] 
Get:31 http://extras.ubuntu.com trusty Release.gpg [72 B]                      
Get:32 http://ppa.launchpad.net trusty/main Translation-en [7,388 B]           
Get:33 http://extras.ubuntu.com trusty Release [11.9 kB]                       
Get:34 http://extras.ubuntu.com trusty/main Sources [14 B]                     
Get:35 http://extras.ubuntu.com trusty/main amd64 Packages [14 B]              
Get:36 http://extras.ubuntu.com trusty/main i386 Packages [14 B]               
Get:37 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Get:38 http://security.ubuntu.com trusty-security/universe amd64 Packages [101 kB]
Ign http://repository.spotify.com stable/non-free Translation-en_PH            
Ign http://repository.spotify.com stable/non-free Translation-en               
Get:39 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,681 B]
Get:40 http://security.ubuntu.com trusty-security/main i386 Packages [256 kB]  
Get:41 http://ph.archive.ubuntu.com trusty/restricted Sources [5,433 B]        
Get:42 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Get:43 http://ph.archive.ubuntu.com trusty/universe Sources [6,399 kB]         
Get:44 http://security.ubuntu.com trusty-security/universe i386 Packages [101 kB]
Get:45 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,846 B]
Get:46 http://security.ubuntu.com trusty-security/main Translation-en [136 kB] 
Ign http://extras.ubuntu.com trusty/main Translation-en_PH                     
Get:47 http://security.ubuntu.com trusty-security/multiverse Translation-en [1,679 B]
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:48 http://security.ubuntu.com trusty-security/restricted Translation-en [2,266 B]
Get:49 http://security.ubuntu.com trusty-security/universe Translation-en [56.8 kB]
Get:50 http://ph.archive.ubuntu.com trusty/multiverse Sources [174 kB]         
Get:51 http://ph.archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]      
Get:52 http://ph.archive.ubuntu.com trusty/restricted amd64 Packages [13.0 kB] 
Get:53 http://ph.archive.ubuntu.com trusty/universe amd64 Packages [5,859 kB]  
Get:54 http://ph.archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]  
Get:55 http://ph.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]       
Get:56 http://ph.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]  
Get:57 http://ph.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]   
Get:58 http://ph.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]   
Get:59 http://ph.archive.ubuntu.com trusty/main Translation-en [762 kB]        
Get:60 http://ph.archive.ubuntu.com trusty/multiverse Translation-en [102 kB]  
Get:61 http://ph.archive.ubuntu.com trusty/restricted Translation-en [3,457 B] 
Get:62 http://ph.archive.ubuntu.com trusty/universe Translation-en [4,089 kB]  
Get:63 http://ph.archive.ubuntu.com trusty-updates/main Sources [198 kB]       
Get:64 http://ph.archive.ubuntu.com trusty-updates/restricted Sources [2,564 B]
Get:65 http://ph.archive.ubuntu.com trusty-updates/universe Sources [114 kB]   
Get:66 http://ph.archive.ubuntu.com trusty-updates/multiverse Sources [5,144 B]
Get:67 http://ph.archive.ubuntu.com trusty-updates/main amd64 Packages [514 kB]
Get:68 http://ph.archive.ubuntu.com trusty-updates/restricted amd64 Packages [9,238 B]
Get:69 http://ph.archive.ubuntu.com trusty-updates/universe amd64 Packages [276 kB]
Get:70 http://ph.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:71 http://ph.archive.ubuntu.com trusty-updates/main i386 Packages [502 kB] 
Get:72 http://ph.archive.ubuntu.com trusty-updates/restricted i386 Packages [9,256 B]
Get:73 http://ph.archive.ubuntu.com trusty-updates/universe i386 Packages [277 kB]
Get:74 http://ph.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Get:75 http://ph.archive.ubuntu.com trusty-updates/main Translation-en [244 kB]
Get:76 http://ph.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,148 B]
Get:77 http://ph.archive.ubuntu.com trusty-updates/restricted Translation-en [2,433 B]
Get:78 http://ph.archive.ubuntu.com trusty-updates/universe Translation-en [143 kB]
Get:79 http://ph.archive.ubuntu.com trusty-backports/main Sources [5,851 B]    
Get:80 http://ph.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:81 http://ph.archive.ubuntu.com trusty-backports/universe Sources [24.8 kB]
Get:82 http://ph.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:83 http://ph.archive.ubuntu.com trusty-backports/main amd64 Packages [6,256 B]
Get:84 http://ph.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:85 http://ph.archive.ubuntu.com trusty-backports/universe amd64 Packages [28.5 kB]
Get:86 http://ph.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,245 B]
Get:87 http://ph.archive.ubuntu.com trusty-backports/main i386 Packages [6,285 B]
Get:88 http://ph.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:89 http://ph.archive.ubuntu.com trusty-backports/universe i386 Packages [28.5 kB]
Get:90 http://ph.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,249 B]
Get:91 http://ph.archive.ubuntu.com trusty-backports/main Translation-en [3,645 B]
Get:92 http://ph.archive.ubuntu.com trusty-backports/multiverse Translation-en [776 B]
Get:93 http://ph.archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]
Get:94 http://ph.archive.ubuntu.com trusty-backports/universe Translation-en [25.3 kB]
Ign http://ph.archive.ubuntu.com trusty/main Translation-en_PH                 
Ign http://ph.archive.ubuntu.com trusty/multiverse Translation-en_PH
Ign http://ph.archive.ubuntu.com trusty/restricted Translation-en_PH
Ign http://ph.archive.ubuntu.com trusty/universe Translation-en_PH
Fetched 31.2 MB in 3min 46s (138 kB/s)
W: Failed to fetch http://repository.spotify.com/dists/stable/non-free/binary-i386/Packages  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ezekielvdp@ezekielvdp:~$ sudo apt-get clean
ezekielvdp@ezekielvdp:~$ cd /var/lib/apt
ezekielvdp@ezekielvdp:/var/lib/apt$ mv list lists.old
mv: cannot stat ‘list’: No such file or directory
ezekielvdp@ezekielvdp:/var/lib/apt$ mv lists lists.old
mv: cannot move ‘lists’ to ‘lists.old’: Permission denied
ezekielvdp@ezekielvdp:/var/lib/apt$ cd ../..
ezekielvdp@ezekielvdp:/var$ cd ..
ezekielvdp@ezekielvdp:/$ ^C
ezekielvdp@ezekielvdp:/$ ^C
ezekielvdp@ezekielvdp:/$ ^C
ezekielvdp@ezekielvdp:/$ ^C
ezekielvdp@ezekielvdp:/$ ^C
ezekielvdp@ezekielvdp:/$ ^C
ezekielvdp@ezekielvdp:/$ sudo apt-get install ruby2.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libupstart1 linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
  linux-signed-image-3.16.0-30-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libjs-jquery libruby2.2 rubygems-integration
Suggested packages:
  javascript-common bundler
The following NEW packages will be installed:
  libjs-jquery libruby2.2 ruby2.2 rubygems-integration
0 upgraded, 4 newly installed, 0 to remove and 31 not upgraded.
Need to get 3,549 kB of archives.
After this operation, 15.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/brightbox/ruby-ng/ubuntu/ trusty/main rubygems-integration all 1.8-1bbox1~trusty1 [4,364 B]
Get:2 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libjs-jquery all 1.7.2+dfsg-2ubuntu1 [78.8 kB]
Get:3 http://ppa.launchpad.net/brightbox/ruby-ng/ubuntu/ trusty/main libruby2.2 amd64 2.2.2-1bbox1~trusty1 [3,386 kB]
Get:4 http://ppa.launchpad.net/brightbox/ruby-ng/ubuntu/ trusty/main ruby2.2 amd64 2.2.2-1bbox1~trusty1 [80.5 kB]
Fetched 3,549 kB in 1min 9s (51.3 kB/s)                                        
Selecting previously unselected package libjs-jquery.
(Reading database ... 238050 files and directories currently installed.)
Preparing to unpack .../libjs-jquery_1.7.2+dfsg-2ubuntu1_all.deb ...
Unpacking libjs-jquery (1.7.2+dfsg-2ubuntu1) ...
Selecting previously unselected package rubygems-integration.
Preparing to unpack .../rubygems-integration_1.8-1bbox1~trusty1_all.deb ...
Unpacking rubygems-integration (1.8-1bbox1~trusty1) ...
Selecting previously unselected package libruby2.2:amd64.
Preparing to unpack .../libruby2.2_2.2.2-1bbox1~trusty1_amd64.deb ...
Unpacking libruby2.2:amd64 (2.2.2-1bbox1~trusty1) ...
Selecting previously unselected package ruby2.2.
Preparing to unpack .../ruby2.2_2.2.2-1bbox1~trusty1_amd64.deb ...
Unpacking ruby2.2 (2.2.2-1bbox1~trusty1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libjs-jquery (1.7.2+dfsg-2ubuntu1) ...
Setting up rubygems-integration (1.8-1bbox1~trusty1) ...
Setting up libruby2.2:amd64 (2.2.2-1bbox1~trusty1) ...
Setting up ruby2.2 (2.2.2-1bbox1~trusty1) ...
update-alternatives: using /usr/bin/gem2.2 to provide /usr/bin/gem (gem) in auto mode
update-alternatives: using /usr/bin/ruby2.2 to provide /usr/bin/ruby (ruby) in auto mode
update-alternatives: warning: skip creation of /usr/bin/testrb because associated file /usr/bin/testrb2.2 (of link group ruby) doesn't exist
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
ezekielvdp@ezekielvdp:/$ ruby2.2 -v
ruby 2.2.2p95 (2015-04-13 revision 50295) [x86_64-linux-gnu]
ezekielvdp@ezekielvdp:/$ clear


ezekielvdp@ezekielvdp:/$ sudo apt-get install ruby2.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libupstart1 linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
  linux-signed-image-3.16.0-30-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgmp-dev libgmpxx4ldbl
Suggested packages:
  libgmp10-doc libmpfr-dev
The following NEW packages will be installed:
  libgmp-dev libgmpxx4ldbl ruby2.2-dev
0 upgraded, 3 newly installed, 0 to remove and 31 not upgraded.
Need to get 1,300 kB of archives.
After this operation, 6,404 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err http://ph.archive.ubuntu.com/ubuntu/ trusty/main libgmpxx4ldbl amd64 2:5.1.3+dfsg-1ubuntu1
  Cannot initiate the connection to ph.archive.ubuntu.com:80 (2001:d18:1:1::94). - connect (101: Network is unreachable)
Err http://ph.archive.ubuntu.com/ubuntu/ trusty/main libgmp-dev amd64 2:5.1.3+dfsg-1ubuntu1
  Cannot initiate the connection to ph.archive.ubuntu.com:80 (2001:d18:1:1::94). - connect (101: Network is unreachable)
Get:1 http://ppa.launchpad.net/brightbox/ruby-ng/ubuntu/ trusty/main ruby2.2-dev amd64 2.2.2-1bbox1~trusty1 [1,000 kB]
Fetched 1,000 kB in 18s (55.1 kB/s)                                            
E: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmpxx4ldbl_5.1.3+dfsg-1ubuntu1_amd64.deb  Cannot initiate the connection to ph.archive.ubuntu.com:80 (2001:d18:1:1::94). - connect (101: Network is unreachable)


E: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp-dev_5.1.3+dfsg-1ubuntu1_amd64.deb  Cannot initiate the connection to ph.archive.ubuntu.com:80 (2001:d18:1:1::94). - connect (101: Network is unreachable)


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ezekielvdp@ezekielvdp:/$ sudo apt-get update
Ign http://extras.ubuntu.com trusty InRelease
Ign http://dl.google.com stable InRelease                                      
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://security.ubuntu.com trusty-security InRelease                       
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Hit http://dl.google.com stable Release                                        
Get:2 http://repository.spotify.com stable InRelease [2,954 B]                 
Get:3 http://repository.spotify.com stable/non-free amd64 Packages [1,431 B]   
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://security.ubuntu.com trusty-security Release                         
Get:4 http://repository.spotify.com stable/non-free i386 Packages [20 B]       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable/main i386 Packages                             
Get:5 http://security.ubuntu.com trusty-security/main Sources [80.3 kB]        
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Get:6 http://ppa.launchpad.net trusty Release.gpg [316 B]                      
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:7 http://ppa.launchpad.net trusty Release.gpg [316 B]                      
Get:8 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]  
Get:9 http://ppa.launchpad.net trusty Release [15.1 kB]                        
Get:10 http://security.ubuntu.com trusty-security/universe Sources [21.9 kB]   
Ign http://ph.archive.ubuntu.com trusty InRelease                              
Ign http://repository.spotify.com stable/non-free Translation-en_PH            
Get:11 http://security.ubuntu.com trusty-security/multiverse Sources [2,334 B] 
Ign http://repository.spotify.com stable/non-free Translation-en               
Get:12 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Ign http://ph.archive.ubuntu.com trusty-updates InRelease                      
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Ign http://ph.archive.ubuntu.com trusty-backports InRelease                    
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Get:13 http://ppa.launchpad.net trusty/main amd64 Packages [6,204 B]           
Get:14 http://ppa.launchpad.net trusty/main i386 Packages [6,250 B]            
Hit http://ph.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Get:15 http://ppa.launchpad.net trusty/main Translation-en [3,365 B]           
Hit http://ph.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Get:16 http://ppa.launchpad.net trusty/main amd64 Packages [7,624 B]           
Hit http://ph.archive.ubuntu.com trusty-backports Release.gpg                  
Get:17 http://ppa.launchpad.net trusty/main i386 Packages [7,626 B]            
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Get:18 http://ppa.launchpad.net trusty/main Translation-en [7,388 B]           
Hit http://ph.archive.ubuntu.com trusty Release                                
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://ph.archive.ubuntu.com trusty-updates Release                        
Ign http://dl.google.com stable/main Translation-en_PH                         
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://ph.archive.ubuntu.com trusty-backports Release                      
Ign http://dl.google.com stable/main Translation-en                            
Ign http://extras.ubuntu.com trusty/main Translation-en_PH                     
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://ph.archive.ubuntu.com trusty/main Sources                           
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://ph.archive.ubuntu.com trusty/restricted Sources                     
Get:19 http://security.ubuntu.com trusty-security/multiverse Translation-en [1,679 B]
Get:20 http://security.ubuntu.com trusty-security/restricted Translation-en [2,266 B]
Hit http://ph.archive.ubuntu.com trusty/universe Sources                       
Get:21 http://security.ubuntu.com trusty-security/universe Translation-en [56.8 kB]
Hit http://ph.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://ph.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://ph.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://ph.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://ph.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://ph.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://ph.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://ph.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://ph.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://ph.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ph.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://ph.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ph.archive.ubuntu.com trusty/universe Translation-en                
Hit http://ph.archive.ubuntu.com trusty-updates/main Sources                   
Get:22 http://ph.archive.ubuntu.com trusty-updates/restricted Sources [2,564 B]
Hit http://ph.archive.ubuntu.com trusty-updates/universe Sources               
Get:23 http://ph.archive.ubuntu.com trusty-updates/multiverse Sources [5,144 B]
Hit http://ph.archive.ubuntu.com trusty-updates/main amd64 Packages            
Get:24 http://ph.archive.ubuntu.com trusty-updates/restricted amd64 Packages [9,238 B]
Hit http://ph.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://ph.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://ph.archive.ubuntu.com trusty-updates/main i386 Packages             
Get:25 http://ph.archive.ubuntu.com trusty-updates/restricted i386 Packages [9,256 B]
Hit http://ph.archive.ubuntu.com trusty-updates/universe i386 Packages         
Get:26 http://ph.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://ph.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://ph.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://ph.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://ph.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://ph.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://ph.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://ph.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://ph.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://ph.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://ph.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://ph.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://ph.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://ph.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://ph.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://ph.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://ph.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://ph.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://ph.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://ph.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://ph.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://ph.archive.ubuntu.com trusty/main Translation-en_PH                 
Ign http://ph.archive.ubuntu.com trusty/multiverse Translation-en_PH
Ign http://ph.archive.ubuntu.com trusty/restricted Translation-en_PH
Ign http://ph.archive.ubuntu.com trusty/universe Translation-en_PH
Fetched 279 kB in 57s (4,847 B/s)
W: Failed to fetch http://repository.spotify.com/dists/stable/non-free/binary-amd64/Packages  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.
ezekielvdp@ezekielvdp:/$ sudo apt-get update
0% [Working]
Ign http://dl.google.com stable InRelease
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable Release.gpg                                    
Get:1 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Hit http://dl.google.com stable Release                                        
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://repository.spotify.com stable InRelease                             
Ign http://archive.ubuntu.com trusty-backports InRelease                       
Get:2 http://repository.spotify.com stable/non-free amd64 Packages [1,431 B]   
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://repository.spotify.com stable/non-free i386 Packages                
Get:3 http://ppa.launchpad.net trusty Release.gpg [316 B]                      
Ign http://archive.ubuntu.com trusty-security InRelease                        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Get:4 http://ppa.launchpad.net trusty Release.gpg [316 B]                      
Get:5 http://archive.ubuntu.com trusty Release.gpg [933 B]                     
Get:6 http://ppa.launchpad.net trusty Release [15.1 kB]                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:7 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Get:8 http://archive.ubuntu.com trusty-backports Release.gpg [933 B]           
Get:9 http://ppa.launchpad.net trusty Release [15.1 kB]                        
Get:10 http://archive.ubuntu.com trusty-security Release.gpg [933 B]           
Get:11 http://archive.ubuntu.com trusty Release [58.5 kB]                      
Ign http://repository.spotify.com stable/non-free Translation-en_PH            
Get:12 http://ppa.launchpad.net trusty/main amd64 Packages [6,204 B]           
Ign http://repository.spotify.com stable/non-free Translation-en               
Get:13 http://archive.ubuntu.com trusty-updates Release [63.5 kB]              
Get:14 http://ppa.launchpad.net trusty/main i386 Packages [6,250 B]            
Get:15 http://archive.ubuntu.com trusty-backports Release [63.5 kB]            
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:16 http://archive.ubuntu.com trusty-security Release [63.5 kB]             
Get:17 http://ppa.launchpad.net trusty/main amd64 Packages [7,624 B]           
Get:18 http://ppa.launchpad.net trusty/main i386 Packages [7,626 B]            
Get:19 http://archive.ubuntu.com trusty/main Sources [1,064 kB]                
Ign http://dl.google.com stable/main Translation-en_PH                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://extras.ubuntu.com trusty/main Translation-en_PH                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:20 http://archive.ubuntu.com trusty/restricted Sources [5,433 B]           
Get:21 http://archive.ubuntu.com trusty/universe Sources [6,399 kB]            
Get:22 http://archive.ubuntu.com trusty/multiverse Sources [174 kB]            
Get:23 http://archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]         
Get:24 http://archive.ubuntu.com trusty/restricted amd64 Packages [13.0 kB]    
Get:25 http://archive.ubuntu.com trusty/universe amd64 Packages [5,859 kB]     
Get:26 http://archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]     
Get:27 http://archive.ubuntu.com trusty/main i386 Packages [1,348 kB]          
Get:28 http://archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]     
Get:29 http://archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]      
Get:30 http://archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]      
Get:31 http://archive.ubuntu.com trusty/main Translation-en [762 kB]           
Get:32 http://archive.ubuntu.com trusty/multiverse Translation-en [102 kB]     
Get:33 http://archive.ubuntu.com trusty/restricted Translation-en [3,457 B]    
Get:34 http://archive.ubuntu.com trusty/universe Translation-en [4,089 kB]     
Get:35 http://archive.ubuntu.com trusty-updates/main Sources [198 kB]          
Get:36 http://archive.ubuntu.com trusty-updates/restricted Sources [2,564 B]   
Get:37 http://archive.ubuntu.com trusty-updates/universe Sources [114 kB]      
Get:38 http://archive.ubuntu.com trusty-updates/multiverse Sources [5,144 B]   
Get:39 http://archive.ubuntu.com trusty-updates/main amd64 Packages [513 kB]   
Get:40 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [9,238 B]
Get:41 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [276 kB]
Get:42 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:43 http://archive.ubuntu.com trusty-updates/main i386 Packages [502 kB]    
Get:44 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [9,256 B]
Get:45 http://archive.ubuntu.com trusty-updates/universe i386 Packages [277 kB]
Get:46 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Get:47 http://archive.ubuntu.com trusty-updates/main Translation-en [244 kB]   
Get:48 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [6,148 B]
Get:49 http://archive.ubuntu.com trusty-updates/restricted Translation-en [2,433 B]
Get:50 http://archive.ubuntu.com trusty-updates/universe Translation-en [143 kB]
Get:51 http://archive.ubuntu.com trusty-backports/main Sources [5,851 B]       
Get:52 http://archive.ubuntu.com trusty-backports/restricted Sources [28 B]    
Get:53 http://archive.ubuntu.com trusty-backports/universe Sources [24.8 kB]   
Get:54 http://archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B] 
Get:55 http://archive.ubuntu.com trusty-backports/main amd64 Packages [6,256 B]
Get:56 http://archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:57 http://archive.ubuntu.com trusty-backports/universe amd64 Packages [28.5 kB]
Get:58 http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,245 B]
Get:59 http://archive.ubuntu.com trusty-backports/main i386 Packages [6,285 B] 
Get:60 http://archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:61 http://archive.ubuntu.com trusty-backports/universe i386 Packages [28.5 kB]
Get:62 http://archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,249 B]
Get:63 http://archive.ubuntu.com trusty-backports/main Translation-en [3,645 B]
Get:64 http://archive.ubuntu.com trusty-backports/multiverse Translation-en [776 B]
Get:65 http://archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]
Get:66 http://archive.ubuntu.com trusty-backports/universe Translation-en [25.3 kB]
Get:67 http://archive.ubuntu.com trusty-security/main Sources [80.3 kB]        
Get:68 http://archive.ubuntu.com trusty-security/restricted Sources [2,061 B]  
Get:69 http://archive.ubuntu.com trusty-security/universe Sources [21.9 kB]    
Get:70 http://archive.ubuntu.com trusty-security/multiverse Sources [2,334 B]  
Get:71 http://archive.ubuntu.com trusty-security/main amd64 Packages [267 kB]  
Get:72 http://archive.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Get:73 http://archive.ubuntu.com trusty-security/universe amd64 Packages [101 kB]
Get:74 http://archive.ubuntu.com trusty-security/multiverse amd64 Packages [3,681 B]
Get:75 http://archive.ubuntu.com trusty-security/main i386 Packages [256 kB]   
Get:76 http://archive.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Get:77 http://archive.ubuntu.com trusty-security/universe i386 Packages [101 kB]
Get:78 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [3,846 B]
Get:79 http://archive.ubuntu.com trusty-security/main Translation-en [136 kB]  
Get:80 http://archive.ubuntu.com trusty-security/multiverse Translation-en [1,679 B]
Get:81 http://archive.ubuntu.com trusty-security/restricted Translation-en [2,266 B]
Get:82 http://archive.ubuntu.com trusty-security/universe Translation-en [56.8 kB]
Ign http://archive.ubuntu.com trusty/main Translation-en_PH                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_PH              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_PH              
Ign http://archive.ubuntu.com trusty/universe Translation-en_PH
Fetched 31.1 MB in 4min 6s (126 kB/s)
W: Failed to fetch http://repository.spotify.com/dists/stable/non-free/binary-amd64/Packages  Hash Sum mismatch



```

---

### Post by ele_ctric on 2015-05-09
I'm getting the same line as you do when giving the update command, that is
```
 W: Failed to fetch http://repository.spotify.com/dists/stable/non-free/binary-i386/Packages  Hash Sum mismatch

```

It just popped up right after adding the Spotify ppa (even if I just installed Spotify without any problem).
Hope it helps.

---

### Post by grahammechanical on 2015-05-09
You have combined the output from several commands into one very long quote. Please do not do that as it is now very difficult to work out what you were trying to do. And what worked and what did not work. 

As far as I can tell apt-get update is working as it should. Then you tried to install ruby2.2 and that worked. Next you tried to install ruby2.2-dev and that failed with the following errors:

> Err [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) trusty/main libgmpxx4ldbl amd64 2:5.1.3+dfsg-1ubuntu1
  Cannot initiate the connection to ph.archive.ubuntu.com:80 (2001:d18:1:1::94). - connect (101: Network is unreachable)
Err [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) trusty/main libgmp-dev amd64 2:5.1.3+dfsg-1ubuntu1
  Cannot initiate the connection to ph.archive.ubuntu.com:80 (2001:d18:1:1::94). - connect (101: Network is unreachable)
Get:1 [http://ppa.launchpad.net/brightbox/ruby-ng/ubuntu/](http://ppa.launchpad.net/brightbox/ruby-ng/ubuntu/) trusty/main ruby2.2-dev amd64 2.2.2-1bbox1~trusty1 [1,000 kB]
Fetched 1,000 kB in 18s (55.1 kB/s)                                            
E: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmpxx4ldbl_5.1.3+dfsg-1ubuntu1_amd64.deb](http://ph.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmpxx4ldbl_5.1.3+dfsg-1ubuntu1_amd64.deb)  Cannot initiate the connection to ph.archive.ubuntu.com:80 (2001:d18:1:1::94). - connect (101: Network is unreachable)

E: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp-dev_5.1.3+dfsg-1ubuntu1_amd64.deb](http://ph.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp-dev_5.1.3+dfsg-1ubuntu1_amd64.deb)  Cannot initiate the connection to ph.archive.ubuntu.com:80 (2001:d18:1:1::94). - connect (101: Network is unreachable)

You will receive errors from apt-get because because you have PPAs as software sources. Now, PPAs are very useful for installing software but it is sometimes best to disable the PPA after the software is installed as many developers do not use the PPA to update their software but only for installing it.

So, the question is, What is the problem? Is it with apt-get? Or with spotify? or with the failure to install ruby2.2-dev?

"101 network unreachable" could mean that the server is temporarily off-line or that the ISP is temporarily off-line. For all I know it could mean other things.

As for spotify, if you are no longer using that service then it might be best to remove spotify from your software sources.

Regards.

---

### Post by benjamin-suzm on 2015-09-19
Hi there,

I think I'm facing the same issue, does anyone know how to solve this? Didn't work when I tried run apt-get update or try with --fix-missing as suggested.

Do you want to continue? [Y/n] y
Err [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) trusty/main liberror-perl all 0.17-1.1
  404  Not Found
E: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/pool/main/libe/liberror-perl/liberror-perl_0.17-1.1_all.deb](http://sg.archive.ubuntu.com/ubuntu/pool/main/libe/liberror-perl/liberror-perl_0.17-1.1_all.deb)  404  Not Found


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by ian-weisser on 2015-09-19
> **benjamin-suzm said:**
> 404  Not Found

Huh? You know [what 404 means]("https://en.wikipedia.org/wiki/HTTP_404").
You solve it exactly the same way you solve any other 404 Not Found from a website:
You try opening it in a browser, You wait a few minutes. You try again. Etc.

---

