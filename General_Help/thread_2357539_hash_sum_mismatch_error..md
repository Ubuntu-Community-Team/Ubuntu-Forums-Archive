---
title: "hash sum mismatch error."
date: 2017-04-03
forum: General Help
---

### Post by again? on 2017-04-03
I have used the same update mirror ([http://ftp.iinet.net.au](http://ftp.iinet.net.au)) for a number of years 
but lately get frequent hash sum mismatch errors when updating.
I can fix by choosing another mirror and then returning to [iinet]("http://ftp.iinet.net.au") in a day or so where updates work again.
I prefer using the iinet mirror because it's my ISP and the traffic is unmetered

I don't know how mirroring works but wondered if the fault may be with iinet and if it's worth contacting them?
I've had these sort of errors about 4 times in the last few weeks.
```
Xen2:~$ sudo apt update
Hit:1 https://downloads.plex.tv/repo/deb public InRelease                                                                       
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                                                                    
Hit:3 http://ftp.iinet.net.au/pub/ubuntu xenial InRelease                                                                       
Get:4 http://ftp.iinet.net.au/pub/ubuntu xenial-updates InRelease [102 kB]                                                      
Hit:7 http://archive.canonical.com/ubuntu xenial InRelease                                                                      
Get:5 http://ftp.iinet.net.au/pub/ubuntu xenial-backports InRelease [102 kB]                                                    
Get:6 http://ftp.iinet.net.au/pub/ubuntu xenial-security InRelease [102 kB]                                                     
Hit:8 http://dl.google.com/linux/chrome/deb stable Release                                                                      
Get:9 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/main amd64 Packages [501 kB]                                            
Get:10 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/main i386 Packages [491 kB]                                            
Ign:11 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/main amd64 DEP-11 Metadata                                             
Ign:12 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/main DEP-11 64x64 Icons                                                
Get:13 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/universe amd64 Packages [451 kB]                                       
Hit:14 http://deb.opera.com/opera-stable stable InRelease                                                                       
Get:15 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/universe i386 Packages [437 kB]                                        
Ign:16 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/universe amd64 DEP-11 Metadata                                         
Ign:17 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/universe DEP-11 64x64 Icons                                            
Ign:18 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata                                       
Ign:20 http://ftp.iinet.net.au/pub/ubuntu xenial-backports/main amd64 DEP-11 Metadata                                           
Get:11 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/main amd64 DEP-11 Metadata [288 kB]                                    
Err:11 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/main amd64 DEP-11 Metadata                                             
  Hash Sum mismatch
Get:16 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [160 kB] 
Err:16 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/universe amd64 DEP-11 Metadata          
  
Get:17 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/universe DEP-11 64x64 Icons [188 kB]    
Hit:21 https://deb.opera.com/opera-beta stable InRelease                                 
Err:17 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/universe DEP-11 64x64 Icons                          
  
Get:18 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]           
Err:18 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata                         
  
Get:20 http://ftp.iinet.net.au/pub/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,324 B]                   
Err:20 http://ftp.iinet.net.au/pub/ubuntu xenial-backports/main amd64 DEP-11 Metadata                             
  Hash Sum mismatch
Ign:22 http://ftp.iinet.net.au/pub/ubuntu xenial-security/main amd64 DEP-11 Metadata                              
Ign:23 http://ftp.iinet.net.au/pub/ubuntu xenial-security/main DEP-11 64x64 Icons
Ign:24 http://ftp.iinet.net.au/pub/ubuntu xenial-security/universe amd64 DEP-11 Metadata
Ign:25 http://ftp.iinet.net.au/pub/ubuntu xenial-security/universe DEP-11 64x64 Icons
Get:22 http://ftp.iinet.net.au/pub/ubuntu xenial-security/main amd64 DEP-11 Metadata [54.2 kB]
Err:22 http://ftp.iinet.net.au/pub/ubuntu xenial-security/main amd64 DEP-11 Metadata                               
  Hash Sum mismatch
Get:23 http://ftp.iinet.net.au/pub/ubuntu xenial-security/main DEP-11 64x64 Icons [42.4 kB]
Ign:23 http://ftp.iinet.net.au/pub/ubuntu xenial-security/main DEP-11 64x64 Icons   
Get:24 http://ftp.iinet.net.au/pub/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32.2 kB]
Err:24 http://ftp.iinet.net.au/pub/ubuntu xenial-security/universe amd64 DEP-11 Metadata
  
Get:25 http://ftp.iinet.net.au/pub/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Err:25 http://ftp.iinet.net.au/pub/ubuntu xenial-security/universe DEP-11 64x64 Icons
  
Hit:26 http://ppa.launchpad.net/audio-recorder/ppa/ubuntu xenial InRelease      
Ign:27 http://repo.vivaldi.com/snapshot/deb stable InRelease              
Ign:28 https://mega.nz/linux/MEGAsync/xUbuntu_16.04 ./ InRelease
Hit:29 http://ppa.launchpad.net/budgie-remix/ppa/ubuntu xenial InRelease
Hit:30 http://ppa.launchpad.net/dhor/myway/ubuntu xenial InRelease        
Ign:31 http://repo.vivaldi.com/stable/deb stable InRelease                
Hit:32 http://repo.vivaldi.com/snapshot/deb stable Release
Hit:33 http://repo.vivaldi.com/stable/deb stable Release
Get:36 https://mega.nz/linux/MEGAsync/xUbuntu_16.04 ./ Release [988 B]
Hit:38 http://ppa.launchpad.net/peek-developers/stable/ubuntu xenial InRelease                                                                                   
Hit:39 http://ppa.launchpad.net/ricotz/docky/ubuntu xenial InRelease                                                                                             
Hit:40 http://ppa.launchpad.net/webupd8team/nemo3/ubuntu xenial InRelease                                                                                        
Fetched 1,072 kB in 7s (145 kB/s)                                                                                                                                
Reading package lists... Done
E: Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/xenial-updates/main/dep11/Components-amd64.yml.xz  Hash Sum mismatch
E: Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/xenial-updates/main/dep11/icons-64x64.tar.gz  404  Not Found
E: Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/xenial-updates/universe/dep11/Components-amd64.yml.xz  
E: Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/xenial-updates/universe/dep11/icons-64x64.tar.gz  
E: Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/xenial-updates/multiverse/dep11/Components-amd64.yml.xz  
E: Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/xenial-backports/main/dep11/Components-amd64.yml.xz  Hash Sum mismatch
E: Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/xenial-security/main/dep11/Components-amd64.yml.xz  Hash Sum mismatch
E: Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/xenial-security/universe/dep11/Components-amd64.yml.xz  
E: Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/xenial-security/universe/dep11/icons-64x64.tar.gz  
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

No error using a different mirror.
```
Xen2:~$ sudo apt update
Get:1 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial InRelease [247 kB]                                                
Hit:2 https://downloads.plex.tv/repo/deb public InRelease                                                                       
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                                                                    
Hit:4 http://ppa.launchpad.net/audio-recorder/ppa/ubuntu xenial InRelease                                                       
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                                                                      
Get:6 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates InRelease [102 kB]                                        
Hit:7 http://deb.opera.com/opera-stable stable InRelease                                                                        
Hit:8 http://dl.google.com/linux/chrome/deb stable Release                                                                      
Hit:9 http://ppa.launchpad.net/budgie-remix/ppa/ubuntu xenial InRelease                                                         
Get:11 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports InRelease [102 kB]                                     
Hit:12 http://ppa.launchpad.net/dhor/myway/ubuntu xenial InRelease                                       
Get:13 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security InRelease [102 kB]                 
Ign:14 http://repo.vivaldi.com/snapshot/deb stable InRelease                                              
Get:15 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/main amd64 Packages [1,201 kB]
Hit:16 https://deb.opera.com/opera-beta stable InRelease                                                   
Ign:17 http://repo.vivaldi.com/stable/deb stable InRelease                                                  
Hit:18 http://repo.vivaldi.com/snapshot/deb stable Release                      
Hit:20 http://repo.vivaldi.com/stable/deb stable Release                             
Ign:22 https://mega.nz/linux/MEGAsync/xUbuntu_16.04 ./ InRelease                     
Hit:23 http://ppa.launchpad.net/peek-developers/stable/ubuntu xenial InRelease
Hit:24 http://ppa.launchpad.net/ricotz/docky/ubuntu xenial InRelease                  
Get:25 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/main i386 Packages [1,196 kB]
Hit:26 http://ppa.launchpad.net/webupd8team/nemo3/ubuntu xenial InRelease         
Get:27 https://mega.nz/linux/MEGAsync/xUbuntu_16.04 ./ Release [988 B]                  
Get:29 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/main Translation-en_AU [420 kB]                                  
Get:30 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/main Translation-en [568 kB]                                     
Get:31 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/main amd64 DEP-11 Metadata [733 kB]                              
Get:32 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/main DEP-11 64x64 Icons [409 kB]                                 
Get:33 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/restricted amd64 Packages [8,344 B]                              
Get:34 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/restricted i386 Packages [8,684 B]                               
Get:35 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/restricted Translation-en_AU [2,012 B]                           
Get:36 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/restricted Translation-en [2,908 B]                              
Get:37 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/restricted amd64 DEP-11 Metadata [186 B]                         
Get:38 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/universe amd64 Packages [7,532 kB]                               
Get:39 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/universe i386 Packages [7,512 kB]                                
Get:40 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/universe Translation-en_AU [3,039 kB]                            
Get:41 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/universe Translation-en [4,354 kB]                               
Get:42 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/universe amd64 DEP-11 Metadata [3,410 kB]                        
Get:43 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/universe DEP-11 64x64 Icons [7,448 kB]                           
Get:44 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/multiverse amd64 Packages [144 kB]                               
Get:45 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/multiverse i386 Packages [140 kB]                                
Get:46 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/multiverse Translation-en_AU [67.7 kB]                           
Get:47 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/multiverse Translation-en [106 kB]                               
Get:48 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/multiverse amd64 DEP-11 Metadata [63.8 kB]                       
Get:49 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial/multiverse DEP-11 64x64 Icons [230 kB]                           
Get:50 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/main amd64 Packages [501 kB]                             
Get:51 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/main i386 Packages [491 kB]                              
Get:52 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/main Translation-en [202 kB]                             
Get:53 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/main amd64 DEP-11 Metadata [287 kB]                      
Get:54 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/main DEP-11 64x64 Icons [191 kB]                         
Get:55 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/restricted amd64 Packages [7,776 B]                      
Get:56 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/restricted i386 Packages [7,792 B]                       
Get:57 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/restricted Translation-en [2,548 B]                      
Get:58 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata [157 B]                 
Get:59 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/universe amd64 Packages [451 kB]                         
Get:60 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/universe i386 Packages [437 kB]                          
Get:61 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/universe Translation-en [172 kB]                         
Get:62 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [160 kB]                  
Get:63 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/universe DEP-11 64x64 Icons [188 kB]                     
Get:64 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/multiverse amd64 Packages [8,920 B]                      
Get:65 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/multiverse i386 Packages [7,720 B]                       
Get:66 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/multiverse Translation-en [4,136 B]                      
Get:67 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]               
Get:68 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons [7,765 B]                  
Get:69 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/main amd64 Packages [4,672 B]                          
Get:70 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/main i386 Packages [4,660 B]                           
Get:71 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/main Translation-en [3,200 B]                          
Get:72 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,324 B]                   
Get:73 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/main DEP-11 64x64 Icons [29 B]                         
Get:74 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/restricted amd64 DEP-11 Metadata [194 B]               
Get:75 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/universe amd64 Packages [2,512 B]                      
Get:76 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/universe i386 Packages [2,508 B]                       
Get:77 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/universe Translation-en [1,216 B]                      
Get:78 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [212 B]                 
Get:79 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/universe DEP-11 64x64 Icons [29 B]                     
Get:80 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [216 B]               
Get:81 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-backports/multiverse DEP-11 64x64 Icons [29 B]                   
Get:82 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/main amd64 Packages [235 kB]                            
Get:83 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/main i386 Packages [227 kB]                             
Get:84 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/main Translation-en [99.7 kB]                           
Get:85 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/main amd64 DEP-11 Metadata [54.2 kB]                    
Get:86 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/main DEP-11 64x64 Icons [46.9 kB]                       
Get:87 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/restricted amd64 Packages [7,428 B]                     
Get:88 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/restricted i386 Packages [7,432 B]                      
Get:89 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/restricted Translation-en [2,428 B]                     
Get:90 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/restricted amd64 DEP-11 Metadata [200 B]                
Get:91 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/universe amd64 Packages [106 kB]                        
Get:92 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/universe i386 Packages [94.2 kB]                        
Get:93 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/universe Translation-en [54.7 kB]                       
Get:94 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32.2 kB]                
Get:95 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]                   
Get:96 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/multiverse amd64 Packages [2,748 B]                     
Get:97 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/multiverse i386 Packages [2,912 B]                      
Get:98 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/multiverse Translation-en [1,232 B]                     
Get:99 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [212 B]                
Get:100 http://mirror.internode.on.net/pub/ubuntu/ubuntu xenial-security/multiverse DEP-11 64x64 Icons [29 B]                   
Fetched 43.3 MB in 1min 18s (554 kB/s)                                                                                          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.



```

---

