---
title: "Updates stopped working whatever method I use - something in /var/lib/apt/lists (??)"
date: 2013-03-30
forum: General Help
---

### Post by blackbird34 on 2013-03-30
Hi all
 
I can't update my system at all now... Software Centre fails silently after being open a couple of seconds, Synaptic throws an error message with only a "close" button which quits the program, and I can't apt-get update / apt-get upgrade either.

Error from Synaptic:
[B]> 
E: Encountered a section with no Package: header[/B]
**E: Problem with MergeList /var/lib/apt/lists/fr.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en**
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


Error from apt-get:
```
 sudo apt-get update && sudo apt-get upgrade
[sudo] password for nad: 
Hit http://archive.canonical.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://fr.archive.ubuntu.com precise Release.gpg                           
Get:2 http://fr.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://fr.archive.ubuntu.com precise-backports Release.gpg                 
Get:3 http://fr.archive.ubuntu.com precise-proposed Release.gpg [198 B]        
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://fr.archive.ubuntu.com precise Release                               
Hit http://archive.ubuntu.com precise Release.gpg                              
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://www.remastersys.com lucid/ Release.gpg                              
Get:5 http://fr.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://archive.ubuntu.com precise Release                                  
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://www.remastersys.com lucid/ Release                                  
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://dl.google.com stable Release.gpg                                    
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Get:6 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Ign http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:7 http://security.ubuntu.com precise-security/main Sources [64.7 kB]       
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://www.remastersys.com lucid/ Packages/DiffIndex                       
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://fr.archive.ubuntu.com precise-backports Release                     
Get:8 http://fr.archive.ubuntu.com precise-proposed Release [49.6 kB]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,380 B] 
Get:10 http://security.ubuntu.com precise-security/universe Sources [22.6 kB]  
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://fr.archive.ubuntu.com precise/restricted Sources                    
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://fr.archive.ubuntu.com precise/main Sources                          
Get:11 http://security.ubuntu.com precise-security/main amd64 Packages [233 kB]
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net precise/main amd64 Packages/DiffIndex             
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                    
Hit http://fr.archive.ubuntu.com precise/multiverse Sources                    
Ign http://ppa.launchpad.net precise/main amd64 Packages/DiffIndex             
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex              
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net precise/main amd64 Packages/DiffIndex             
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex              
Hit http://fr.archive.ubuntu.com precise/universe Sources                      
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://fr.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://fr.archive.ubuntu.com precise/restricted amd64 Packages             
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://fr.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://fr.archive.ubuntu.com precise/multiverse amd64 Packages             
Ign http://dl.google.com stable/main Translation-en                            
Hit http://fr.archive.ubuntu.com precise/main i386 Packages                    
Hit http://fr.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://fr.archive.ubuntu.com precise/universe i386 Packages                
Get:12 http://ppa.launchpad.net precise/main Sources [603 B]                   
Get:13 http://ppa.launchpad.net precise/main amd64 Packages [456 B]            
Get:14 http://ppa.launchpad.net precise/main i386 Packages [456 B]             
Get:15 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:16 http://security.ubuntu.com precise-security/universe amd64 Packages [68.6 kB]
Hit http://fr.archive.ubuntu.com precise/multiverse i386 Packages              
Get:17 http://ppa.launchpad.net precise/main Sources [741 B]                   
Get:18 http://ppa.launchpad.net precise/main amd64 Packages [1,058 B]          
Get:19 http://ppa.launchpad.net precise/main i386 Packages [1,058 B]           
Get:20 http://ppa.launchpad.net precise/main Sources [16.9 kB]                 
Hit http://fr.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://www.remastersys.com lucid/ Packages                                 
Get:21 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,186 B]
Get:22 http://security.ubuntu.com precise-security/main i386 Packages [243 kB] 
Hit http://fr.archive.ubuntu.com precise/multiverse TranslationIndex           
Get:23 http://ppa.launchpad.net precise/main amd64 Packages [18.0 kB]          
Ign http://www.remastersys.com lucid/ Translation-en_US                        
Hit http://fr.archive.ubuntu.com precise/restricted TranslationIndex           
Ign http://www.remastersys.com lucid/ Translation-en                           
Get:24 http://ppa.launchpad.net precise/main i386 Packages [18.1 kB]           
Hit http://fr.archive.ubuntu.com precise/universe TranslationIndex             
Get:25 http://fr.archive.ubuntu.com precise-updates/restricted Sources [5,494 B]
Get:26 http://fr.archive.ubuntu.com precise-updates/main Sources [373 kB]      
Get:27 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:28 http://security.ubuntu.com precise-security/universe i386 Packages [70.5 kB]
Get:29 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en     
Hit http://security.ubuntu.com precise-security/restricted Translation-en     
Hit http://security.ubuntu.com precise-security/universe Translation-en       
Get:30 http://fr.archive.ubuntu.com precise-updates/multiverse Sources [4,746 B]
Get:31 http://fr.archive.ubuntu.com precise-updates/universe Sources [82.7 kB] 
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:32 http://fr.archive.ubuntu.com precise-updates/main amd64 Packages [592 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:33 http://fr.archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]
Get:34 http://fr.archive.ubuntu.com precise-updates/universe amd64 Packages [190 kB]
Get:35 http://fr.archive.ubuntu.com precise-updates/multiverse amd64 Packages [9,418 B]
Get:36 http://fr.archive.ubuntu.com precise-updates/main i386 Packages [603 kB]
Get:37 http://fr.archive.ubuntu.com precise-updates/restricted i386 Packages [10.1 kB]
Get:38 http://fr.archive.ubuntu.com precise-updates/universe i386 Packages [192 kB]
Get:39 http://fr.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]
Hit http://fr.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://fr.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://fr.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://fr.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://fr.archive.ubuntu.com precise-backports/main Sources                
Hit http://fr.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://fr.archive.ubuntu.com precise-backports/universe Sources            
Hit http://fr.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://fr.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://fr.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://fr.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://fr.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://fr.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://fr.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://fr.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://fr.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://fr.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://fr.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://fr.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://fr.archive.ubuntu.com precise-backports/universe TranslationIndex   
Get:40 http://fr.archive.ubuntu.com precise-proposed/restricted Sources [14 B] 
Get:41 http://fr.archive.ubuntu.com precise-proposed/main Sources [27.1 kB]    
Get:42 http://fr.archive.ubuntu.com precise-proposed/multiverse Sources [2,982 B]
Get:43 http://fr.archive.ubuntu.com precise-proposed/universe Sources [4,958 B]
Get:44 http://fr.archive.ubuntu.com precise-proposed/restricted amd64 Packages [14 B]
Get:45 http://fr.archive.ubuntu.com precise-proposed/main amd64 Packages [54.1 kB]
Get:46 http://fr.archive.ubuntu.com precise-proposed/multiverse amd64 Packages [5,092 B]
Get:47 http://fr.archive.ubuntu.com precise-proposed/universe amd64 Packages [11.2 kB]
Get:48 http://fr.archive.ubuntu.com precise-proposed/restricted i386 Packages [14 B]
Get:49 http://fr.archive.ubuntu.com precise-proposed/main i386 Packages [57.4 kB]
Get:50 http://fr.archive.ubuntu.com precise-proposed/multiverse i386 Packages [4,312 B]
Get:51 http://fr.archive.ubuntu.com precise-proposed/universe i386 Packages [12.1 kB]
Hit http://fr.archive.ubuntu.com precise-proposed/main TranslationIndex        
Hit http://fr.archive.ubuntu.com precise-proposed/multiverse TranslationIndex  
Hit http://fr.archive.ubuntu.com precise-proposed/restricted TranslationIndex  
Hit http://fr.archive.ubuntu.com precise-proposed/universe TranslationIndex    
Hit http://fr.archive.ubuntu.com precise/main Translation-en                   
Hit http://fr.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://fr.archive.ubuntu.com precise/restricted Translation-en             
Hit http://fr.archive.ubuntu.com precise/universe Translation-en               
Hit http://fr.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://fr.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://fr.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://fr.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://fr.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://fr.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://fr.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://fr.archive.ubuntu.com precise-backports/universe Translation-en     
Hit http://fr.archive.ubuntu.com precise-proposed/main Translation-en          
Hit http://fr.archive.ubuntu.com precise-proposed/multiverse Translation-en    
Hit http://fr.archive.ubuntu.com precise-proposed/restricted Translation-en    
Hit http://fr.archive.ubuntu.com precise-proposed/universe Translation-en      
Fetched 3,188 kB in 29s (107 kB/s)                                             
Reading package lists... Error!
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 799A5FD5D1C5997F Launchpad Pynagram
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG C2518248EEA14886 Launchpad VLC
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG EB563F93142986CE Launchpad PPA for Xubuntu Developers
**E: Encountered a section with no Package: header**
**E: Problem with MergeList /var/lib/apt/lists/fr.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en**
E: The package lists or status file could not be parsed or opened.
nad@Macondo:~$ 


```
I also tried removing something to see what errors it would throw up:
```
sudo apt-get purge jupiter
[sudo] password for nad: 
Reading package lists... Error!
**E: Encountered a section with no Package: header**
**E: Problem with MergeList /var/lib/apt/lists/fr.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en**
E: The package lists or status file could not be parsed or opened.

```

Can anyone help me and tell me what on earth the incriminating file (in bold) is, if it's the only one causing the problem, and what to do to sort the problem out? Can I just delete the file and let it re-generate itself or does APT not work like that? 
Thanks in advance!

---

### Post by ibjsb4 on 2013-03-30
In terminal

```
sudo rm -r /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
```

---

### Post by blackbird34 on 2013-03-30
Thanks very much, it worked. 
I'm apt-get upgrading now... I'll mark it as solved if everything is fine.

EDIT: this issue was solved, can't find the place to mark it as solved, it must have moved. Thanks very much!

I do have another problem with a kernel update in [this thread]("http://ubuntuforums.org/showthread.php?t=2131007&p=12582031#post12582031").

---

