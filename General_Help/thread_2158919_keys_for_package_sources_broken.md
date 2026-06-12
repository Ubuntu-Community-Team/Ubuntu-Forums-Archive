---
title: "keys for package sources broken?"
date: 2013-07-01
forum: General Help
---

### Post by ottosykora on 2013-07-01
I am trying to run normal update on my 12.04/32bit but now for all packets it tells me that those are from not authenticated sources. Even the main ubuntu server.

Where can I get the key/cert for the ubuntu update server ?

---

### Post by plucky on 2013-07-01
> I am trying to run normal update on my 12.04/32bit but now for all packets it tells me that those are from not authenticated sources. Even the main ubuntu server.

Where can I get the key/cert for the ubuntu update server ? 

Post output for ```
sudo apt-get update
``` from a terminal window.

---

### Post by ottosykora on 2013-07-01
Well apt-get update will do exactly same as the GUI version, namely get the list of the items, but not install it as either the whole keyring or just some of the keys got hosed.
Therefore I think I should reimport some ubuntu keys in fact. But have no idea where I can get them.




```
Paketlisten werden gelesen... Fertig
otto@LAPTOPOTTOS7L:~$ sudo apt-get update
OK   http://repo.wuala.com stable Release.gpg                                  
OK   http://ppa.launchpad.net precise Release.gpg                              
OK   http://archive.canonical.com precise Release.gpg                          
OK   http://repo.wuala.com stable Release                                      
OK   http://dl.google.com stable Release.gpg                                   
OK   http://archive.ubuntu.com precise Release.gpg                             
OK   http://extras.ubuntu.com precise Release.gpg                              
OK   http://ppa.launchpad.net precise Release                                  
OK   http://archive.ubuntu.com precise-updates Release.gpg                     
OK   http://deb.torproject.org precise Release.gpg                             
OK   http://archive.ubuntu.com precise-security Release.gpg                    
OK   http://archive.canonical.com precise Release                              
OK   http://extras.ubuntu.com precise Release                                  
OK   http://deb.torproject.org precise Release                                 
OK   http://ppa.launchpad.net precise/main Sources                             
OK   http://repo.wuala.com stable/main i386 Packages                           
OK   http://archive.ubuntu.com precise Release                                 
OK   http://archive.ubuntu.com precise-updates Release                         
OK   http://dl.google.com stable Release                                       
OK   http://archive.canonical.com precise/partner Sources                      
OK   http://ppa.launchpad.net precise/main i386 Packages                       
OK   http://extras.ubuntu.com precise/main Sources                             
OK   http://deb.torproject.org precise/main Sources                            
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
OK   http://extras.ubuntu.com precise/main i386 Packages                       
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
OK   http://deb.torproject.org precise/main i386 Packages                      
Ign http://deb.torproject.org precise/main TranslationIndex                    
Ign http://repo.wuala.com stable/main TranslationIndex                         
OK   http://archive.canonical.com precise/partner i386 Packages                
Ign http://archive.canonical.com precise/partner TranslationIndex          
OK   http://archive.ubuntu.com precise-security Release                    
OK   http://archive.ubuntu.com precise/main Sources                            
OK   http://archive.ubuntu.com precise/restricted Sources                      
OK   http://archive.ubuntu.com precise/multiverse Sources                      
OK   http://archive.ubuntu.com precise/universe Sources                        
OK   http://archive.ubuntu.com precise/main i386 Packages                      
OK   http://archive.ubuntu.com precise/restricted i386 Packages                
OK   http://archive.ubuntu.com precise/universe i386 Packages                  
OK   http://archive.ubuntu.com precise/multiverse i386 Packages                
OK   http://archive.ubuntu.com precise/main TranslationIndex                   
OK   http://archive.ubuntu.com precise/multiverse TranslationIndex             
OK   http://archive.ubuntu.com precise/restricted TranslationIndex             
OK   http://archive.ubuntu.com precise/universe TranslationIndex               
OK   http://archive.ubuntu.com precise-updates/restricted Sources              
OK   http://archive.ubuntu.com precise-updates/main Sources                    
OK   http://archive.ubuntu.com precise-updates/multiverse Sources              
OK   http://archive.ubuntu.com precise-updates/universe Sources                
OK   http://archive.ubuntu.com precise-updates/main i386 Packages              
OK   http://archive.ubuntu.com precise-updates/restricted i386 Packages        
OK   http://archive.ubuntu.com precise-updates/universe i386 Packages          
OK   http://archive.ubuntu.com precise-updates/multiverse i386 Packages        
OK   http://archive.ubuntu.com precise-updates/main TranslationIndex           
OK   http://archive.ubuntu.com precise-updates/multiverse TranslationIndex     
OK   http://archive.ubuntu.com precise-updates/restricted TranslationIndex     
OK   http://archive.ubuntu.com precise-updates/universe TranslationIndex       
OK   http://archive.ubuntu.com precise-security/restricted Sources             
OK   http://archive.ubuntu.com precise-security/main Sources                   
OK   http://archive.ubuntu.com precise-security/multiverse Sources             
OK   http://archive.ubuntu.com precise-security/universe Sources               
OK   http://archive.ubuntu.com precise-security/main i386 Packages             
OK   http://archive.ubuntu.com precise-security/restricted i386 Packages       
OK   http://archive.ubuntu.com precise-security/universe i386 Packages         
OK   http://archive.ubuntu.com precise-security/multiverse i386 Packages       
Ign http://deb.torproject.org precise/main Translation-de_CH                   
OK   http://archive.ubuntu.com precise-security/main TranslationIndex          
OK   http://archive.ubuntu.com precise-security/multiverse TranslationIndex    
OK   http://archive.ubuntu.com precise-security/restricted TranslationIndex    
OK   http://archive.ubuntu.com precise-security/universe TranslationIndex      
OK   http://archive.ubuntu.com precise/main Translation-de                     
OK   http://archive.ubuntu.com precise/main Translation-en                     
Ign http://ppa.launchpad.net precise/main Translation-de_CH                    
Ign http://ppa.launchpad.net precise/main Translation-de                       
Ign http://deb.torproject.org precise/main Translation-de                      
OK   http://archive.ubuntu.com precise/multiverse Translation-de               
OK   http://archive.ubuntu.com precise/multiverse Translation-en               
Ign http://deb.torproject.org precise/main Translation-en                      
OK   http://archive.ubuntu.com precise/restricted Translation-de               
OK   http://archive.ubuntu.com precise/restricted Translation-en               
OK   http://archive.ubuntu.com precise/universe Translation-de                 
OK   http://archive.ubuntu.com precise/universe Translation-en                 
OK   http://archive.ubuntu.com precise-updates/main Translation-de             
Ign http://ppa.launchpad.net precise/main Translation-en                       
OK   http://archive.ubuntu.com precise-updates/main Translation-en             
OK   http://archive.ubuntu.com precise-updates/multiverse Translation-de       
OK   http://archive.ubuntu.com precise-updates/multiverse Translation-en       
OK   http://archive.ubuntu.com precise-updates/restricted Translation-de       
OK   http://archive.ubuntu.com precise-updates/restricted Translation-en       
OK   http://archive.ubuntu.com precise-updates/universe Translation-de         
OK   http://dl.google.com stable/main i386 Packages                            
Ign http://dl.google.com stable/main TranslationIndex                          
OK   http://archive.ubuntu.com precise-updates/universe Translation-en         
Ign http://repo.wuala.com stable/main Translation-de_CH                        
OK   http://archive.ubuntu.com precise-security/main Translation-en            
OK   http://archive.ubuntu.com precise-security/multiverse Translation-en      
OK   http://archive.ubuntu.com precise-security/restricted Translation-en      
Ign http://repo.wuala.com stable/main Translation-de                           
OK   http://archive.ubuntu.com precise-security/universe Translation-en        
Ign http://repo.wuala.com stable/main Translation-en                           
Ign http://archive.canonical.com precise/partner Translation-de_CH             
Ign http://archive.canonical.com precise/partner Translation-de            
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://dl.google.com stable/main Translation-de_CH
Ign http://dl.google.com stable/main Translation-de
Ign http://extras.ubuntu.com precise/main Translation-de_CH
Ign http://dl.google.com stable/main Translation-en
Ign http://extras.ubuntu.com precise/main Translation-de
Ign http://extras.ubuntu.com precise/main Translation-en
Paketlisten werden gelesen... Fertig
otto@LAPTOPOTTOS7L:~$ 

```

---

### Post by plucky on 2013-07-01
No errors.

Now post output for ```
sudo apt-get upgrade
```

---

