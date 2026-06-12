---
title: "Update from 17.04 to 17.10 Issues"
date: 2019-04-25
forum: General Help
---

### Post by kodingkoning on 2019-04-25
Hi,

I am trying to update my Ubuntu 17.04 installation, but I'm running into some problems.

I tried to follow the instructions in this thread, but either I'm doing something wrong, or what they did isn't applicable to me.
[https://ubuntuforums.org/showthread.php?t=2382832&page=2](https://ubuntuforums.org/showthread.php?t=2382832&page=2)
That sent me here:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

At this point, my sources.list is:
```

## EOL upgrade sources.list# Required
deb http://old-releases.ubuntu.com/ubuntu/ CODENAME main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ CODENAME-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ CODENAME-security main restricted universe multiverse


# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ CODENAME-backports main restricted universe multiverse

```


When I tried to run sudo apt-get update again, it was more promising than the first time, but it failed to fetch some files.

What should I try next?

Output:
```

Get:1 https://deb.nodesource.com/node_8.x zesty InRelease [4,645 B]
Hit:2 http://linux.lsdev.sil.org/ubuntu zesty InRelease                                                 
Ign:3 http://old-releases.ubuntu.com/ubuntu CODENAME InRelease                                          
Hit:4 http://linux.lsdev.sil.org/ubuntu zesty-experimental InRelease                           
Hit:5 http://ppa.launchpad.net/ansible/ansible/ubuntu zesty InRelease    
Ign:7 http://old-releases.ubuntu.com/ubuntu CODENAME-updates InRelease                              
Ign:9 http://old-releases.ubuntu.com/ubuntu CODENAME-security InRelease                             
Hit:10 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu zesty InRelease
Ign:12 http://old-releases.ubuntu.com/ubuntu CODENAME Release                                        
Hit:6 https://packagecloud.io/AtomEditor/atom/any any InRelease                                      
Ign:13 http://old-releases.ubuntu.com/ubuntu CODENAME-updates Release    
Hit:14 http://ppa.launchpad.net/swi-prolog/stable/ubuntu zesty InRelease 
Ign:15 http://old-releases.ubuntu.com/ubuntu CODENAME-security Release
Hit:11 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease
Ign:16 http://old-releases.ubuntu.com/ubuntu CODENAME/main amd64 Packages
Ign:17 http://old-releases.ubuntu.com/ubuntu CODENAME/main all Packages
Get:8 https://packagecloud.io/github/git-lfs/ubuntu zesty InRelease [23.2 kB]
Ign:18 http://old-releases.ubuntu.com/ubuntu CODENAME/main i386 Packages
Err:8 https://packagecloud.io/github/git-lfs/ubuntu zesty InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B05F25D762E3157
Ign:19 http://old-releases.ubuntu.com/ubuntu CODENAME/main Translation-en
Ign:20 http://old-releases.ubuntu.com/ubuntu CODENAME/main Translation-en_US
Ign:21 http://old-releases.ubuntu.com/ubuntu CODENAME/main all DEP-11 Metadata
Ign:22 http://old-releases.ubuntu.com/ubuntu CODENAME/main amd64 DEP-11 Metadata
Ign:23 http://old-releases.ubuntu.com/ubuntu CODENAME/main DEP-11 64x64 Icons
Ign:24 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted amd64 Packages
Ign:25 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted i386 Packages
Ign:26 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted all Packages
Ign:27 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted Translation-en
Ign:28 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted Translation-en_US
Ign:29 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted all DEP-11 Metadata
Ign:30 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted amd64 DEP-11 Metadata
Ign:31 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted DEP-11 64x64 Icons
Ign:32 http://old-releases.ubuntu.com/ubuntu CODENAME/universe amd64 Packages
Ign:33 http://old-releases.ubuntu.com/ubuntu CODENAME/universe i386 Packages
Ign:34 http://old-releases.ubuntu.com/ubuntu CODENAME/universe all Packages
Ign:35 http://old-releases.ubuntu.com/ubuntu CODENAME/universe Translation-en
Ign:36 http://old-releases.ubuntu.com/ubuntu CODENAME/universe Translation-en_US                        
Ign:37 http://old-releases.ubuntu.com/ubuntu CODENAME/universe amd64 DEP-11 Metadata                    
Ign:38 http://old-releases.ubuntu.com/ubuntu CODENAME/universe all DEP-11 Metadata                      
Ign:39 http://old-releases.ubuntu.com/ubuntu CODENAME/universe DEP-11 64x64 Icons                       
Ign:40 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse i386 Packages                          
Ign:41 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse amd64 Packages                         
Ign:42 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse all Packages                           
Ign:43 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse Translation-en_US                      
Ign:44 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse Translation-en                         
Ign:45 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse all DEP-11 Metadata                    
Ign:46 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse amd64 DEP-11 Metadata                  
Ign:47 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse DEP-11 64x64 Icons                     
Ign:48 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main amd64 Packages                       
Ign:49 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main all Packages                         
Ign:50 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main i386 Packages                        
Ign:51 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main Translation-en                       
Ign:52 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main Translation-en_US                    
Ign:53 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main all DEP-11 Metadata                  
Ign:54 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main amd64 DEP-11 Metadata                
Ign:55 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main DEP-11 64x64 Icons                   
Ign:56 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted amd64 Packages                 
Ign:57 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted all Packages                   
Ign:58 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted i386 Packages
Ign:59 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted Translation-en
Ign:60 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted Translation-en_US
Ign:61 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted all DEP-11 Metadata
Ign:62 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted amd64 DEP-11 Metadata
Ign:63 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted DEP-11 64x64 Icons
Ign:64 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe all Packages
Ign:65 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe i386 Packages
Ign:66 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe amd64 Packages
Ign:67 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe Translation-en
Ign:68 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe Translation-en_US
Ign:69 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe amd64 DEP-11 Metadata
Ign:70 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe all DEP-11 Metadata
Ign:71 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe DEP-11 64x64 Icons
Ign:72 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse amd64 Packages
Ign:73 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse all Packages
Ign:74 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse i386 Packages
Ign:75 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse Translation-en
Ign:76 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse Translation-en_US
Ign:77 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse all DEP-11 Metadata
Ign:78 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse amd64 DEP-11 Metadata
Ign:79 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse DEP-11 64x64 Icons
Ign:80 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main all Packages
Ign:81 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main i386 Packages
Ign:82 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main amd64 Packages
Ign:83 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main Translation-en
Ign:84 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main Translation-en_US
Ign:85 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main amd64 DEP-11 Metadata
Ign:86 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main all DEP-11 Metadata
Ign:87 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main DEP-11 64x64 Icons
Ign:88 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted i386 Packages
Ign:89 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted all Packages
Ign:90 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted amd64 Packages
Ign:91 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted Translation-en
Ign:92 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted Translation-en_US
Ign:93 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted amd64 DEP-11 Metadata
Ign:94 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted all DEP-11 Metadata
Ign:95 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted DEP-11 64x64 Icons
Ign:96 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe all Packages
Ign:97 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe amd64 Packages
Ign:98 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe i386 Packages
Ign:99 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe Translation-en
Ign:100 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe Translation-en_US
Ign:101 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe all DEP-11 Metadata
Ign:102 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe amd64 DEP-11 Metadata
Ign:103 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe DEP-11 64x64 Icons
Ign:104 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse i386 Packages
Ign:105 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse amd64 Packages
Ign:106 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse all Packages
Ign:107 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse Translation-en_US
Ign:108 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse Translation-en
Ign:109 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse amd64 DEP-11 Metadata
Ign:110 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse all DEP-11 Metadata
Ign:111 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse DEP-11 64x64 Icons
Ign:16 http://old-releases.ubuntu.com/ubuntu CODENAME/main amd64 Packages
Ign:17 http://old-releases.ubuntu.com/ubuntu CODENAME/main all Packages
Ign:18 http://old-releases.ubuntu.com/ubuntu CODENAME/main i386 Packages
Ign:19 http://old-releases.ubuntu.com/ubuntu CODENAME/main Translation-en
Ign:20 http://old-releases.ubuntu.com/ubuntu CODENAME/main Translation-en_US
Ign:21 http://old-releases.ubuntu.com/ubuntu CODENAME/main all DEP-11 Metadata
Ign:22 http://old-releases.ubuntu.com/ubuntu CODENAME/main amd64 DEP-11 Metadata
Ign:23 http://old-releases.ubuntu.com/ubuntu CODENAME/main DEP-11 64x64 Icons
Ign:24 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted amd64 Packages
Ign:25 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted i386 Packages
Ign:26 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted all Packages
Ign:27 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted Translation-en
Ign:28 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted Translation-en_US
Ign:29 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted all DEP-11 Metadata
Ign:30 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted amd64 DEP-11 Metadata
Ign:31 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted DEP-11 64x64 Icons
Ign:32 http://old-releases.ubuntu.com/ubuntu CODENAME/universe amd64 Packages
Ign:33 http://old-releases.ubuntu.com/ubuntu CODENAME/universe i386 Packages
Ign:34 http://old-releases.ubuntu.com/ubuntu CODENAME/universe all Packages
Ign:35 http://old-releases.ubuntu.com/ubuntu CODENAME/universe Translation-en
Ign:36 http://old-releases.ubuntu.com/ubuntu CODENAME/universe Translation-en_US
Ign:37 http://old-releases.ubuntu.com/ubuntu CODENAME/universe amd64 DEP-11 Metadata
Ign:38 http://old-releases.ubuntu.com/ubuntu CODENAME/universe all DEP-11 Metadata
Ign:39 http://old-releases.ubuntu.com/ubuntu CODENAME/universe DEP-11 64x64 Icons
Ign:40 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse i386 Packages
Ign:41 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse amd64 Packages
Ign:42 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse all Packages
Ign:43 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse Translation-en_US
Ign:44 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse Translation-en
Ign:45 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse all DEP-11 Metadata
Ign:46 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse amd64 DEP-11 Metadata
Ign:47 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse DEP-11 64x64 Icons
Ign:48 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main amd64 Packages
Ign:49 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main all Packages
Ign:50 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main i386 Packages
Ign:51 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main Translation-en
Ign:52 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main Translation-en_US
Ign:53 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main all DEP-11 Metadata
Ign:54 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main amd64 DEP-11 Metadata
Ign:55 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main DEP-11 64x64 Icons
Ign:56 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted amd64 Packages
Ign:57 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted all Packages
Ign:58 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted i386 Packages
Ign:59 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted Translation-en
Ign:60 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted Translation-en_US
Ign:61 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted all DEP-11 Metadata
Ign:62 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted amd64 DEP-11 Metadata
Ign:63 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted DEP-11 64x64 Icons
Ign:64 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe all Packages
Ign:65 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe i386 Packages
Ign:66 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe amd64 Packages
Ign:67 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe Translation-en
Ign:68 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe Translation-en_US
Ign:69 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe amd64 DEP-11 Metadata
Ign:70 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe all DEP-11 Metadata
Ign:71 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe DEP-11 64x64 Icons
Ign:72 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse amd64 Packages
Ign:73 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse all Packages
Ign:74 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse i386 Packages
Ign:75 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse Translation-en
Ign:76 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse Translation-en_US
Ign:77 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse all DEP-11 Metadata
Ign:78 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse amd64 DEP-11 Metadata
Ign:79 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse DEP-11 64x64 Icons
Ign:80 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main all Packages
Ign:81 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main i386 Packages
Ign:82 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main amd64 Packages
Ign:83 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main Translation-en
Ign:84 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main Translation-en_US
Ign:85 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main amd64 DEP-11 Metadata
Ign:86 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main all DEP-11 Metadata
Ign:87 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main DEP-11 64x64 Icons
Ign:88 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted i386 Packages
Ign:89 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted all Packages
Ign:90 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted amd64 Packages
Ign:91 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted Translation-en
Ign:92 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted Translation-en_US
Ign:93 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted amd64 DEP-11 Metadata
Ign:94 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted all DEP-11 Metadata
Ign:95 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted DEP-11 64x64 Icons
Ign:96 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe all Packages
Ign:97 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe amd64 Packages
Ign:98 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe i386 Packages
Ign:99 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe Translation-en
Ign:100 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe Translation-en_US
Ign:101 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe all DEP-11 Metadata
Ign:102 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe amd64 DEP-11 Metadata
Ign:103 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe DEP-11 64x64 Icons
Ign:104 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse i386 Packages
Ign:105 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse amd64 Packages
Ign:106 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse all Packages
Ign:107 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse Translation-en_US
Ign:108 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse Translation-en
Ign:109 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse amd64 DEP-11 Metadata
Ign:110 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse all DEP-11 Metadata
Ign:111 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse DEP-11 64x64 Icons
Ign:16 http://old-releases.ubuntu.com/ubuntu CODENAME/main amd64 Packages
Ign:17 http://old-releases.ubuntu.com/ubuntu CODENAME/main all Packages
Ign:18 http://old-releases.ubuntu.com/ubuntu CODENAME/main i386 Packages
Ign:19 http://old-releases.ubuntu.com/ubuntu CODENAME/main Translation-en
Ign:20 http://old-releases.ubuntu.com/ubuntu CODENAME/main Translation-en_US
Ign:21 http://old-releases.ubuntu.com/ubuntu CODENAME/main all DEP-11 Metadata
Ign:22 http://old-releases.ubuntu.com/ubuntu CODENAME/main amd64 DEP-11 Metadata
Ign:23 http://old-releases.ubuntu.com/ubuntu CODENAME/main DEP-11 64x64 Icons
Ign:24 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted amd64 Packages
Ign:25 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted i386 Packages
Ign:26 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted all Packages
Ign:27 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted Translation-en
Ign:28 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted Translation-en_US
Ign:29 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted all DEP-11 Metadata
Ign:30 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted amd64 DEP-11 Metadata
Ign:31 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted DEP-11 64x64 Icons
Ign:32 http://old-releases.ubuntu.com/ubuntu CODENAME/universe amd64 Packages
Ign:33 http://old-releases.ubuntu.com/ubuntu CODENAME/universe i386 Packages
Ign:34 http://old-releases.ubuntu.com/ubuntu CODENAME/universe all Packages
Ign:35 http://old-releases.ubuntu.com/ubuntu CODENAME/universe Translation-en
Ign:36 http://old-releases.ubuntu.com/ubuntu CODENAME/universe Translation-en_US
Ign:37 http://old-releases.ubuntu.com/ubuntu CODENAME/universe amd64 DEP-11 Metadata
Ign:38 http://old-releases.ubuntu.com/ubuntu CODENAME/universe all DEP-11 Metadata
Ign:39 http://old-releases.ubuntu.com/ubuntu CODENAME/universe DEP-11 64x64 Icons
Ign:40 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse i386 Packages
Ign:41 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse amd64 Packages
Ign:42 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse all Packages
Ign:43 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse Translation-en_US
Ign:44 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse Translation-en
Ign:45 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse all DEP-11 Metadata
Ign:46 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse amd64 DEP-11 Metadata
Ign:47 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse DEP-11 64x64 Icons
Ign:48 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main amd64 Packages
Ign:49 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main all Packages
Ign:50 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main i386 Packages
Ign:51 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main Translation-en
Ign:52 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main Translation-en_US
Ign:53 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main all DEP-11 Metadata
Ign:54 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main amd64 DEP-11 Metadata
Ign:55 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main DEP-11 64x64 Icons
Ign:56 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted amd64 Packages
Ign:57 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted all Packages
Ign:58 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted i386 Packages
Ign:59 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted Translation-en
Ign:60 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted Translation-en_US
Ign:61 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted all DEP-11 Metadata
Ign:62 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted amd64 DEP-11 Metadata
Ign:63 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted DEP-11 64x64 Icons
Ign:64 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe all Packages
Ign:65 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe i386 Packages
Ign:66 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe amd64 Packages
Ign:67 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe Translation-en
Ign:68 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe Translation-en_US
Ign:69 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe amd64 DEP-11 Metadata
Ign:70 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe all DEP-11 Metadata
Ign:71 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe DEP-11 64x64 Icons
Ign:72 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse amd64 Packages
Ign:73 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse all Packages
Ign:74 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse i386 Packages
Ign:75 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse Translation-en
Ign:76 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse Translation-en_US
Ign:77 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse all DEP-11 Metadata
Ign:78 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse amd64 DEP-11 Metadata
Ign:79 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse DEP-11 64x64 Icons
Ign:80 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main all Packages
Ign:81 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main i386 Packages
Ign:82 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main amd64 Packages
Ign:83 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main Translation-en
Ign:84 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main Translation-en_US
Ign:85 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main amd64 DEP-11 Metadata
Ign:86 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main all DEP-11 Metadata
Ign:87 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main DEP-11 64x64 Icons
Ign:88 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted i386 Packages
Ign:89 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted all Packages
Ign:90 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted amd64 Packages
Ign:91 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted Translation-en
Ign:92 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted Translation-en_US
Ign:93 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted amd64 DEP-11 Metadata
Ign:94 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted all DEP-11 Metadata
Ign:95 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted DEP-11 64x64 Icons
Ign:96 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe all Packages
Ign:97 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe amd64 Packages
Ign:98 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe i386 Packages
Ign:99 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe Translation-en
Ign:100 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe Translation-en_US
Ign:101 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe all DEP-11 Metadata
Ign:102 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe amd64 DEP-11 Metadata
Ign:103 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe DEP-11 64x64 Icons
Ign:104 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse i386 Packages
Ign:105 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse amd64 Packages
Ign:106 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse all Packages
Ign:107 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse Translation-en_US
Ign:108 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse Translation-en
Ign:109 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse amd64 DEP-11 Metadata
Ign:110 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse all DEP-11 Metadata
Ign:111 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse DEP-11 64x64 Icons
Ign:16 http://old-releases.ubuntu.com/ubuntu CODENAME/main amd64 Packages
Ign:17 http://old-releases.ubuntu.com/ubuntu CODENAME/main all Packages
Ign:18 http://old-releases.ubuntu.com/ubuntu CODENAME/main i386 Packages
Ign:19 http://old-releases.ubuntu.com/ubuntu CODENAME/main Translation-en
Ign:20 http://old-releases.ubuntu.com/ubuntu CODENAME/main Translation-en_US
Ign:21 http://old-releases.ubuntu.com/ubuntu CODENAME/main all DEP-11 Metadata
Ign:22 http://old-releases.ubuntu.com/ubuntu CODENAME/main amd64 DEP-11 Metadata
Ign:23 http://old-releases.ubuntu.com/ubuntu CODENAME/main DEP-11 64x64 Icons
Ign:24 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted amd64 Packages
Ign:25 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted i386 Packages
Ign:26 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted all Packages
Ign:27 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted Translation-en
Ign:28 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted Translation-en_US
Ign:29 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted all DEP-11 Metadata
Ign:30 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted amd64 DEP-11 Metadata
Ign:31 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted DEP-11 64x64 Icons
Ign:32 http://old-releases.ubuntu.com/ubuntu CODENAME/universe amd64 Packages
Ign:33 http://old-releases.ubuntu.com/ubuntu CODENAME/universe i386 Packages
Ign:34 http://old-releases.ubuntu.com/ubuntu CODENAME/universe all Packages
Ign:35 http://old-releases.ubuntu.com/ubuntu CODENAME/universe Translation-en
Ign:36 http://old-releases.ubuntu.com/ubuntu CODENAME/universe Translation-en_US
Ign:37 http://old-releases.ubuntu.com/ubuntu CODENAME/universe amd64 DEP-11 Metadata
Ign:38 http://old-releases.ubuntu.com/ubuntu CODENAME/universe all DEP-11 Metadata
Ign:39 http://old-releases.ubuntu.com/ubuntu CODENAME/universe DEP-11 64x64 Icons
Ign:40 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse i386 Packages
Ign:41 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse amd64 Packages
Ign:42 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse all Packages
Ign:43 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse Translation-en_US
Ign:44 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse Translation-en
Ign:45 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse all DEP-11 Metadata
Ign:46 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse amd64 DEP-11 Metadata
Ign:47 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse DEP-11 64x64 Icons
Ign:48 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main amd64 Packages
Ign:49 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main all Packages
Ign:50 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main i386 Packages
Ign:51 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main Translation-en
Ign:52 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main Translation-en_US
Ign:53 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main all DEP-11 Metadata
Ign:54 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main amd64 DEP-11 Metadata
Ign:55 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main DEP-11 64x64 Icons
Ign:56 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted amd64 Packages
Ign:57 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted all Packages
Ign:58 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted i386 Packages
Ign:59 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted Translation-en
Ign:60 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted Translation-en_US
Ign:61 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted all DEP-11 Metadata
Ign:62 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted amd64 DEP-11 Metadata
Ign:63 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted DEP-11 64x64 Icons
Ign:64 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe all Packages
Ign:65 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe i386 Packages
Ign:66 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe amd64 Packages
Ign:67 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe Translation-en
Ign:68 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe Translation-en_US
Ign:69 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe amd64 DEP-11 Metadata
Ign:70 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe all DEP-11 Metadata
Ign:71 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe DEP-11 64x64 Icons
Ign:72 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse amd64 Packages
Ign:73 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse all Packages
Ign:74 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse i386 Packages
Ign:75 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse Translation-en
Ign:76 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse Translation-en_US
Ign:77 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse all DEP-11 Metadata
Ign:78 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse amd64 DEP-11 Metadata
Ign:79 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse DEP-11 64x64 Icons
Ign:80 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main all Packages
Ign:81 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main i386 Packages
Ign:82 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main amd64 Packages
Ign:83 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main Translation-en
Ign:84 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main Translation-en_US
Ign:85 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main amd64 DEP-11 Metadata
Ign:86 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main all DEP-11 Metadata
Ign:87 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main DEP-11 64x64 Icons
Ign:88 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted i386 Packages
Ign:89 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted all Packages
Ign:90 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted amd64 Packages
Ign:91 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted Translation-en
Ign:92 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted Translation-en_US
Ign:93 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted amd64 DEP-11 Metadata
Ign:94 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted all DEP-11 Metadata
Ign:95 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted DEP-11 64x64 Icons
Ign:96 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe all Packages
Ign:97 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe amd64 Packages
Ign:98 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe i386 Packages
Ign:99 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe Translation-en
Ign:100 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe Translation-en_US
Ign:101 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe all DEP-11 Metadata
Ign:102 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe amd64 DEP-11 Metadata
Ign:103 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe DEP-11 64x64 Icons
Ign:104 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse i386 Packages
Ign:105 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse amd64 Packages
Ign:106 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse all Packages
Ign:107 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse Translation-en_US
Ign:108 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse Translation-en
Ign:109 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse amd64 DEP-11 Metadata
Ign:110 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse all DEP-11 Metadata
Ign:111 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse DEP-11 64x64 Icons
Ign:16 http://old-releases.ubuntu.com/ubuntu CODENAME/main amd64 Packages
Ign:17 http://old-releases.ubuntu.com/ubuntu CODENAME/main all Packages
Ign:18 http://old-releases.ubuntu.com/ubuntu CODENAME/main i386 Packages
Ign:19 http://old-releases.ubuntu.com/ubuntu CODENAME/main Translation-en
Ign:20 http://old-releases.ubuntu.com/ubuntu CODENAME/main Translation-en_US
Ign:21 http://old-releases.ubuntu.com/ubuntu CODENAME/main all DEP-11 Metadata
Ign:22 http://old-releases.ubuntu.com/ubuntu CODENAME/main amd64 DEP-11 Metadata
Ign:23 http://old-releases.ubuntu.com/ubuntu CODENAME/main DEP-11 64x64 Icons
Ign:24 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted amd64 Packages
Ign:25 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted i386 Packages
Ign:26 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted all Packages
Ign:27 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted Translation-en
Ign:28 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted Translation-en_US
Ign:29 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted all DEP-11 Metadata
Ign:30 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted amd64 DEP-11 Metadata
Ign:31 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted DEP-11 64x64 Icons
Ign:32 http://old-releases.ubuntu.com/ubuntu CODENAME/universe amd64 Packages
Ign:33 http://old-releases.ubuntu.com/ubuntu CODENAME/universe i386 Packages
Ign:34 http://old-releases.ubuntu.com/ubuntu CODENAME/universe all Packages
Ign:35 http://old-releases.ubuntu.com/ubuntu CODENAME/universe Translation-en
Ign:36 http://old-releases.ubuntu.com/ubuntu CODENAME/universe Translation-en_US
Ign:37 http://old-releases.ubuntu.com/ubuntu CODENAME/universe amd64 DEP-11 Metadata
Ign:38 http://old-releases.ubuntu.com/ubuntu CODENAME/universe all DEP-11 Metadata
Ign:39 http://old-releases.ubuntu.com/ubuntu CODENAME/universe DEP-11 64x64 Icons
Ign:40 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse i386 Packages
Ign:41 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse amd64 Packages
Ign:42 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse all Packages
Ign:43 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse Translation-en_US
Ign:44 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse Translation-en
Ign:45 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse all DEP-11 Metadata
Ign:46 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse amd64 DEP-11 Metadata
Ign:47 http://old-releases.ubuntu.com/ubuntu CODENAME/multiverse DEP-11 64x64 Icons
Ign:48 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main amd64 Packages
Ign:49 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main all Packages
Ign:50 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main i386 Packages
Ign:51 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main Translation-en
Ign:52 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main Translation-en_US
Ign:53 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main all DEP-11 Metadata
Ign:54 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main amd64 DEP-11 Metadata
Ign:55 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main DEP-11 64x64 Icons
Ign:56 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted amd64 Packages
Ign:57 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted all Packages
Ign:58 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted i386 Packages
Ign:59 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted Translation-en
Ign:60 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted Translation-en_US
Ign:61 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted all DEP-11 Metadata
Ign:62 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted amd64 DEP-11 Metadata
Ign:63 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted DEP-11 64x64 Icons
Ign:64 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe all Packages
Ign:65 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe i386 Packages
Ign:66 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe amd64 Packages
Ign:67 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe Translation-en
Ign:68 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe Translation-en_US
Ign:69 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe amd64 DEP-11 Metadata
Ign:70 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe all DEP-11 Metadata
Ign:71 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/universe DEP-11 64x64 Icons
Ign:72 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse amd64 Packages
Ign:73 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse all Packages
Ign:74 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse i386 Packages
Ign:75 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse Translation-en
Ign:76 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse Translation-en_US
Ign:77 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse all DEP-11 Metadata
Ign:78 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse amd64 DEP-11 Metadata
Ign:79 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/multiverse DEP-11 64x64 Icons
Ign:80 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main all Packages
Ign:81 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main i386 Packages
Ign:82 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main amd64 Packages
Ign:83 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main Translation-en
Ign:84 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main Translation-en_US
Ign:85 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main amd64 DEP-11 Metadata
Ign:86 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main all DEP-11 Metadata
Ign:87 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main DEP-11 64x64 Icons
Ign:88 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted i386 Packages
Ign:89 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted all Packages
Ign:90 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted amd64 Packages
Ign:91 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted Translation-en
Ign:92 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted Translation-en_US
Ign:93 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted amd64 DEP-11 Metadata
Ign:94 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted all DEP-11 Metadata
Ign:95 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted DEP-11 64x64 Icons
Ign:96 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe all Packages
Ign:97 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe amd64 Packages
Ign:98 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe i386 Packages
Ign:99 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe Translation-en
Ign:100 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe Translation-en_US
Ign:101 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe all DEP-11 Metadata
Ign:102 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe amd64 DEP-11 Metadata
Ign:103 http://old-releases.ubuntu.com/ubuntu CODENAME-security/universe DEP-11 64x64 Icons
Ign:104 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse i386 Packages
Ign:105 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse amd64 Packages
Ign:106 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse all Packages
Ign:107 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse Translation-en_US
Ign:108 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse Translation-en
Ign:109 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse amd64 DEP-11 Metadata
Ign:110 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse all DEP-11 Metadata
Ign:111 http://old-releases.ubuntu.com/ubuntu CODENAME-security/multiverse DEP-11 64x64 Icons
Err:16 http://old-releases.ubuntu.com/ubuntu CODENAME/main amd64 Packages
  404  Not Found
Ign:17 http://old-releases.ubuntu.com/ubuntu CODENAME/main all Packages
Ign:18 http://old-releases.ubuntu.com/ubuntu CODENAME/main i386 Packages
Ign:19 http://old-releases.ubuntu.com/ubuntu CODENAME/main Translation-en
Ign:20 http://old-releases.ubuntu.com/ubuntu CODENAME/main Translation-en_US
Ign:21 http://old-releases.ubuntu.com/ubuntu CODENAME/main all DEP-11 Metadata
Ign:22 http://old-releases.ubuntu.com/ubuntu CODENAME/main amd64 DEP-11 Metadata
Ign:23 http://old-releases.ubuntu.com/ubuntu CODENAME/main DEP-11 64x64 Icons
Ign:24 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted amd64 Packages
Ign:25 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted i386 Packages
Ign:26 http://old-releases.ubuntu.com/ubuntu CODENAME/restricted all Packages
Err:48 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main amd64 Packages
  404  Not Found
Ign:49 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main all Packages
Ign:50 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main i386 Packages
Ign:51 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main Translation-en
Ign:52 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main Translation-en_US
Ign:53 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main all DEP-11 Metadata
Ign:54 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main amd64 DEP-11 Metadata
Ign:55 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/main DEP-11 64x64 Icons
Ign:56 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted amd64 Packages
Ign:57 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted all Packages
Ign:58 http://old-releases.ubuntu.com/ubuntu CODENAME-updates/restricted i386 Packages
Ign:80 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main all Packages
Err:81 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main i386 Packages
  404  Not Found
Ign:82 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main amd64 Packages
Ign:83 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main Translation-en
Ign:84 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main Translation-en_US
Ign:85 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main amd64 DEP-11 Metadata
Ign:86 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main all DEP-11 Metadata
Ign:87 http://old-releases.ubuntu.com/ubuntu CODENAME-security/main DEP-11 64x64 Icons
Ign:88 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted i386 Packages
Ign:89 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted all Packages
Ign:90 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted amd64 Packages
Ign:91 http://old-releases.ubuntu.com/ubuntu CODENAME-security/restricted Translation-en
Fetched 27.9 kB in 2min 17s (203 B/s)
Reading package lists... Done
W: The repository 'http://old-releases.ubuntu.com/ubuntu CODENAME Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://old-releases.ubuntu.com/ubuntu CODENAME-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://old-releases.ubuntu.com/ubuntu CODENAME-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://packagecloud.io/github/git-lfs/ubuntu zesty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B05F25D762E3157
W: Failed to fetch https://packagecloud.io/github/git-lfs/ubuntu/dists/zesty/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B05F25D762E3157
E: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/CODENAME/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/CODENAME-updates/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/CODENAME-security/main/binary-i386/Packages  404  Not Found
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by wildmanne39 on 2019-04-25
I recommend backing up important files and doing a clean install of 18.04 or later version of Ubuntu that is still supported and receives updates which 17.10 does not. it will take a lot longer and cause a lot more issues trying to do an upgrade from one EOL version to another and your system will still be at risk since it will not receive security updates.

---

### Post by kodingkoning on 2019-04-26
Good to know! Thanks. I will work on doing that instead then.

---

