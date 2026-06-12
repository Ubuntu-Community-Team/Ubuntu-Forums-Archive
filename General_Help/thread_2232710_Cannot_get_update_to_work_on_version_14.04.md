---
title: "Cannot get update to work on version 14.04"
date: 2014-07-03
forum: General Help
---

### Post by SUPERFITTER on 2014-07-03
Cannot get update to work on version 14.04.  I ran this in terminal.

```
dennis@Dennis1:~$ sudo apt-get update
[sudo] password for dennis: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg [933 B]        
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Ign [http://repository.spotify.com](http://repository.spotify.com) trusty InRelease                             
Hit [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [58.5 kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [58.5 kB]             
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release [58.6 kB]          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Ign [http://repository.spotify.com](http://repository.spotify.com) trusty Release.gpg                           
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [30.6 kB]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]     
Ign [http://repository.spotify.com](http://repository.spotify.com) trusty Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [6,808 B]    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [688 B]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [105 kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [80.4 kB]      
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [14 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US              
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [35.9 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]   
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [60.1 kB]  
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [1,157 B]
Get:18 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:19 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:20 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [2,681 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [214 kB]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [102 kB]  
Get:24 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:25 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:26 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:27 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:28 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:29 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [14 B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [154 kB]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [35.9 kB]
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,392 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [7,397 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [210 kB] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en            
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [154 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [7,569 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [74.5 kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [14 B]       
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [14 B] 
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [7,265 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [768 B]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages [14 B]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [14 B]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages [8,141 B]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [619 B]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [14 B]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [14 B]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [8,157 B]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [619 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en [5,273 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US   
Fetched 1,543 kB in 7s (196 kB/s)                                              
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repository.spotify.com_dists_trusty_non-free_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
dennis@Dennis1:~$
```

---

### Post by ubudog on 2014-07-03
Resetting the control files will probably help.

Check out [this solution]("http://ubuntuforums.org/showthread.php?t=2230860&p=13055620#post13055620").

---

### Post by SUPERFITTER on 2014-07-03
> **ubudog said:**
> Resetting the control files will probably help.

Check out [this solution]("http://ubuntuforums.org/showthread.php?t=2230860&p=13055620#post13055620").

I tried this solution and got this.

```
dennis@Dennis1:~$ sudo rm -fr /var/lib/apt/lists
[sudo] password for dennis: 
dennis@Dennis1:~$ sudo mkdir -pv /var/lib/apt/lists/partial
mkdir: created directory &#8216;/var/lib/apt/lists&#8217;
mkdir: created directory &#8216;/var/lib/apt/lists/partial&#8217;
dennis@Dennis1:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [58.5 kB]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg [933 B]                  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Get:6 [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg [933 B]                  
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                      
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg [933 B]        
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release [58.5 kB]                    
Ign [http://repository.spotify.com](http://repository.spotify.com) trusty InRelease                             
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [30.6 kB]       
Get:11 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release [11.9 kB]                       
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [14.0 kB]                       
Get:13 [http://archive.canonical.com](http://archive.canonical.com) trusty Release [8,257 B]                   
Get:14 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease [2,980 B]                
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]    
Get:16 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources [14 B]                     
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [6,808 B]   
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [58.5 kB]           
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [688 B]   
Get:20 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages [14 B]              
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [12.4 kB]           
Get:22 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages [4,917 B]    
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [105 kB] 
Ign [http://repository.spotify.com](http://repository.spotify.com) trusty Release.gpg                           
Get:24 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages [14 B]               
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release [58.6 kB]         
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [12.4 kB]            
Get:27 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages [944 B]    
Get:28 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages [5,818 B]     
Get:29 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages [943 B]     
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources [1,064 kB]             
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [14 B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [35.9 kB]
Ign [http://repository.spotify.com](http://repository.spotify.com) trusty Release                               
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [1,157 B]
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [102 kB]  
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [35.9 kB]
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,392 B]
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [49.4 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [587 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [14 B]
Get:41 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:42 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US
Get:43 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:44 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:45 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:46 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:47 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:48 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:49 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:50 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US         
Get:51 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [19.5 kB]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources [5,433 B]        
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources [6,399 kB]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US      
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources [174 kB]         
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages [1,350 kB]      
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages [13.0 kB] 
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages [5,859 kB]  
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages [132 kB]  
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages [1,348 kB]       
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages [13.4 kB]  
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages [5,866 kB]   
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages [134 kB]   
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en [762 kB]        
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en [102 kB]  
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en [3,457 B] 
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en [4,089 kB]  
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [80.4 kB]      
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]   
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [60.1 kB]  
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [2,681 B]
Get:71 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [214 kB]
Get:72 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [14 B]
Get:73 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [154 kB]
Get:74 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [7,397 B]
Get:75 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [210 kB] 
Get:76 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Get:77 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [154 kB]
Get:78 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [7,569 B]
Get:79 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [97.4 kB]
Get:80 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [3,971 B]
Get:81 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en [14 B]
Get:82 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [74.5 kB]
Get:83 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [14 B]       
Get:84 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [14 B] 
Get:85 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [7,265 B]
Get:86 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [768 B]
Get:87 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages [14 B]
Get:88 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [14 B]
Get:89 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages [8,141 B]
Get:90 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [619 B]
Get:91 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [14 B] 
Get:92 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [14 B]
Get:93 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [8,157 B]
Get:94 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [619 B]
Get:95 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en [14 B]
Get:96 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en [307 B]
Get:97 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en [14 B]
Get:98 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en [5,273 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US   
Fetched 29.2 MB in 1min 20s (362 kB/s)                                         
[B]Reading package lists... Error!
W: Duplicate sources.list entry [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free amd64 Packages (/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free i386 Packages (/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-i386_Packages)
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.[/B]
dennis@Dennis1:~$ sudo apt-get upgrade
Reading package lists... Error!
[B]W: Duplicate sources.list entry [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free amd64 Packages (/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free i386 Packages (/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-i386_Packages)
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened[/B].
dennis@Dennis1:~$
```

---

### Post by ubudog on 2014-07-03
Looks like the Spotify repositories are broken, but as a workaround try [this]("http://community.spotify.com/t5/Help-Desktop-Linux-Mac-and/Spotify-0-9-11-for-GNU-Linux/m-p/845061/highlight/true#M91512").

---

### Post by SUPERFITTER on 2014-07-04
> **ubudog said:**
> Looks like the Spotify repositories are broken, but as a workaround try [this]("http://community.spotify.com/t5/Help-Desktop-Linux-Mac-and/Spotify-0-9-11-for-GNU-Linux/m-p/845061/highlight/true#M91512").

Sorry I'm lost on this one, and  I cannot open software updater or Ubuntu software center?

---

### Post by QIII on 2014-07-04
Hello, SUPERFITTER.

Please use code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by Bucky Ball on 2014-07-04
> **SUPERFITTER said:**
> Sorry I'm lost on this one, and  I cannot open software updater or Ubuntu software center?

The Spotify repo does look broken, as mentioned, but the above is another problem altogether. What happens when you try to open Software Updater? What is the message, exactly? You should probably post a new thread for the issue of not being able to open Software Updater or Software Centre if that persists. It will increase your chances of getting help.

If you have Synaptic Package Manager you can get to the settings screen from there. 

Anyway, you can switch the repo off in a terminal. Issue:

```
sudo nano /etc/apt/sources.list
```

Look in there for the offending Spotify repo, place a hash (#) and space at the beginning of that line. Control+x to save, y, then try the update again.

---

### Post by SUPERFITTER on 2014-07-04
[How do I get out of: sudo nano /etc/apt/sources.list]

[Software Updater will not open.]

[Ubuntu software center starts to open then closes]

---

### Post by deadflowr on 2014-07-04
> [How do I get out of: sudo nano /etc/apt/sources.list]
Bucky Ball posted it, but ctrl + x to save and exit. If you changed nothing then it will simply exit.

But I think spotify has it's own repo which would be in the folder, not file, /etc/apt/sources.list.d.
I would think you would look in that folder for a spotify.list file.
From there, you would add a comment, #, to the existing deb lines and then add the the line(copy and paste is best)from the link ubudog provided of the fix to the file.
Then run 
```
sudo apt-get update
```
again to see if the fix worked.

---

### Post by SUPERFITTER on 2014-07-04
```
dennis@Dennis1:~$ sudo apt-get update
[sudo] password for dennis: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                      
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://repository.spotify.com](http://repository.spotify.com) trusty InRelease                             
Hit [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg [933 B]        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [14.0 kB]                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [58.5 kB]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Ign [http://repository.spotify.com](http://repository.spotify.com) trusty Release.gpg                           
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [12.4 kB]            
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release [58.6 kB]          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [12.4 kB]             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Ign [http://repository.spotify.com](http://repository.spotify.com) trusty Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US              
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [80.4 kB]      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [60.1 kB]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [2,681 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [214 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en     
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [14 B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [154 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en     
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [7,397 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [211 kB] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en       
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [154 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [7,569 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [97.4 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [74.5 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [14 B]       
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [14 B] 
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en      
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [7,265 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [768 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages [14 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [14 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages [8,141 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US          
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [619 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US    
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [14 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [14 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [8,157 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US    
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [619 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en 
Err [http://repository.spotify.com](http://repository.spotify.com) trusty/non-free amd64 Packages
  404  Not Found [IP: 205.251.253.127 80]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Err [http://repository.spotify.com](http://repository.spotify.com) trusty/non-free i386 Packages
  404  Not Found [IP: 205.251.253.127 80]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Ign [http://repository.spotify.com](http://repository.spotify.com) trusty/non-free Translation-en_US
Ign [http://repository.spotify.com](http://repository.spotify.com) trusty/non-free Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US   
Fetched 1,246 kB in 7s (172 kB/s)                                              
W: Failed to fetch [http://repository.spotify.com/dists/trusty/non-free/binary-amd64/Packages](http://repository.spotify.com/dists/trusty/non-free/binary-amd64/Packages)  404  Not Found [IP: 205.251.253.127 80]

W: Failed to fetch [http://repository.spotify.com/dists/trusty/non-free/binary-i386/Packages](http://repository.spotify.com/dists/trusty/non-free/binary-i386/Packages)  404  Not Found [IP: 205.251.253.127 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
dennis@Dennis1:~$
```

---

### Post by deadflowr on 2014-07-04
You haven't changed the repo.

For a clearer idea do this
1)open terminal and run
```
sudo nano /etc/apt/sources.list.d/spotify.list
```
then add this line
```
deb http://repository-origin.spotify.com stable non-free
```
and then add a # symbol to every other line that starts with deb.
so it'll look like
```
deb http://repository-origin.spotify.com stable non-free
#deb otherline
#deb another other line
```
then ctrl +x to save and exit.
(select y and hit enter)
then re-run the update command.

**Also, please read post # 6, again.**

---

### Post by SUPERFITTER on 2014-07-04
I get the same as post #10?  The problem is I updated to Ubuntu 14.04 from 12.11 and saved everything that I had on 12.11.  This is a duel boot with Win 7 on one hard drive and Ubuntu on another drive.

---

### Post by deadflowr on 2014-07-04
Saving and updating releases has nothing to do with the spotify error.
The normal spotify repos are having a problem, thus ubudog's post with the link to the fix.
Once you apply the fix, the updater will run as it is suppose to, then other problems will be resolved as well.
Like the software center not opening.

But to further this, please post the output for
```
cat /etc/apt/sources.list.d/spotify.list
```

---

### Post by SUPERFITTER on 2014-07-04
```
dennis@Dennis1:~$ cat /etc/apt/sources.list.d/spotify.list
cat: /etc/apt/sources.list.d/spotify.list: No such file or directory
dennis@Dennis1:~$ 

```

---

### Post by deadflowr on 2014-07-04
Hmm,
then what about
```
ls /etc/apt/sources.list.d
```
post the output please.
Or  is the spotify entry, for some reason, inside the main sources.list?
```
cat /etc/apt/sources.list
```
Might as well post that output as well.

**Edit:Adding:** Also, I'm not sure if this has been put forth yet, but can you open the program named "Software and Updates", without it crashing?
If so open that and go to Other Software and uncheck any entry for spotify.
Then run update command again.

---

### Post by SUPERFITTER on 2014-07-04
This fixed the problem:```

**Edit:Adding:** Also, I'm not sure if this has been put forth yet,  but can you open the program named "Software and Updates", without it  crashing?
If so open that and go to **Other Software and uncheck any entry for spotify.**
Then run update command again.                 

I ran Software Updater, rebooted and ran it again, each time getting more updates.  Ubuntu Software Center also works. I do have two Software & Updates?
``` 
[SIZE=5]
Thank you[/SIZE] 
     [**[COLOR=#C61919][B]deadflowr, **[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1276577")      [**[COLOR=#DD4814][B]ubudog**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=739457")[**[COLOR=#C61919][B] and  Bucky Ball**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=504316")   [URL="http://ubuntuforums.org/member.php?u=739457"][SIZE=5][FONT=times new roman]For helping me[/FONT][/SIZE]

_I will wait a couple of days to make sure that everthing is still working and then I will post solved._
[/URL]

---

### Post by Bucky Ball on 2014-07-04
All good. Please mark your thread as solved using Thread Tools at top right. Thanks.

---

