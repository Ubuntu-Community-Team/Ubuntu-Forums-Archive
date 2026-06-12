---
title: "The update information is outdated"
date: 2014-10-07
forum: General Help
---

### Post by jpiserhard on 2014-10-07
> "The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by selecting "Show updates" from the indicator menu, and watching for any failing repository."
Today I switched on my computer and on the top bar appears one orange triangle with a "!" in the center and says that the update information is outdated and when I click on "show updates" appears a message saying that my computer is already updated. I'm new on ubuntu and I don't know what to do. My version is 14.04. Can someone help me?

---

### Post by papibe on 2014-10-07
Hi jpiserhard.

Could you open a terminal run this command, and post back the results (you can copy/paste the text)?
```
sudo apt-get update
```
Regards.

---

### Post by jpiserhard on 2014-10-07
> **papibe said:**
> Hi jpiserhard.

Could you open a terminal run this command, and post back the results (you can copy/paste the text)?
```
sudo apt-get update
```
Regards.


These was the results:
```
joao@JOAO-PC:~$ sudo apt-get update[sudo] password for joao: 
Ign http://br.archive.ubuntu.com trusty InRelease                              
Ign http://br.archive.ubuntu.com trusty-updates InRelease                      
Ign http://dl.google.com stable InRelease                                      
Ign http://br.archive.ubuntu.com trusty-backports InRelease                    
Reached http://br.archive.ubuntu.com trusty Release.gpg                       
Get:1 http://br.archive.ubuntu.com trusty-updates Release.gpg [933 B]        
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Reached http://deb.playonlinux.com trusty InRelease                           
Get:2 http://br.archive.ubuntu.com trusty-backports Release.gpg [933 B]      
Reached http://br.archive.ubuntu.com trusty Release                           
Ign http://dl.google.com stable InRelease                                      
Get:3 http://br.archive.ubuntu.com trusty-updates Release [59,7 kB]          
Reached http://extras.ubuntu.com trusty Release.gpg                           
Reached http://security.ubuntu.com trusty-security Release.gpg                
Reached http://archive.canonical.com trusty Release.gpg                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:4 http://br.archive.ubuntu.com trusty-backports Release [59,7 kB]        
Get:5 http://dl.google.com stable Release.gpg [198 B]                        
Reached http://br.archive.ubuntu.com trusty/main Sources                      
Reached http://br.archive.ubuntu.com trusty/restricted Sources                
Reached http://extras.ubuntu.com trusty Release                               
Reached http://security.ubuntu.com trusty-security Release                    
Reached http://archive.canonical.com trusty Release                           
Reached http://br.archive.ubuntu.com trusty/universe Sources                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Reached http://br.archive.ubuntu.com trusty/multiverse Sources                
Reached http://br.archive.ubuntu.com trusty/main amd64 Packages               
Reached http://br.archive.ubuntu.com trusty/restricted amd64 Packages         
Reached http://dl.google.com stable Release.gpg                               
Reached http://br.archive.ubuntu.com trusty/universe amd64 Packages           
Reached http://extras.ubuntu.com trusty/main Sources                          
Reached http://br.archive.ubuntu.com trusty/multiverse amd64 Packages         
Reached http://security.ubuntu.com trusty-security/main Sources               
Ign http://ppa.launchpad.net trusty InRelease                                  
Reached http://br.archive.ubuntu.com trusty/main i386 Packages                
Reached http://br.archive.ubuntu.com trusty/restricted i386 Packages          
Reached http://deb.playonlinux.com trusty/main amd64 Packages                 
Reached http://archive.canonical.com trusty/partner amd64 Packages            
Reached http://extras.ubuntu.com trusty/main amd64 Packages                   
Get:6 http://dl.google.com stable Release [1.347 B]                          
Reached http://br.archive.ubuntu.com trusty/universe i386 Packages            
Reached http://security.ubuntu.com trusty-security/restricted Sources         
Ign http://ppa.launchpad.net trusty InRelease                                  
Reached http://br.archive.ubuntu.com trusty/multiverse i386 Packages          
Reached http://br.archive.ubuntu.com trusty/main Translation-pt_BR            
Reached http://archive.canonical.com trusty/partner i386 Packages             
Reached http://deb.playonlinux.com trusty/main i386 Packages                  
Reached http://br.archive.ubuntu.com trusty/main Translation-pt               
Reached http://br.archive.ubuntu.com trusty/main Translation-en               
Reached http://extras.ubuntu.com trusty/main i386 Packages                    
Reached http://br.archive.ubuntu.com trusty/multiverse Translation-pt_BR      
Reached http://security.ubuntu.com trusty-security/universe Sources           
Reached http://dl.google.com stable Release                                   
Ign http://ppa.launchpad.net trusty Release.gpg                                
Reached http://br.archive.ubuntu.com trusty/multiverse Translation-pt         
Reached http://br.archive.ubuntu.com trusty/multiverse Translation-en         
Reached http://archive.canonical.com trusty/partner Translation-en            
Reached http://br.archive.ubuntu.com trusty/restricted Translation-pt_BR      
Reached http://br.archive.ubuntu.com trusty/restricted Translation-pt         
Ign https://private-ppa.launchpad.net trusty InRelease                         
Reached http://security.ubuntu.com trusty-security/multiverse Sources         
Reached http://br.archive.ubuntu.com trusty/restricted Translation-en         
Get:7 http://dl.google.com stable/main amd64 Packages [1.188 B]              
Reached http://br.archive.ubuntu.com trusty/universe Translation-pt_BR        
Reached http://ppa.launchpad.net trusty Release.gpg                           
Reached http://br.archive.ubuntu.com trusty/universe Translation-pt           
Reached http://br.archive.ubuntu.com trusty/universe Translation-en           
Get:8 http://br.archive.ubuntu.com trusty-updates/main Sources [126 kB]      
Reached http://security.ubuntu.com trusty-security/main amd64 Packages        
Reached https://private-ppa.launchpad.net trusty Release.gpg                  
Get:9 http://ppa.launchpad.net trusty Release.gpg [316 B]                    
Get:10 http://dl.google.com stable/main i386 Packages [1.186 B]              
Get:11 http://br.archive.ubuntu.com trusty-updates/restricted Sources [1.408 B]
Get:12 http://br.archive.ubuntu.com trusty-updates/universe Sources [86,7 kB]
Reached http://security.ubuntu.com trusty-security/restricted amd64 Packages  
Reached https://private-ppa.launchpad.net trusty Release                      
Reached http://ppa.launchpad.net trusty Release.gpg                           
Get:13 http://br.archive.ubuntu.com trusty-updates/multiverse Sources [3.531 B]
Reached http://security.ubuntu.com trusty-security/universe amd64 Packages    
Get:14 http://br.archive.ubuntu.com trusty-updates/main amd64 Packages [337 kB]
Ign http://ppa.launchpad.net trusty Release.gpg                                
Reached https://private-ppa.launchpad.net trusty/main amd64 Packages          
Reached http://security.ubuntu.com trusty-security/multiverse amd64 Packages  
Ign http://ppa.launchpad.net trusty Release                                    
Get:15 http://br.archive.ubuntu.com trusty-updates/restricted amd64 Packages [5.820 B]
Reached https://private-ppa.launchpad.net trusty/main i386 Packages           
Reached http://security.ubuntu.com trusty-security/main i386 Packages         
Get:16 http://br.archive.ubuntu.com trusty-updates/universe amd64 Packages [210 kB]
Reached http://ppa.launchpad.net trusty Release                               
Reached http://dl.google.com stable/main amd64 Packages                       
Reached http://security.ubuntu.com trusty-security/restricted i386 Packages   
Get:17 http://br.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [9.366 B]
Get:18 http://br.archive.ubuntu.com trusty-updates/main i386 Packages [331 kB]
Get:19 http://ppa.launchpad.net trusty Release [14,5 kB]                     
Reached http://security.ubuntu.com trusty-security/universe i386 Packages     
Reached http://dl.google.com stable/main i386 Packages                        
Get:20 http://br.archive.ubuntu.com trusty-updates/restricted i386 Packages [5.820 B]
Get:21 http://br.archive.ubuntu.com trusty-updates/universe i386 Packages [211 kB]
Reached http://security.ubuntu.com trusty-security/multiverse i386 Packages   
Reached http://ppa.launchpad.net trusty Release                               
Get:22 http://br.archive.ubuntu.com trusty-updates/multiverse i386 Packages [9.532 B]
Get:23 http://br.archive.ubuntu.com trusty-updates/main Translation-en [150 kB]
Reached http://security.ubuntu.com trusty-security/main Translation-en        
Ign http://ppa.launchpad.net trusty Release                                    
Reached http://br.archive.ubuntu.com trusty-updates/multiverse Translation-en 
Reached http://br.archive.ubuntu.com trusty-updates/restricted Translation-en 
Get:24 http://br.archive.ubuntu.com trusty-updates/universe Translation-en [106 kB]
Reached http://security.ubuntu.com trusty-security/multiverse Translation-en  
Get:25 http://br.archive.ubuntu.com trusty-backports/main Sources [4.760 B]  
Get:26 http://br.archive.ubuntu.com trusty-backports/restricted Sources [14 B]
Get:27 http://br.archive.ubuntu.com trusty-backports/universe Sources [14,1 kB]
Reached http://security.ubuntu.com trusty-security/restricted Translation-en  
Get:28 http://br.archive.ubuntu.com trusty-backports/multiverse Sources [1.883 B]
Ign http://extras.ubuntu.com trusty/main Translation-pt_BR                     
Get:29 http://br.archive.ubuntu.com trusty-backports/main amd64 Packages [6.356 B]
Get:30 http://br.archive.ubuntu.com trusty-backports/restricted amd64 Packages [14 B]
Get:31 http://br.archive.ubuntu.com trusty-backports/universe amd64 Packages [17,4 kB]
Ign http://extras.ubuntu.com trusty/main Translation-pt                        
Get:32 http://br.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1.231 B]
Get:33 http://br.archive.ubuntu.com trusty-backports/main i386 Packages [6.379 B]
Ign http://deb.playonlinux.com trusty/main Translation-pt_BR                   
Get:34 http://br.archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]
Get:35 http://br.archive.ubuntu.com trusty-backports/universe i386 Packages [17,4 kB]
Reached http://security.ubuntu.com trusty-security/universe Translation-en    
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:36 http://br.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1.235 B]
Reached http://br.archive.ubuntu.com trusty-backports/main Translation-en     
Reached http://br.archive.ubuntu.com trusty-backports/multiverse Translation-en
Ign http://deb.playonlinux.com trusty/main Translation-pt                      
Reached http://br.archive.ubuntu.com trusty-backports/restricted Translation-en
Reached http://br.archive.ubuntu.com trusty-backports/universe Translation-en 
Ign http://deb.playonlinux.com trusty/main Translation-en                      
Reached http://ppa.launchpad.net trusty/main amd64 Packages                   
Reached http://ppa.launchpad.net trusty/main i386 Packages                    
Ign https://private-ppa.launchpad.net trusty/main Translation-pt_BR            
Ign https://private-ppa.launchpad.net trusty/main Translation-pt               
Get:37 http://ppa.launchpad.net trusty/main amd64 Packages [3.060 B]         
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Get:38 http://ppa.launchpad.net trusty/main i386 Packages [3.040 B]          
Get:39 http://ppa.launchpad.net trusty/main Translation-en [1.386 B]         
Reached http://ppa.launchpad.net trusty/main amd64 Packages                   
Reached http://ppa.launchpad.net trusty/main i386 Packages                    
Ign http://dl.google.com stable/main Translation-pt_BR                         
Ign http://dl.google.com stable/main Translation-pt                            
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-pt_BR                         
Ign http://dl.google.com stable/main Translation-pt                            
Ign http://dl.google.com stable/main Translation-en                            
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-pt_BR
Ign http://ppa.launchpad.net trusty/main Translation-pt
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-pt_BR
Ign http://ppa.launchpad.net trusty/main Translation-pt
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-pt_BR
Ign http://ppa.launchpad.net trusty/main Translation-pt
Ign http://ppa.launchpad.net trusty/main Translation-en
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-pt_BR
Ign http://ppa.launchpad.net trusty/main Translation-pt
Ign http://ppa.launchpad.net trusty/main Translation-en
Downloaded 1.813 kB em 27s (64,9 kB/s)
W: Failed to fetch http://ppa.launchpad.net/samba-team/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/samba-team/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/multimedia/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/multimedia/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


E: Failed to download some index files. Were ignored or older were used instead.



```

Kind regards

---

### Post by deadflowr on 2014-10-08
Open the program "Software and Updates."
Go to the tab marked Other Software.
Uncheck, or remove the entries for both samba-team, and upubuntu, as they have no ppa's for trusty.
Then Close software and updates.
Then re-run the apt-get update command again.
(Or hopefully it will ask to reload when you close software and updates)

---

### Post by jpiserhard on 2014-10-08
> **deadflowr said:**
> Open the program "Software and Updates."
Go to the tab marked Other Software.
Uncheck, or remove the entries for both samba-team, and upubuntu, as they have no ppa's for trusty.
Then Close software and updates.
Then re-run the apt-get update command again.
(Or hopefully it will ask to reload when you close software and updates)

It worked! Thank you.

---

