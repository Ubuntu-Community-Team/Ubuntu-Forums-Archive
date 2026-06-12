---
title: "Ubuntu 12.04.2 error...help!"
date: 2013-02-03
forum: General Help
---

### Post by jomoyomo on 2013-02-03
Hi,
I've updated to ubuntu12.04.2 from 12.04.1.
As usual, I started building and after few minutes, I can move mouse pointers but other things don't respond.

Second problem, my icons in desktop has been gone away and unable to click right button in mouse.

Third problem, When I run update manager, it says unable to connect repository.
Is there way to fix these problem?

Thanks!

---

### Post by ibjsb4 on 2013-02-04
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And post the results please

---

### Post by jomoyomo on 2013-02-04
> **ibjsb4 said:**
> [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```And post the results please


Update manager log:
```

W:Failed to fetch http://archive.ubuntu/dists/hardy/Release.gpg  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy-updates/Release.gpg  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy/main/source/Sources  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy/multiverse/source/Sources  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy/multiverse/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy/main/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy/multiverse/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy-updates/main/source/Sources  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy-updates/multiverse/source/Sources  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy-updates/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy-updates/main/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy/main/i18n/Translation-ko  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy/multiverse/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy/multiverse/i18n/Translation-ko  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy-updates/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy-updates/main/i18n/Translation-ko  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://archive.ubuntu/dists/hardy-updates/multiverse/i18n/Translation-ko  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```

sudo apt-get update issue:

```

Ign http://ftp.daum.net precise InRelease
Ign http://ftp.daum.net precise-updates InRelease                              
Ign http://archive.ubuntu hardy InRelease                                      
Ign http://archive.ubuntu hardy-updates InRelease                              
Err http://archive.ubuntu hardy Release.gpg                                    
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy-updates Release.gpg                            
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu hardy Release                                        
Ign http://archive.ubuntu hardy-updates Release                                
Ign http://archive.ubuntu hardy/main TranslationIndex                          
Ign http://ftp.daum.net precise-backports InRelease                            
Ign http://ftp.daum.net precise-security InRelease                             
Hit http://ftp.daum.net precise Release.gpg                                    
Hit http://ftp.daum.net precise-updates Release.gpg                            
Hit http://ftp.daum.net precise-backports Release.gpg                          
Hit http://ftp.daum.net precise-security Release.gpg                           
Hit http://ftp.daum.net precise Release                                        
Hit http://ftp.daum.net precise-updates Release                                
Hit http://ftp.daum.net precise-backports Release                              
Hit http://ftp.daum.net precise-security Release                               
Ign http://archive.ubuntu hardy/multiverse TranslationIndex                    
Hit http://ftp.daum.net precise/main Sources                                   
Ign http://dl.google.com stable InRelease                                      
Ign http://archive.ubuntu hardy-updates/main TranslationIndex                  
Ign http://archive.ubuntu hardy-updates/multiverse TranslationIndex            
Hit http://ftp.daum.net precise/restricted Sources                             
Hit http://ftp.daum.net precise/universe Sources                               
Hit http://dl.google.com stable Release.gpg                                    
Ign http://www.scootersoftware.com stable InRelease                            
Hit http://ftp.daum.net precise/multiverse Sources                             
Hit http://ftp.daum.net precise/main amd64 Packages                            
Hit http://ftp.daum.net precise/restricted amd64 Packages                      
Hit http://ftp.daum.net precise/universe amd64 Packages                        
Hit http://dl.google.com stable Release                                        
Hit http://ftp.daum.net precise/multiverse amd64 Packages                      
Hit http://ftp.daum.net precise/main i386 Packages                             
Hit http://ftp.daum.net precise/restricted i386 Packages                       
Hit http://ftp.daum.net precise/universe i386 Packages                         
Hit http://ftp.daum.net precise/multiverse i386 Packages                       
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ftp.daum.net precise/main TranslationIndex                          
Hit http://ftp.daum.net precise/multiverse TranslationIndex                    
Hit http://ftp.daum.net precise/restricted TranslationIndex                    
Hit http://ftp.daum.net precise/universe TranslationIndex                      
Hit http://ftp.daum.net precise-updates/main Sources                           
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ftp.daum.net precise-updates/restricted Sources                     
Hit http://ftp.daum.net precise-updates/universe Sources                       
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ftp.daum.net precise-updates/multiverse Sources                     
Hit http://ftp.daum.net precise-updates/main amd64 Packages                    
Hit http://ftp.daum.net precise-updates/restricted amd64 Packages              
Hit http://ftp.daum.net precise-updates/universe amd64 Packages                
Hit http://ftp.daum.net precise-updates/multiverse amd64 Packages              
Hit http://ftp.daum.net precise-updates/main i386 Packages                     
Hit http://www.scootersoftware.com stable Release.gpg                          
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://ftp.daum.net precise-updates/restricted i386 Packages               
Hit http://ftp.daum.net precise-updates/universe i386 Packages                 
Hit http://ftp.daum.net precise-updates/multiverse i386 Packages               
Hit http://ftp.daum.net precise-updates/main TranslationIndex                  
Hit http://ftp.daum.net precise-updates/multiverse TranslationIndex            
Hit http://ftp.daum.net precise-updates/restricted TranslationIndex            
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ftp.daum.net precise-updates/universe TranslationIndex              
Ign http://archive.ubuntu.com hardy InRelease                                  
Ign http://archive.ubuntu.com hardy-updates InRelease                          
Hit http://ftp.daum.net precise-backports/main Sources                         
Hit http://ftp.daum.net precise-backports/restricted Sources                   
Hit http://ftp.daum.net precise-backports/universe Sources                     
Hit http://ftp.daum.net precise-backports/multiverse Sources                   
Hit http://ftp.daum.net precise-backports/main amd64 Packages                  
Err http://archive.ubuntu hardy/main Sources                                   
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy/multiverse Sources                             
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy/main amd64 Packages                            
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy/multiverse amd64 Packages                      
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy/main i386 Packages                             
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Hit http://ftp.daum.net precise-backports/restricted amd64 Packages            
Err http://archive.ubuntu hardy/multiverse i386 Packages                       
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Hit http://ftp.daum.net precise-backports/universe amd64 Packages              
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://ftp.daum.net precise-backports/multiverse amd64 Packages            
Hit http://ftp.daum.net precise-backports/main i386 Packages                   
Err http://archive.ubuntu hardy-updates/main Sources                           
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Hit http://extras.ubuntu.com precise Release.gpg                               
Err http://archive.ubuntu hardy-updates/multiverse Sources                     
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy-updates/main amd64 Packages                    
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy-updates/multiverse amd64 Packages              
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy-updates/main i386 Packages                     
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Hit http://ftp.daum.net precise-backports/restricted i386 Packages             
Err http://archive.ubuntu hardy-updates/multiverse i386 Packages               
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Hit http://packages.mate-desktop.org precise InRelease                         
Hit http://ftp.daum.net precise-backports/universe i386 Packages               
Hit http://ftp.daum.net precise-backports/multiverse i386 Packages             
Hit http://ftp.daum.net precise-backports/main TranslationIndex                
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Err http://archive.ubuntu hardy/main Translation-en_US                         
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Hit http://archive.ubuntu.com hardy Release.gpg                                
Hit http://www.scootersoftware.com stable Release                              
Err http://archive.ubuntu hardy/main Translation-en                            
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Hit http://ftp.daum.net precise-backports/multiverse TranslationIndex          
Hit http://ftp.daum.net precise-backports/restricted TranslationIndex          
Err http://archive.ubuntu hardy/main Translation-ko                            
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy/multiverse Translation-en_US                   
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy/multiverse Translation-en                      
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Hit http://ftp.daum.net precise-backports/universe TranslationIndex            
Err http://archive.ubuntu hardy/multiverse Translation-ko                      
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy-updates/main Translation-en_US                 
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy-updates/main Translation-en                    
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy-updates/main Translation-ko                    
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy-updates/multiverse Translation-en_US           
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Hit http://ftp.daum.net precise-security/main Sources                          
Err http://archive.ubuntu hardy-updates/multiverse Translation-en              
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu hardy-updates/multiverse Translation-ko              
  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)
Hit http://ftp.daum.net precise-security/restricted Sources                    
Hit http://ftp.daum.net precise-security/universe Sources                      
Hit http://ftp.daum.net precise-security/multiverse Sources                    
Hit http://ftp.daum.net precise-security/main amd64 Packages                   
Hit http://ftp.daum.net precise-security/restricted amd64 Packages             
Hit http://ftp.daum.net precise-security/universe amd64 Packages               
Hit http://ftp.daum.net precise-security/multiverse amd64 Packages             
Hit http://ftp.daum.net precise-security/main i386 Packages                    
Hit http://ftp.daum.net precise-security/restricted i386 Packages              
Hit http://ftp.daum.net precise-security/universe i386 Packages                
Hit http://archive.canonical.com precise Release                               
Hit http://ftp.daum.net precise-security/multiverse i386 Packages              
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ftp.daum.net precise-security/main TranslationIndex                 
Hit http://ftp.daum.net precise-security/multiverse TranslationIndex           
Hit http://ftp.daum.net precise-security/restricted TranslationIndex           
Hit http://ftp.daum.net precise-security/universe TranslationIndex             
Hit http://packages.mate-desktop.org precise/main Sources                      
Hit http://ftp.daum.net precise/main Translation-en                            
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://ftp.daum.net precise/main Translation-ko                            
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ftp.daum.net precise/multiverse Translation-en                      
Hit http://ftp.daum.net precise/restricted Translation-en                      
Hit http://ftp.daum.net precise/restricted Translation-ko                      
Hit http://ftp.daum.net precise/universe Translation-en                        
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ftp.daum.net precise/universe Translation-ko                        
Hit http://www.scootersoftware.com stable/non-free amd64 Packages              
Hit http://ftp.daum.net precise-updates/main Translation-en                    
Hit http://ftp.daum.net precise-updates/main Translation-ko                    
Hit http://ftp.daum.net precise-updates/multiverse Translation-en              
Hit http://ftp.daum.net precise-updates/restricted Translation-en              
Ign http://dl.google.com stable/main Translation-ko                            
Hit http://ftp.daum.net precise-updates/restricted Translation-ko              
Hit http://ftp.daum.net precise-updates/universe Translation-en                
Hit http://ftp.daum.net precise-updates/universe Translation-ko                
Hit http://ftp.daum.net precise-backports/main Translation-en                  
Hit http://ftp.daum.net precise-backports/multiverse Translation-en            
Hit http://ftp.daum.net precise-backports/restricted Translation-en            
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://ftp.daum.net precise-backports/universe Translation-en              
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ftp.daum.net precise-security/main Translation-en                   
Hit http://ftp.daum.net precise-security/multiverse Translation-en             
Hit http://packages.mate-desktop.org precise/main amd64 Packages               
Hit http://packages.mate-desktop.org precise/main i386 Packages                
Hit http://ftp.daum.net precise-security/restricted Translation-en             
Hit http://ftp.daum.net precise-security/universe Translation-en               
Hit http://archive.ubuntu.com hardy Release                                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://www.scootersoftware.com stable/non-free i386 Packages               
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://packages.mate-desktop.org precise/main TranslationIndex             
Hit http://archive.ubuntu.com hardy-updates Release                            
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://www.scootersoftware.com stable/non-free TranslationIndex            
Hit http://archive.ubuntu.com hardy/main Sources                               
Hit http://archive.ubuntu.com hardy/multiverse Sources                         
Hit http://archive.ubuntu.com hardy/main amd64 Packages                        
Hit http://archive.ubuntu.com hardy/multiverse amd64 Packages                  
Hit http://archive.ubuntu.com hardy/main i386 Packages                         
Hit http://archive.ubuntu.com hardy/multiverse i386 Packages                   
Ign http://archive.ubuntu.com hardy/main TranslationIndex                      
Ign http://archive.ubuntu.com hardy/multiverse TranslationIndex                
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.ubuntu.com hardy-updates/main Sources                       
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources                 
Hit http://archive.ubuntu.com hardy-updates/main amd64 Packages                
Hit http://archive.ubuntu.com hardy-updates/multiverse amd64 Packages          
Hit http://archive.ubuntu.com hardy-updates/main i386 Packages                 
Hit http://archive.ubuntu.com hardy-updates/multiverse i386 Packages           
Hit http://archive.ubuntu.com hardy-updates/main TranslationIndex              
Hit http://archive.ubuntu.com hardy-updates/multiverse TranslationIndex        
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
Hit http://archive.ubuntu.com hardy/main Translation-ko                        
Hit http://archive.ubuntu.com hardy-updates/main Translation-ko                
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://archive.canonical.com precise/partner Translation-ko                
Ign http://archive.ubuntu.com hardy/main Translation-en_US                                                                                 
Ign http://archive.ubuntu.com hardy/main Translation-en                                                                                    
Ign http://packages.mate-desktop.org precise/main Translation-en_US                                                         
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                                                
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                                
Ign http://ppa.launchpad.net precise/main Translation-en                                                                    
Ign http://ppa.launchpad.net precise/main Translation-ko                                                                                   
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                                
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                   
Ign http://ppa.launchpad.net precise/main Translation-ko                                                                                   
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US                                                            
Ign http://packages.mate-desktop.org precise/main Translation-en                                                                           
Ign http://extras.ubuntu.com precise/main Translation-en                                                                                   
Ign http://archive.ubuntu.com hardy/multiverse Translation-en                                                                              
Ign http://archive.ubuntu.com hardy/multiverse Translation-ko                                                         
Ign http://packages.mate-desktop.org precise/main Translation-ko                                                      
Ign http://extras.ubuntu.com precise/main Translation-ko                                                                         
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                      
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-ko
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-ko
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-ko
Ign http://www.scootersoftware.com stable/non-free Translation-en_US
Ign http://www.scootersoftware.com stable/non-free Translation-en
Ign http://www.scootersoftware.com stable/non-free Translation-ko
W: Failed to fetch http://archive.ubuntu/dists/hardy/Release.gpg  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/Release.gpg  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy/main/source/Sources  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy/multiverse/source/Sources  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy/multiverse/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy/main/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy/multiverse/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/main/source/Sources  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/multiverse/source/Sources  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/main/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy/main/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy/main/i18n/Translation-ko  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy/multiverse/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy/multiverse/i18n/Translation-ko  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/main/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/main/i18n/Translation-ko  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu/dists/hardy-updates/multiverse/i18n/Translation-ko  Something wicked happened resolving 'archive.ubuntu:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

Any ideas about "screen-black-out" issue?

thanks

---

### Post by ibjsb4 on 2013-02-05
The above says that you upgraded from 8o4 to 12o4.

How did you do this version upgrade?

You have to remove all Hardy (8o4) sources from the sources list or this will never work.

---

### Post by Cheesemill on 2013-02-05
Are you sure about all of your information?

12.04.2 hasn't been released yet.

It won't be available until the 14th of February.
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)

---

### Post by jomoyomo on 2013-02-05
> **Cheesemill said:**
> Are you sure about all of your information?

12.04.2 hasn't been released yet.

It won't be available until the 14th of February.
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)

Dunno why,
it says like this:
$ cat /etc/issue
Ubuntu 12.04.2 LTS \n \l

---

### Post by ibjsb4 on 2013-02-05
> **jomoyomo said:**
> Dunno why,
it says like this:
$ cat /etc/issue
Ubuntu 12.04.2 LTS \n \l

I seen another post where upgrading to the 3.5 kernel will do this.

---

