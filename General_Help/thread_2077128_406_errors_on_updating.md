---
title: "406 errors on updating"
date: 2012-10-27
forum: General Help
---

### Post by von Stalhein on 2012-10-27
Recently any updates run are reporting "406 not acceptable" errors on a couple of source entries:
```
Ign http://ftp.iinet.net.au precise InRelease
Ign http://ftp.iinet.net.au precise-updates InRelease                          
Ign http://ftp.iinet.net.au precise-backports InRelease                        
Ign http://ftp.iinet.net.au precise-security InRelease                         
Hit http://ftp.iinet.net.au precise Release.gpg                                
Hit http://ftp.iinet.net.au precise-updates Release.gpg                        
Hit http://ftp.iinet.net.au precise-backports Release.gpg                      
Hit http://ftp.iinet.net.au precise-security Release.gpg                       
Hit http://ftp.iinet.net.au precise Release                                    
Hit http://ftp.iinet.net.au precise-updates Release                            
Hit http://ftp.iinet.net.au precise-backports Release                          
Ign http://download.ebz.epson.net lsb3.2 InRelease                             
Hit http://ftp.iinet.net.au precise-security Release                           
Hit http://ftp.iinet.net.au precise/main Sources                               
Hit http://ftp.iinet.net.au precise/restricted Sources                         
Ign http://archive.canonical.com precise InRelease                             
Ign http://linux.dropbox.com precise InRelease                                 
Hit http://ftp.iinet.net.au precise/multiverse Sources                         
Hit http://ftp.iinet.net.au precise/main i386 Packages                         
Hit http://ftp.iinet.net.au precise/restricted i386 Packages                   
Hit http://ftp.iinet.net.au precise/universe i386 Packages                     
Hit http://ftp.iinet.net.au precise/multiverse i386 Packages                   
Hit http://ftp.iinet.net.au precise/main TranslationIndex                      
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ftp.iinet.net.au precise/multiverse TranslationIndex                
Hit http://ftp.iinet.net.au precise/restricted TranslationIndex                
Hit http://ftp.iinet.net.au precise/universe TranslationIndex                  
Hit http://download.ebz.epson.net lsb3.2 Release.gpg                           
Hit http://ftp.iinet.net.au precise-updates/main Sources                       
Hit http://ftp.iinet.net.au precise-updates/restricted Sources                 
Get:1 http://linux.dropbox.com precise Release.gpg [489 B]                     
Hit http://ftp.iinet.net.au precise-updates/universe Sources                   
Hit http://ftp.iinet.net.au precise-updates/multiverse Sources                 
Hit http://ftp.iinet.net.au precise-updates/main i386 Packages                 
Hit http://ftp.iinet.net.au precise-updates/restricted i386 Packages           
Hit http://ftp.iinet.net.au precise-updates/universe i386 Packages             
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://ftp.iinet.net.au precise-updates/multiverse i386 Packages           
Hit http://ftp.iinet.net.au precise-updates/main TranslationIndex              
Hit http://ftp.iinet.net.au precise-updates/multiverse TranslationIndex        
Hit http://ftp.iinet.net.au precise-updates/restricted TranslationIndex        
Hit http://ftp.iinet.net.au precise-updates/universe TranslationIndex          
Hit http://ftp.iinet.net.au precise-backports/main Sources                     
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://ftp.iinet.net.au precise-backports/restricted Sources               
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:2 http://linux.dropbox.com precise Release [2,603 B]                       
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://download.ebz.epson.net lsb3.2 Release                               
Hit http://ftp.iinet.net.au precise-backports/universe Sources                 
Hit http://ftp.iinet.net.au precise-backports/multiverse Sources               
Hit http://ftp.iinet.net.au precise-backports/main i386 Packages               
Hit http://ftp.iinet.net.au precise-backports/restricted i386 Packages         
Hit http://ftp.iinet.net.au precise-backports/universe i386 Packages           
Hit http://ftp.iinet.net.au precise-backports/multiverse i386 Packages         
Hit http://ftp.iinet.net.au precise-backports/main TranslationIndex            
Hit http://ftp.iinet.net.au precise-backports/multiverse TranslationIndex      
Hit http://archive.canonical.com precise Release                               
Hit http://ftp.iinet.net.au precise-backports/restricted TranslationIndex      
Hit http://ftp.iinet.net.au precise-backports/universe TranslationIndex        
Hit http://ftp.iinet.net.au precise-security/main Sources                      
Hit http://ftp.iinet.net.au precise-security/restricted Sources                
Hit http://ftp.iinet.net.au precise-security/universe Sources                  
Hit http://ftp.iinet.net.au precise-security/multiverse Sources                
Hit http://ftp.iinet.net.au precise-security/main i386 Packages                
Get:3 http://linux.dropbox.com precise/main i386 Packages [1,029 B]            
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages                    
Hit http://ftp.iinet.net.au precise-security/restricted i386 Packages          
Hit http://ftp.iinet.net.au precise-security/universe i386 Packages            
Hit http://ftp.iinet.net.au precise-security/multiverse i386 Packages          
Hit http://ftp.iinet.net.au precise-security/main TranslationIndex             
Hit http://ftp.iinet.net.au precise-security/multiverse TranslationIndex       
Hit http://ftp.iinet.net.au precise-security/restricted TranslationIndex       
Hit http://ftp.iinet.net.au precise-security/universe TranslationIndex         
Hit http://archive.canonical.com precise/partner Sources                       
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://download.ebz.epson.net lsb3.2/main TranslationIndex                 
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://packages.medibuntu.org precise InRelease                            
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://packages.medibuntu.org precise/free Sources                         
Get:4 http://ftp.iinet.net.au precise/universe Sources [6,239 kB]              
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ftp.iinet.net.au precise/main Translation-en_AU                     
Hit http://ftp.iinet.net.au precise/main Translation-en                        
Hit http://ftp.iinet.net.au precise/multiverse Translation-en_AU               
Hit http://ftp.iinet.net.au precise/multiverse Translation-en                  
Hit http://ftp.iinet.net.au precise/restricted Translation-en_AU               
Hit http://ftp.iinet.net.au precise/restricted Translation-en                  
Hit http://ftp.iinet.net.au precise/universe Translation-en                    
Hit http://ftp.iinet.net.au precise-updates/main Translation-en_AU             
Hit http://ftp.iinet.net.au precise-updates/main Translation-en                
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://ftp.iinet.net.au precise-updates/multiverse Translation-en_AU       
Hit http://ftp.iinet.net.au precise-updates/multiverse Translation-en          
Hit http://ftp.iinet.net.au precise-updates/restricted Translation-en_AU       
Hit http://ftp.iinet.net.au precise-updates/restricted Translation-en          
Hit http://ftp.iinet.net.au precise-updates/universe Translation-en            
Hit http://ftp.iinet.net.au precise-backports/main Translation-en              
Hit http://ftp.iinet.net.au precise-backports/multiverse Translation-en        
Hit http://ftp.iinet.net.au precise-backports/restricted Translation-en        
Hit http://ftp.iinet.net.au precise-backports/universe Translation-en          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ftp.iinet.net.au precise-security/main Translation-en               
Hit http://ftp.iinet.net.au precise-security/multiverse Translation-en         
Hit http://ftp.iinet.net.au precise-security/restricted Translation-en         
Hit http://ftp.iinet.net.au precise-security/universe Translation-en           
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://packages.medibuntu.org precise/non-free Sources                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://linux.dropbox.com precise/main Translation-en_AU                    
Ign http://linux.dropbox.com precise/main Translation-en                       
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Ign http://download.ebz.epson.net lsb3.2/main Translation-en_AU                
Err http://ftp.iinet.net.au precise/universe Sources                           
  
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Err http://ftp.iinet.net.au precise/universe Sources                           
  406  Not Acceptable
Ign http://download.ebz.epson.net lsb3.2/main Translation-en                   
Ign http://archive.canonical.com precise/partner Translation-en_AU             
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Ign http://ppa.launchpad.net precise/main Translation-en_AU                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_AU                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_AU                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_AU                    
Ign http://ppa.launchpad.net precise/main Translation-en_AU                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_AU                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_AU                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://packages.medibuntu.org precise/free Translation-en_AU               
Ign http://packages.medibuntu.org precise/free Translation-en
Ign http://packages.medibuntu.org precise/non-free Translation-en_AU
Ign http://packages.medibuntu.org precise/non-free Translation-en
Fetched 4,122 B in 21s (188 B/s)
W: Failed to fetch http://ftp.iinet.net.au/pub/ubuntu/dists/precise/universe/source/Sources  406  Not Acceptable

E: Some index files failed to download. They have been ignored, or old ones used instead.
```Where do I start top troubleshoot that? Google hasn't helped. thanks in advance.

---

### Post by von Stalhein on 2012-10-28
Bump? :)

---

### Post by von Stalhein on 2012-10-29
You can all stop searching :P , I seem to have sorted it ("seemed", I say, as time will tell!!).

I removed the Universe repositories from the sources list, rebooted, re enabled the Universe group and then ```
sudo apt-get update 
``` ftw!

Nek minnit, all good (so far).

Hopefully that might help someone else. The issue was triggered after an update about 2 weeks ago I think.

---

