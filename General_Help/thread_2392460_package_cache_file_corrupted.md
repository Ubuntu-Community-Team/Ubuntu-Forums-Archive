---
title: "package cache file corrupted"
date: 2018-05-21
forum: General Help
---

### Post by ashotti2 on 2018-05-21
Hi all,

since few days I receive a system error notification every time I access Ubuntu. 
I executed sudo apt-get update as suggested and I got the Error: The package cache file is corrupted.

Can somebody help me with this?

Thanks a lot in advance!

---

### Post by deadflowr on 2018-05-21
Please post the full output from
```
sudo apt-get update
```

---

### Post by ashotti2 on 2018-05-21
Here it is:

```

Hit:1 http://archive.canonical.com xenial InRelease
Hit:2 http://de.archive.ubuntu.com/ubuntu xenial InRelease                     
Ign:4 http://extras.ubuntu.com/ubuntu xenial InRelease                         
Ign:6 http://extras.ubuntu.com/ubuntu xenial Release                           
Hit:7 http://de.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Get:5 http://archive.ubuntu.com/ubuntu xenial InRelease [247 kB]               
Ign:8 http://extras.ubuntu.com/ubuntu xenial/main Sources.diff/Index           
Hit:9 http://de.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Get:3 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu xenial InRelease [17,5 kB]
Ign:10 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages.diff/Index   
Ign:11 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages.diff/Index    
Hit:12 https://repo.skype.com/deb stable InRelease                             
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main all Packages.diff/Index     
Get:14 http://security.ubuntu.com/ubuntu xenial-security InRelease [107 kB]    
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US           
Ign:16 http://extras.ubuntu.com/ubuntu xenial/main Translation-en.diff/Index   
Ign:17 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata.diff/Index
Ign:18 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons.diff/Index
Ign:19 http://extras.ubuntu.com/ubuntu xenial/main Sources                     
Ign:20 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages              
Ign:21 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages               
Ign:22 http://extras.ubuntu.com/ubuntu xenial/main all Packages                
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US           
Ign:23 http://extras.ubuntu.com/ubuntu xenial/main Translation-en              
Ign:24 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata       
Ign:25 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons          
Ign:19 http://extras.ubuntu.com/ubuntu xenial/main Sources              
Ign:20 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages        
Ign:26 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages       
Ign:21 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages         
Ign:22 http://extras.ubuntu.com/ubuntu xenial/main all Packages                
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US 
Ign:27 http://security.ubuntu.com/ubuntu xenial-security/main Sources
Ign:23 http://extras.ubuntu.com/ubuntu xenial/main Translation-en              
Ign:24 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata       
Ign:28 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu xenial/main amd64 Packages
Ign:25 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons          
Ign:29 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages              
Ign:19 http://extras.ubuntu.com/ubuntu xenial/main Sources                     
Ign:20 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages              
Ign:30 http://archive.ubuntu.com/ubuntu xenial/main Translation-en             
Ign:21 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages               
Ign:22 http://extras.ubuntu.com/ubuntu xenial/main all Packages                
Ign:31 http://security.ubuntu.com/ubuntu xenial-security/restricted Sources    
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US           
Hit:32 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata      
Ign:23 http://extras.ubuntu.com/ubuntu xenial/main Translation-en              
Err:32 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata      
  Hash Sum mismatch
Ign:24 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata       
Ign:33 http://security.ubuntu.com/ubuntu xenial-security/universe Sources      
Ign:34 http://archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons         
Ign:25 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons          
Ign:19 http://extras.ubuntu.com/ubuntu xenial/main Sources                     
Ign:35 http://security.ubuntu.com/ubuntu xenial-security/multiverse Sources    
Ign:20 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages              
Ign:36 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages         
Ign:21 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages               
Ign:22 http://extras.ubuntu.com/ubuntu xenial/main all Packages                
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US           
Ign:37 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages          
Ign:23 http://extras.ubuntu.com/ubuntu xenial/main Translation-en              
Ign:24 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata       
Ign:38 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en         
Ign:39 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages   
Ign:25 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons          
Ign:40 http://archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata  
Ign:19 http://extras.ubuntu.com/ubuntu xenial/main Sources                     
Ign:41 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages    
Ign:20 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages              
Ign:21 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages               
Ign:42 http://archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons     
Ign:22 http://extras.ubuntu.com/ubuntu xenial/main all Packages                
Ign:43 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en   
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US           
Ign:44 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages       
Ign:23 http://extras.ubuntu.com/ubuntu xenial/main Translation-en              
Ign:24 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata       
Ign:45 http://archive.ubuntu.com/ubuntu xenial/restricted i386 Packages        
Get:46 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [67,7 kB]
Ign:25 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons          
Err:19 http://extras.ubuntu.com/ubuntu xenial/main Sources                     
  404  Not Found [IP: 2001:67c:1360:8c01::23 80]
Get:47 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [68,0 kB]
Ign:20 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages              
Ign:21 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages               
Ign:48 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en       
Ign:49 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages
Ign:22 http://extras.ubuntu.com/ubuntu xenial/main all Packages                
Ign:23 http://extras.ubuntu.com/ubuntu xenial/main Translation-en              
Ign:24 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata       
Ign:50 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 DEP-11 Metadata
Ign:51 http://security.ubuntu.com/ubuntu xenial-security/restricted i386 Packages
Ign:25 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons          
Ign:52 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu xenial/main i386 Packages
Ign:53 http://security.ubuntu.com/ubuntu xenial-security/restricted Translation-en
Ign:54 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu xenial/main Translation-en
Ign:28 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu xenial/main amd64 Packages
Hit:55 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata
Err:55 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata
  Hash Sum mismatch
Ign:52 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu xenial/main i386 Packages
Ign:56 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
Ign:54 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu xenial/main Translation-en
Get:28 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu xenial/main amd64 Packages [2.702 B]
Ign:52 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu xenial/main i386 Packages
Ign:57 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages
Get:54 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu xenial/main Translation-en [2.123 B]
Get:58 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [130 kB]
Err:52 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu xenial/main i386 Packages
  Could not open file /var/lib/apt/lists/partial/ppa.launchpad.net_pmjdebruijn_darktable-release_ubuntu_dists_xenial_main_binary-i386_Packages.xz - open (13: Permission denied)
Get:59 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [107 kB]
Get:60 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [147 kB]
Get:61 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [3.464 B]
Get:62 http://security.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages [3.624 B]
Get:63 http://security.ubuntu.com/ubuntu xenial-security/multiverse Translation-en [1.744 B]
Hit:64 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata
Hit:65 http://security.ubuntu.com/ubuntu xenial-security/multiverse DEP-11 64x64 Icons
Fetched 371 kB in 2s (124 kB/s)

** (appstreamcli:13079): WARNING **: No origin found for file archive.canonical.com_dists_xenial_partner_dep11_Components-amd64.yml.gz

** (appstreamcli:13079): WARNING **: No origin found for file ppa.launchpad.net_pmjdebruijn_darktable-release_ubuntu_dists_xenial_main_dep11_Components-amd64.yml.gz
Segmentation fault (core dumped)
Reading package lists... Error!
W: The repository 'http://extras.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/xenial/main/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::23 80]
E: Failed to fetch http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu/dists/xenial/main/binary-i386/Packages  Could not open file /var/lib/apt/lists/partial/ppa.launchpad.net_pmjdebruijn_darktable-release_ubuntu_dists_xenial_main_binary-i386_Packages.xz - open (13: Permission denied)
E: Failed to fetch store:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_xenial_main_dep11_Components-amd64.yml.gz  Hash Sum mismatch
E: Failed to fetch store:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_dep11_Components-amd64.yml.gz  Hash Sum mismatch
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh > /dev/null; fi'
E: Sub-process returned an error code
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_main_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_main_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_main_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_main_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_universe_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_universe_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_universe_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_multiverse_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_multiverse_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_multiverse_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_multiverse_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_xenial_main_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_xenial_main_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_xenial_main_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_xenial_main_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_main_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_main_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_main_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_main_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_universe_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_restricted_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_restricted_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_restricted_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_restricted_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_multiverse_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_multiverse_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_multiverse_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_multiverse_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_pmjdebruijn_darktable-release_ubuntu_dists_xenial_main_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_pmjdebruijn_darktable-release_ubuntu_dists_xenial_main_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_pmjdebruijn_darktable-release_ubuntu_dists_xenial_main_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_pmjdebruijn_darktable-release_ubuntu_dists_xenial_main_i18n_Translation-en (1)
W: You may want to run apt-get update to correct these problems
E: The package cache file is corrupted

```

---

### Post by deadflowr on 2018-05-21
I don't think extras exist beyond 14.10.
Try opening Software and Updates and go to other software and uncheck the Independent Software (or some name to that affect).
That should be it, from memory it relates to the extras repository.

Then open a terminal and run
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

Then post back the results again.

---

### Post by ashotti2 on 2018-05-22
Thanks! This is what I did:
opened Software&Updates, under Other Software unchecked the two following:
- [https://repo.skype.com/deb](https://repo.skype.com/deb) stable main
- [https://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu](https://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu) xenial main

Other things checked (I left them so) were [https://extras.ubuntu.com/ubuntu](https://extras.ubuntu.com/ubuntu) xenial and similar

This is what I got after running the two commands you wrote:

```

Get:1 http://de.archive.ubuntu.com/ubuntu xenial InRelease [247 kB]
Get:2 http://archive.canonical.com xenial InRelease [11,5 kB]                  
Ign:3 http://extras.ubuntu.com/ubuntu xenial InRelease                         
Get:4 http://archive.ubuntu.com/ubuntu xenial InRelease [247 kB]               
Ign:5 http://extras.ubuntu.com/ubuntu xenial Release                           
Ign:6 http://extras.ubuntu.com/ubuntu xenial/main Sources                      
Ign:7 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages               
Get:8 http://archive.canonical.com xenial/partner amd64 Packages [3.124 B]     
Ign:9 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages                
Get:10 http://archive.canonical.com xenial/partner i386 Packages [3.124 B]     
Get:11 http://archive.canonical.com xenial/partner Translation-en [1.616 B]    
Ign:12 http://extras.ubuntu.com/ubuntu xenial/main all Packages                
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US           
Get:14 http://de.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]   
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main Translation-en              
Get:16 http://de.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB] 
Ign:17 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata       
Ign:18 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons          
Get:19 http://de.archive.ubuntu.com/ubuntu xenial/main Sources [868 kB]        
Ign:6 http://extras.ubuntu.com/ubuntu xenial/main Sources                      
Ign:7 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages               
Ign:9 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages                
Ign:12 http://extras.ubuntu.com/ubuntu xenial/main all Packages                
Get:20 http://de.archive.ubuntu.com/ubuntu xenial/restricted Sources [4.808 B] 
Get:21 http://de.archive.ubuntu.com/ubuntu xenial/universe Sources [7.728 kB]  
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US           
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main Translation-en              
Ign:17 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata       
Ign:18 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons          
Ign:6 http://extras.ubuntu.com/ubuntu xenial/main Sources                      
Ign:7 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages               
Ign:9 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages                
Ign:12 http://extras.ubuntu.com/ubuntu xenial/main all Packages                
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US           
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main Translation-en              
Ign:17 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata       
Ign:18 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons          
Ign:6 http://extras.ubuntu.com/ubuntu xenial/main Sources                      
Ign:7 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages               
Ign:9 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages                
Ign:12 http://extras.ubuntu.com/ubuntu xenial/main all Packages                
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US           
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main Translation-en              
Ign:17 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata       
Ign:18 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons          
Ign:6 http://extras.ubuntu.com/ubuntu xenial/main Sources                      
Ign:7 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages               
Ign:9 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages                
Ign:12 http://extras.ubuntu.com/ubuntu xenial/main all Packages                
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US           
Get:22 http://de.archive.ubuntu.com/ubuntu xenial/multiverse Sources [179 kB]  
Get:23 http://de.archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1.201 kB]
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main Translation-en              
Ign:17 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata       
Ign:18 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons          
Err:6 http://extras.ubuntu.com/ubuntu xenial/main Sources                      
  404  Not Found [IP: 2001:67c:1360:8c01::23 80]
Ign:7 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages               
Get:24 http://de.archive.ubuntu.com/ubuntu xenial/main i386 Packages [1.196 kB]
Ign:9 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages                
Ign:12 http://extras.ubuntu.com/ubuntu xenial/main all Packages                
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US           
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main Translation-en              
Get:25 http://de.archive.ubuntu.com/ubuntu xenial/main Translation-en [568 kB] 
Ign:17 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata       
Ign:18 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons          
Get:26 http://de.archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata [733 kB]
Get:27 http://de.archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons [409 kB]
Get:28 http://de.archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages [8.344 B]
Get:29 http://de.archive.ubuntu.com/ubuntu xenial/restricted i386 Packages [8.684 B]
Get:30 http://de.archive.ubuntu.com/ubuntu xenial/restricted Translation-en [2.908 B]
Get:31 http://de.archive.ubuntu.com/ubuntu xenial/restricted amd64 DEP-11 Metadata [186 B]
Get:32 http://de.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [7.532 kB]
Get:33 http://de.archive.ubuntu.com/ubuntu xenial/universe i386 Packages [7.512 kB]                                                
Get:34 http://de.archive.ubuntu.com/ubuntu xenial/universe Translation-en [4.354 kB]                                                       
Get:35 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1.201 kB]                                                              
Get:36 http://de.archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata [3.410 kB]                                                
Get:37 http://de.archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons [7.448 kB]                                                   
Get:38 http://de.archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages [144 kB]                                                       
Get:39 http://de.archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages [140 kB]                                                        
Get:40 http://de.archive.ubuntu.com/ubuntu xenial/multiverse Translation-en [106 kB]                                                       
Get:41 http://de.archive.ubuntu.com/ubuntu xenial/multiverse amd64 DEP-11 Metadata [63,8 kB]                                               
Get:42 http://de.archive.ubuntu.com/ubuntu xenial/multiverse DEP-11 64x64 Icons [230 kB]                                                   
Get:43 http://de.archive.ubuntu.com/ubuntu xenial-updates/main Sources [305 kB]                                                            
Get:44 http://de.archive.ubuntu.com/ubuntu xenial-updates/restricted Sources [2.524 B]                                                     
Get:45 http://de.archive.ubuntu.com/ubuntu xenial-updates/universe Sources [203 kB]                                                        
Get:46 http://de.archive.ubuntu.com/ubuntu xenial-updates/multiverse Sources [8.404 B]                                                     
Get:47 http://de.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [783 kB]                                                     
Get:48 http://de.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [718 kB]                                                      
Get:49 http://de.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [324 kB]                                                     
Get:50 http://de.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [319 kB]                                              
Get:51 http://de.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [230 kB]                                                 
Get:52 http://de.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages [7.560 B]                                              
Get:53 http://de.archive.ubuntu.com/ubuntu xenial-updates/restricted i386 Packages [7.524 B]                                               
Get:54 http://de.archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en [2.272 B]                                              
Get:55 http://de.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata [157 B]                                         
Get:56 http://de.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [630 kB]                                                 
Get:57 http://de.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [577 kB]                                                  
Get:58 http://de.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [253 kB]                                                 
Get:59 http://de.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [246 kB]                                          
Get:60 http://de.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [331 kB]                                             
Get:61 http://de.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [16,4 kB]                                              
Get:62 http://de.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [15,5 kB]                                               
Get:63 http://de.archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en [8.344 B]                                              
Get:64 http://de.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5.964 B]                                       
Get:65 http://de.archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons [14,3 kB]                                          
Get:66 http://de.archive.ubuntu.com/ubuntu xenial-backports/main Sources [3.436 B]                                                         
Get:67 http://de.archive.ubuntu.com/ubuntu xenial-backports/universe Sources [5.820 B]                                           
Get:68 http://de.archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages [4.844 B]                                                  
Get:69 http://de.archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages [4.836 B]                                                   
Get:70 http://de.archive.ubuntu.com/ubuntu xenial-backports/main Translation-en [3.220 B]                                        
Get:71 http://de.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3.324 B]                                           
Get:72 http://de.archive.ubuntu.com/ubuntu xenial-backports/main DEP-11 64x64 Icons [29 B]                                                 
Get:73 http://de.archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 DEP-11 Metadata [194 B]                                       
Get:74 http://de.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 Packages [7.400 B]                                              
Get:75 http://de.archive.ubuntu.com/ubuntu xenial-backports/universe i386 Packages [7.080 B]                                               
Get:76 http://de.archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en [3.996 B]                                              
Get:77 http://de.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [5.088 B]                                       
Get:78 http://de.archive.ubuntu.com/ubuntu xenial-backports/universe DEP-11 64x64 Icons [2.717 B]                                          
Get:79 http://de.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [216 B]                                       
Get:80 http://de.archive.ubuntu.com/ubuntu xenial-backports/multiverse DEP-11 64x64 Icons [29 B]                                           
Get:81 http://security.ubuntu.com/ubuntu xenial-security InRelease [107 kB]                                                                
Get:82 http://security.ubuntu.com/ubuntu xenial-security/main Sources [122 kB]                   
Get:83 http://security.ubuntu.com/ubuntu xenial-security/restricted Sources [2.116 B]                                                      
Get:84 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [65,4 kB]                                                        
Get:85 http://security.ubuntu.com/ubuntu xenial-security/multiverse Sources [2.120 B]                                                      
Get:86 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [499 kB]                                                      
Get:87 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [442 kB]                                                       
Get:88 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [215 kB]                                                      
Get:89 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [67,7 kB]                                              
Get:90 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [68,0 kB]                                                 
Get:91 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [7.224 B]                                               
Get:92 http://security.ubuntu.com/ubuntu xenial-security/restricted i386 Packages [7.224 B]                                                
Get:93 http://security.ubuntu.com/ubuntu xenial-security/restricted Translation-en [2.152 B]                                               
Get:94 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata [200 B]                                          
Get:95 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [350 kB]                                                  
Get:96 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [301 kB]                                                   
Get:97 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [130 kB]                                                  
Get:98 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [107 kB]                                           
Get:99 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [142 kB]                                              
Get:100 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [3.464 B]                                              
Get:101 http://security.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages [3.624 B]                                               
Get:102 http://security.ubuntu.com/ubuntu xenial-security/multiverse Translation-en [1.744 B]                                              
Get:103 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [212 B]                                         
Get:104 http://security.ubuntu.com/ubuntu xenial-security/multiverse DEP-11 64x64 Icons [29 B]                                             
Get:105 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages [1.196 kB]                                                              
Get:106 http://archive.ubuntu.com/ubuntu xenial/main Translation-en [568 kB]                                                               
Get:107 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata [733 kB]                                                        
Get:108 http://archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons [409 kB]                                                           
Get:109 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [7.532 kB]                                                         
Get:110 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages [7.512 kB]                                                          
Get:111 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en [4.354 kB]                                                         
Get:112 http://archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata [3.410 kB]                                                  
Get:113 http://archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons [7.448 kB]                                                     
Get:114 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages [8.344 B]                                                        
Get:115 http://archive.ubuntu.com/ubuntu xenial/restricted i386 Packages [8.684 B]                                                         
Get:116 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en [2.908 B]                                                        
Get:117 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 DEP-11 Metadata [186 B]                                                   
Get:118 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages [144 kB]                                                         
Get:119 http://archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages [140 kB]                                                          
Get:120 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en [106 kB]                                                         
Get:121 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 DEP-11 Metadata [63,8 kB]                                                 
Get:122 http://archive.ubuntu.com/ubuntu xenial/multiverse DEP-11 64x64 Icons [230 kB]                                                     
Fetched 87,3 MB in 4min 45s (306 kB/s)                                                                                                     
Reading package lists... Done
W: The repository 'http://extras.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/xenial/main/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::23 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by deadflowr on 2018-05-22
You probably should done the opposite and unchecked and disabled the extras repo entry and left the skype and darktable ppa enabled.
Since there is no extras repos for 16.04.

There was no skype problem and the darktable error was a hashsum mismatch, the same as the security repo error.

Hash sum mismatch errors can be usually cleared when running the the remove command I posted.
(It basically empties the list folder and allows a fresh download of the needed files.
Sometimes those files get corrupted during transport or by other means and then stick around causing unwanted frustrations)

There is no fix for the extras repo problem, so best to disable it.

---

### Post by ashotti2 on 2018-05-22
Thank you, I followed your suggestion and unchecked the extras and enabled again skype and dark table. Then I ran the two commands again and everything looks ok.

Thanks a lot for your help!

---

