---
title: "dependency problems prevent configuration of python3-tk"
date: 2014-05-24
forum: General Help
---

### Post by david_a2 on 2014-05-24
I have started to encounter the following problem. Everytime the Update Manager highlights the following important security update: [B]pythonic binding for the libxml2 and libxslt libraries
python3-lxml[/B], I get the following error: **dpkg: dependency problems prevent configuration of python3-tk** when I try to install the update.

I also encountered the same problem when I ran **sudo apt-get install openjdk-6-jre openjdk-6-jdk icedtea6-plugin**. It also encountered errors while processing the following:

python3
python3-tk
idle-python3.2
idle3
python3-all
python3-dev
python3-all-dev
python3-roman
python3-docutils
python3-examples
python3-lxml
python3-pkg-resources
python3-pygments

What can I do to resolve this problem?

---

### Post by ian-weisser on 2014-05-26
Open a terminal and try the following:
```
sudo apt-get update
sudo apt-get upgrade
```

Please show us the *complete* output of both commands.

---

### Post by david_a2 on 2014-05-27
I have included the output from the 2 commands below, as requested. I also ended up getting 2 dialog boxes after running the 'sudo apt-get upgrade' command:

System program problem detected
Do you want to report the problem now?
[Cancel][Report problem...]

and

Crash report
Package: python3 3.2.3-0ubuntu1.2
Send an error report to help fix this problem
[Show details][Continue]

---------------------------------------

sudo apt-get update OUTPUT:
```

Ign cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204) precise/main TranslationIndex             
Ign cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204) precise/restricted TranslationIndex       
Ign cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204) precise/main Translation-en_GB            
Ign cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204) precise/main Translation-en               
Ign cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204) precise/restricted Translation-en_GB      
Ign cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204) precise/restricted Translation-en         
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg                                                                   
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B]                                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg                                                         
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release                                                                       
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release [49.6 kB]                                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                           
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                           
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                             
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]                                                    
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                     
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                  
Get:6 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg [489 B]                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                             
Get:7 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release [2,603 B]                                                               
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [105 kB]                                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release                                                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                                                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources                                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources                                                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources                                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources                                                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main amd64 Packages                                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted amd64 Packages                                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe amd64 Packages                                                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse amd64 Packages                                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages                                                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages                                                      
Get:9 [http://linux.dropbox.com](http://linux.dropbox.com) precise/main amd64 Packages [1,143 B]                                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages                                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages                                                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex                                                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex                                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex                                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex                                                     
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [459 kB]                                              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                                                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                          
Get:11 [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages [1,143 B]                                         
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]        
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.9 kB]                        
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,794 B]                                
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [395 kB]                      
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [8,056 B]                               
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [107 kB]                                      
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources [8,902 B]                                 
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main amd64 Packages [782 kB]                                  
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_GB                                                    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                                 
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]                                 
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [93.2 kB]                                   
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted amd64 Packages [13.7 kB]                                
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe amd64 Packages [241 kB]                                   
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,453 B]                                 
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [422 kB]                                         
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [15.3 kB]                                
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [815 kB]                                        
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]                                  
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [97.7 kB]                                    
Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.7 kB]                                 
Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages [247 kB]                                    
Get:32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages [15.5 kB]                                 
Get:33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]                                    
Get:34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]                              
Get:35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]                              
Get:36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources                                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources                                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main amd64 Packages                                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted amd64 Packages                                           
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,636 B]                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe amd64 Packages                                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse amd64 Packages                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages                                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages                                              
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages                                            
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]                                  
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex                                               
Get:41 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB                                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en                                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en                                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en                                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB                                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en                                                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB                                                
Get:42 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en [349 kB]                                       
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [182 kB]                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB                                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en                                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB                                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en                                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB                                            
Get:44 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en [140 kB]                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                                              
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [57.4 kB]                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en                                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en                                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en                                             
Fetched 4,733 kB in 16s (291 kB/s)                                                                                     
Reading package lists... Done
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/main amd64 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/restricted amd64 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/main amd64 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/restricted amd64 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```
------------------------------------------------

sudo apt-get upgrade OUTPUT:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic-lts-saucy linux-image-generic-lts-saucy
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common cups-ppdc libcups2 libcups2:i386 libcupscgi1 libcupsdriver1 libcupsimage2
  libcupsimage2:i386 libcupsmime1 libcupsppdc1 linux-generic-lts-saucy linux-libc-dev python3-lxml
16 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.
13 not fully installed or removed.
Need to get 3,801 kB/4,453 kB of archives.
After this operation, 17.4 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libcups2 amd64 1.5.3-0ubuntu8.3 [171 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libcups2 i386 1.5.3-0ubuntu8.3 [172 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libcupsmime1 amd64 1.5.3-0ubuntu8.3 [13.5 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libcupscgi1 amd64 1.5.3-0ubuntu8.3 [29.8 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libcupsimage2 i386 1.5.3-0ubuntu8.3 [52.4 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libcupsimage2 amd64 1.5.3-0ubuntu8.3 [51.7 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libcupsppdc1 amd64 1.5.3-0ubuntu8.3 [52.4 kB]
Get:8 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main cups-common all 1.5.3-0ubuntu8.3 [822 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main cups-bsd amd64 1.5.3-0ubuntu8.3 [44.8 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main cups-client amd64 1.5.3-0ubuntu8.3 [175 kB]           
Get:11 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main cups-ppdc amd64 1.5.3-0ubuntu8.3 [30.6 kB]            
Get:12 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main cups amd64 1.5.3-0ubuntu8.3 [1,300 kB]                
Get:13 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libcupsdriver1 amd64 1.5.3-0ubuntu8.3 [19.6 kB]       
Get:14 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-generic-lts-saucy amd64 3.11.0.22.19 [1,744 B]  
Get:15 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-libc-dev amd64 3.2.0-63.95 [866 kB]             
Fetched 3,801 kB in 17s (214 kB/s)                                                                                     
Preconfiguring packages ...
(Reading database ... 305997 files and directories currently installed.)
Preparing to replace libcups2:i386 1.5.3-0ubuntu8.2 (using .../libcups2_1.5.3-0ubuntu8.3_i386.deb) ...
De-configuring libcups2 ...
Unpacking replacement libcups2:i386 ...
Preparing to replace libcups2 1.5.3-0ubuntu8.2 (using .../libcups2_1.5.3-0ubuntu8.3_amd64.deb) ...
Unpacking replacement libcups2 ...
Setting up libcups2:i386 (1.5.3-0ubuntu8.3) ...
Setting up libcups2 (1.5.3-0ubuntu8.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 305997 files and directories currently installed.)
Preparing to replace libcupsmime1 1.5.3-0ubuntu8.2 (using .../libcupsmime1_1.5.3-0ubuntu8.3_amd64.deb) ...
Unpacking replacement libcupsmime1 ...
Preparing to replace libcupscgi1 1.5.3-0ubuntu8.2 (using .../libcupscgi1_1.5.3-0ubuntu8.3_amd64.deb) ...
Unpacking replacement libcupscgi1 ...
Preparing to replace libcupsimage2 1.5.3-0ubuntu8.2 (using .../libcupsimage2_1.5.3-0ubuntu8.3_amd64.deb) ...
De-configuring libcupsimage2:i386 ...
Unpacking replacement libcupsimage2 ...
Preparing to replace libcupsimage2:i386 1.5.3-0ubuntu8.2 (using .../libcupsimage2_1.5.3-0ubuntu8.3_i386.deb) ...
Unpacking replacement libcupsimage2:i386 ...
Setting up libcupsimage2 (1.5.3-0ubuntu8.3) ...
Setting up libcupsimage2:i386 (1.5.3-0ubuntu8.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 305997 files and directories currently installed.)
Preparing to replace libcupsppdc1 1.5.3-0ubuntu8.2 (using .../libcupsppdc1_1.5.3-0ubuntu8.3_amd64.deb) ...
Unpacking replacement libcupsppdc1 ...
Preparing to replace cups-common 1.5.3-0ubuntu8.2 (using .../cups-common_1.5.3-0ubuntu8.3_all.deb) ...
Unpacking replacement cups-common ...
Preparing to replace cups-bsd 1.5.3-0ubuntu8.2 (using .../cups-bsd_1.5.3-0ubuntu8.3_amd64.deb) ...
Unpacking replacement cups-bsd ...
Preparing to replace cups-client 1.5.3-0ubuntu8.2 (using .../cups-client_1.5.3-0ubuntu8.3_amd64.deb) ...
Unpacking replacement cups-client ...
Preparing to replace cups-ppdc 1.5.3-0ubuntu8.2 (using .../cups-ppdc_1.5.3-0ubuntu8.3_amd64.deb) ...
Unpacking replacement cups-ppdc ...
Preparing to replace cups 1.5.3-0ubuntu8.2 (using .../cups_1.5.3-0ubuntu8.3_amd64.deb) ...
cups stop/waiting
Unpacking replacement cups ...
Preparing to replace libcupsdriver1 1.5.3-0ubuntu8.2 (using .../libcupsdriver1_1.5.3-0ubuntu8.3_amd64.deb) ...
Unpacking replacement libcupsdriver1 ...
Preparing to replace linux-generic-lts-saucy 3.11.0.20.18 (using .../linux-generic-lts-saucy_3.11.0.22.19_amd64.deb) ...
Unpacking replacement linux-generic-lts-saucy ...
Preparing to replace linux-libc-dev 3.2.0-61.93 (using .../linux-libc-dev_3.2.0-63.95_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Processing triggers for doc-base ...
Processing 46 changed doc-base files...
Registering documents with scrollkeeper...
Setting up python3 (3.2.3-0ubuntu1.2) ...
running python rtupdate hooks for python3.2...
E: py3compile:289: Requested versions are not installed
error running python rtupdate hook kivy-examples
dpkg: error processing python3 (--configure):
 subprocess installed post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of python3-tk:
 python3-tk depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.
 python3-tk depends on python3 (<< 3.3); however:
  Package python3 is not configured yet.
dpkg: error processing python3-tk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of idle-python3.2:
 idle-python3.2 depends on python3-tk; however:
  Package python3-tk is not configured yet.
 idle-python3.2 depends on python3.2-tk; however:
  Package python3.2-tk is not installed.
  Package python3-tk which provides python3.2-tk is not configured yet.
dpkg: error processing idle-python3.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of idle3:
 idle3 depends on python3 (>= 3.2.3-0ubuntu1.2); however:
  Package No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                                      No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                          No apport report written because MaxReports has already been reached
                                                      No apport report written because MaxReports has already been reached
  No apport report written because MaxReports has already been reached
                                                                      No apport report written because MaxReports has already been reached
                  No apport report written because MaxReports has already been reached
                                                                                      No apport report written because MaxReports has already been reached
                                  No apport report written because MaxReports has already been reached
                                                                                                      No apport report written because MaxReports has already been reached
                                                  No apport report written because MaxReports has already been reached
                                                                                                                      No apport report written because MaxReports has already been reached
                                                                  python3 is not configured yet.
 idle3 depends on python3-tk; however:
  Package python3-tk is not configured yet.
 idle3 depends on idle-python3.2; however:
  Package idle-python3.2 is not configured yet.
dpkg: error processing idle3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-all:
 python3-all depends on python3 (= 3.2.3-0ubuntu1.2); however:
  Package python3 is not configured yet.
dpkg: error processing python3-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-dev:
 python3-dev depends on python3 (= 3.2.3-0ubuntu1.2); however:
  Package python3 is not configured yet.
dpkg: error processing python3-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-all-dev:
 python3-all-dev depends on python3 (= 3.2.3-0ubuntu1.2); however:
  Package python3 is not configured yet.
 python3-all-dev depends on python3-all (= 3.2.3-0ubuntu1.2); however:
  Package python3-all is not configured yet.
 python3-all-dev depends on python3-dev (= 3.2.3-0ubuntu1.2); however:
  Package python3-dev is not configured yet.
dpkg: error processing python3-all-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-roman:
 python3-roman depends on python3 (>= 3.1.3-13~); however:
  Package python3 is not configured yet.
dpkg: error processing python3-roman (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-docutils:
 python3-docutils depends on python3 (>= 3.1.3-13~); however:
  Package python3 is not configured yet.
 python3-docutils depends on python3-roman; however:
  Package python3-roman is not configured yet.
dpkg: error processing python3-docutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-examples:
 python3-examples depends on python3 (>= 3.2.3-0ubuntu1.2); however:
  Package python3 is not configured yet.
dpkg: error processing python3-examples (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-lxml:
 python3-lxml depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.
 python3-lxml depends on python3 (<< 3.3); however:
  Package python3 is not configured yet.
dpkg: error processing python3-lxml (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pkg-resources:
 python3-pkg-resources depends on python3 (>= 3.1.2-8~); however:
  Package python3 is not configured yet.
dpkg: error processing python3-pkg-resources (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pygments:
 python3-pygments depends on python3 (>= 3.1.3-13~); however:
  Package python3 is not configured yet.
dpkg: error processing python3-pygments (--configure):
 dependency problems - leaving unconfigured
Setting up libcupsmime1 (1.5.3-0ubuntu8.3) ...
Setting up libcupscgi1 (1.5.3-0ubuntu8.3) ...
Setting up libcupsppdc1 (1.5.3-0ubuntu8.3) ...
Setting up cups-common (1.5.3-0ubuntu8.3) ...
Setting up cups-client (1.5.3-0ubuntu8.3) ...
Setting up cups-bsd (1.5.3-0ubuntu8.3) ...
Setting up cups-ppdc (1.5.3-0ubuntu8.3) ...
Setting up cups (1.5.3-0ubuntu8.3) ...
cups start/running, process 5574
Updating PPD files for cups ...
Setting up libcupsdriver1 (1.5.3-0ubuntu8.3) ...
Setting up linux-generic-lts-saucy (3.11.0.22.19) ...
Setting up linux-libc-dev (3.2.0-63.95) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 python3
 python3-tk
 idle-python3.2
 idle3
 python3-all
 python3-dev
 python3-all-dev
 python3-roman
 python3-docutils
 python3-examples
 python3-lxml
 python3-pkg-resources
 python3-pygments
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ptn107 on 2014-05-27
Post the output of
```
dpkg -l | grep -e python3
```
You might have conflicting versions since the dependencies say specifically python 3.2.3.

If all else fails you can remove python3-tk, idle, and all the dependencies and try again from scratch.

---

### Post by david_a2 on 2014-05-28
dpkg -l | grep -e python3 OUTPUT:

iU  idle-python3.2                             3.2.3-0ubuntu3.6                                    IDE for Python (v3.2) using Tkinter
ii  libpython3.2                               3.2.3-0ubuntu3.6                                    Shared Python runtime library (version 3.2)
iF  python3                                    3.2.3-0ubuntu1.2                                    interactive high-level object-oriented language (default python3 version)
iU  python3-all                                3.2.3-0ubuntu1.2                                    package depending on all supported Python 3 runtime versions
iU  python3-all-dev                            3.2.3-0ubuntu1.2                                    package depending on all supported Python 3 development packages
iU  python3-dev                                3.2.3-0ubuntu1.2                                    header files and a static library for Python (default)
iU  python3-docutils                           0.8.1-4ubuntu1                                      text processing system for reStructuredText (implemented in Python 3)
iU  python3-examples                           3.2.3-0ubuntu1.2                                    examples for the Python language (default version)
iU  python3-lxml                               2.3.2-1                                             pythonic binding for the libxml2 and libxslt libraries
ii  python3-minimal                            3.2.3-0ubuntu1.2                                    minimal subset of the Python language (default python3 version)
iU  python3-pkg-resources                      0.6.24-1ubuntu1                                     Package Discovery and Resource Access using pkg_resources
iU  python3-pygments                           1.4+dfsg-2                                          syntax highlighting package written in Python 3
iU  python3-roman                              0.8.1-4ubuntu1                                      module for generating/analyzing Roman numerals for Python 3
iU  python3-tk                                 3.2.3-1                                             Tkinter - Writing Tk applications with Python 3.x
ii  python3.2                                  3.2.3-0ubuntu3.6                                    Interactive high-level object-oriented language (version 3.2)
ii  python3.2-dev                              3.2.3-0ubuntu3.6                                    Header files and a static library for Python (v3.2)
ii  python3.2-examples                         3.2.3-0ubuntu3.6                                    Examples for the Python language (v3.2)
ii  python3.2-minimal                          3.2.3-0ubuntu3.6                                    Minimal subset of the Python language (version 3.2)

---

### Post by ptn107 on 2014-05-28
I would remove these
```
idle-python3.2
libpython3.2
python3
python3-all
python3-all-dev
python3-dev
python3-docutils
python3-examples
python3-lxml
python3-minimal
python3-pkg-resources
python3-pygments
python3-roman
python3-tk
python3.2
python3.2-dev
python3.2-examples
python3.2-minimal
```

purge all your ppas that have anything to do with python

```
sudo apt-get update
```

and then trying to reinstall them.

---

### Post by david_a2 on 2014-05-30
I appreciate all your help with this issue to date. My experience of  removing software on Linux is very limited. I would be extremely grateful if you could give examples of removing, purging and  reinstalling the python software in question.

Thank you for all your help with this matter.

---

