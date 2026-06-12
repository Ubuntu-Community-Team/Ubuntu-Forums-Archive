---
title: "apt-get update is not working"
date: 2015-07-03
forum: General Help
---

### Post by mrityunjay23 on 2015-07-03
After typing command apt-get update on terminal it gives follwing errors. Earlier my update was working. But from last some days it is not working.

```
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise Release.gpg
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates Release.gpg              
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports Release.gpg            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise Release                          
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates Release                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports Release                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/main TranslationIndex            
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/multiverse TranslationIndex      
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/restricted TranslationIndex      
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/universe TranslationIndex        
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
  407  Proxy Authentication Required
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
  407  Proxy Authentication Required
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
  407  Proxy Authentication Required
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_IN                    
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/main TranslationIndex    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/main TranslationIndex  
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security Release.gpg                
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security Release                    
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/main TranslationIndex      
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/multiverse TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/restricted TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/universe TranslationIndex  
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg                               
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                                   
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                     
Err [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
  407  Proxy Authentication Required
Err [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
  407  Proxy Authentication Required
Err [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
  407  Proxy Authentication Required
Err [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
  407  Proxy Authentication Required
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise/main amd64 Packages                       
  407  Proxy Authentication Required
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages                        
  407  Proxy Authentication Required
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_IN                    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex    
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
  407  Proxy Authentication Required
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources                         
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources             
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources             
  407  Proxy Authentication Required
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_IN   
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages            
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/main Sources     
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages        
  407  Proxy Authentication Required
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en      
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/restricted Sources
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/universe Sources
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/multiverse Sources
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages             
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/main amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages         
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/universe amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages       
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/main i386 Packages
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/universe i386 Packages
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/multiverse i386 Packages
  407  Proxy Authentication Required
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en_IN         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en_IN   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en_IN   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/main Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en        
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/multiverse Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/restricted Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/restricted Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/universe Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/universe Translation-en
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/main Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/restricted Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/universe Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/multiverse Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/main amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/universe amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/main i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/universe i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/multiverse i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/main Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/restricted Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/universe Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/multiverse Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/main amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/universe amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/main i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/universe i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/multiverse i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/main Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/restricted Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/universe Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/multiverse Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/main amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/universe amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/main i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/universe i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/multiverse i386 Packages
  407  Proxy Authentication Required
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/main Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/main Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/multiverse Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/multiverse Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/restricted Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/restricted Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/universe Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/universe Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/main Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/main Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/multiverse Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/multiverse Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/restricted Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/restricted Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/universe Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/universe Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/main Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/main Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/multiverse Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/multiverse Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/restricted Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/restricted Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/universe Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/universe Translation-en
W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://linux.dropbox.com/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/precise/main/binary-i386/Packages](http://linux.dropbox.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages)  407  Proxy Authentication Required

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by grahammechanical on 2015-07-03
First, would you please enclose that long printout in quote tags. Select the text and then click the icon of a text balloon. A mouse over of the icon says Wrap [QUOTE] tags around selected texts.

Second, the clue is in the message "Proxy Authentication Required." The system is setup to access the internet through a proxy server and you have not authenticated the connection to the proxy server.

[https://en.wikipedia.org/wiki/Proxy_server](https://en.wikipedia.org/wiki/Proxy_server)

Where are you connecting to the internet from? From your home where you have a router that connects to an Internet Service Provider (ISP) that you have a valid service agreement with? Or, some other place that does not allow machines on the network to have outside connections to the internet and world wide web?

Regards.

---

### Post by dino99 on 2015-07-03
use 'normal' ubuntu sources instead of those 'exotic' and 'untrusted' ones  [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by v3.xx on 2015-07-03
@ grahamm

+1

@dino

-99

---

### Post by Bucky Ball on 2015-07-03
@grahammechanical: [code] tags you mean, not quote tags, please. Thanks. :)

See last link in my signature. 

@OP: Suggest you get back to basics. As suggested, disable some of those added PPAs.

Open your Software & Updates> disable all the PPAs you have added manually (Other Software tab)> Update. All good? If so, add them back one by one and update after each until you get the error. That will find the culprit(s).

---

### Post by monkeybrain20122 on 2015-07-03
What are all these in.old.releases?

---

### Post by monkeybrain20122 on 2015-07-03
> **v3.xx said:**
> 

@dino

-99

+ 99, as in I agree with you 99 times. or totally -198 for dino. :)

---

### Post by QDR06VV9 on 2015-07-03
Sheesh! It is a tough crowd today.LOL

---

### Post by deadflowr on 2015-07-03
> **monkeybrain20122 said:**
> What are all these in.old.releases?

I'm thinking the OP did an EOL upgrade where as you change the sources.list for the dead release (probably 10.04 or 11.10) to the old-release repos, this then allows the user to grab the upgrade utilities to go to the next release.
But then the user needs to revert the sources.list back to normal repo.
That is a total guess, though.

The "in" part I think is the local mirror (india?)
the source should have been changed from in.archive but they only changed the archive part, so the were it should have changed from in.archive to only old-releases, it changed to in.old-releases.
I'm not even sure such an in.old-release repo even exists...

But aside from that the OP seems to be running through a proxy, which I've never used but have seen others do so with similar problems.


All that aside, the actual sources.list would be interesting to view.
Since it seems to have both regular sources (archive.ubuntu.com lines) and the old-releases sources (the in.old-releases lines)
me go ??? to that.

To the OP(original poster) please post the output for
```
cat /etc/apt/sources.list
```
It'll make things on that end a little clearer.

As for the proxy auth errors, that is something i know nothing about, other than it exists...

Hope this helps

---

### Post by mrityunjay23 on 2015-07-04
My Settings for ubuntu 12.04:
Synaptic package manager->Setting ->Repositories->ubuntu software center->Download from->Main server
~/.bash rc contains > export tag ttp_proxy=http://<usernam>:<password>@<proxy ip>:<port>
export http_proxy
/etc/apt/apt.conf contains follwing 
> Acquire::http:proxy "http://<proxy ip>:<port>/";
Acquire::https:proxy "https://<proxy ip>:<port>/";
out put of 
cat /etc/apt/sources.list

```

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise universe
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise universe
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise multiverse
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://in.old-releases.ubuntu.com/ubuntu/](http://in.old-releases.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise-security main restricted
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise-security universe
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise-security universe
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe main multiverse restricted #Added by software-properties

```

after typing apt-get install update

> 
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise Release.gpg
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security Release.gpg
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates Release.gpg              
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security Release                    
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports Release.gpg            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise Release                          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates Release                  
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports Release                
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/main TranslationIndex            
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/main TranslationIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/multiverse TranslationIndex      
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/multiverse TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/restricted TranslationIndex      
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/universe TranslationIndex  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/universe TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg                               
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
  407  Proxy Authentication Required
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
  407  Proxy Authentication Required
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
  407  Proxy Authentication Required
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
  407  Proxy Authentication Required
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                                   
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
  407  Proxy Authentication Required
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_IN             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_IN                    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/main TranslationIndex    
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/universe TranslationIndex
Err [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
  407  Proxy Authentication Required
Err [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
  407  Proxy Authentication Required
Err [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
  407  Proxy Authentication Required
Err [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
  407  Proxy Authentication Required
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise/main amd64 Packages                       
  407  Proxy Authentication Required
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages                        
  407  Proxy Authentication Required
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_IN                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/main TranslationIndex  
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                       
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/universe TranslationIndex
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/main Sources     
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/restricted Sources
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources               
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/universe Sources 
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                   
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/multiverse Sources
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources             
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/main amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources             
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages            
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/universe amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages        
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages      
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/main i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages      
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/universe i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
  407  Proxy Authentication Required
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/multiverse i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
  407  Proxy Authentication Required
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en_IN         
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/main Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/multiverse Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en_IN
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) precise-security/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_IN     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en        
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/main Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/restricted Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/universe Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/multiverse Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/main amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/universe amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/main i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/universe i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/multiverse i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/main Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/restricted Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/universe Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/multiverse Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/main amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/universe amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/main i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/universe i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/multiverse i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/main Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/restricted Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/universe Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/multiverse Sources
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/main amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/universe amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/main i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/universe i386 Packages
  407  Proxy Authentication Required
Err [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/multiverse i386 Packages
  407  Proxy Authentication Required
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/main Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/main Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/multiverse Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/multiverse Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/restricted Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/restricted Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/universe Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise/universe Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/main Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/main Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/multiverse Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/multiverse Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/restricted Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/restricted Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/universe Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-updates/universe Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/main Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/main Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/multiverse Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/multiverse Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/restricted Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/restricted Translation-en
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/universe Translation-en_IN
Ign [http://in.old-releases.ubuntu.com](http://in.old-releases.ubuntu.com) precise-backports/universe Translation-en
W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://linux.dropbox.com/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/precise/main/binary-i386/Packages](http://linux.dropbox.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by deadflowr on 2015-07-04
Well, I don't understand the bashrc line
I thought it was suppose to be 
```
http_proxy=yourproxeaddress:theportnumber
export http_proxy
```
instead of the above
```
export tag http_proxy=...
export http_proxy ...
```

But aside from that, which I say I am totaly unfamliar with,
The sources list file is mainly unusable.
Except for the last two section at the bottom.

Everything else which contains the in.old-release and old-release are pointless.
This is because 12.04 is still supported so the repos are not in the old-release archives yet.

And while the last sections will at least give you access to the correct archives, they are not complete as you do not have any proper access to the security repos.
And at this point, most updates will be through those security repos.

Thankfully there is an on-line website that helps with generating clean, proper sources.list
See: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
It is simple to use.
Just select the verison of Ubuntu and then the check the repos you want to add.
at the bottom click generate list, then a new window will open with the source.list, the easiest way is to highlight and copy the output.
Then open gedit (Ubuntu's text editor) and paste it into there.
save. (give it an easy filename to remember)
then in a terminal
```
sudo cp ~/easyfilename /etc/apt/sources.list
```
at least in that regard you will have a functional proper sources.list.

As for the proxy stuff, does any of this help?
[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

Hope this helps, or at least makes sense.

---

### Post by limbenjamin on 2015-07-04
> **mrityunjay23 said:**
> [COLOR=#000000]~/.bash rc contains
[/COLOR]
```
[COLOR=#000000][I]export tag ttp_proxy=http://<usernam>:<password>@<proxy ip>:<port>
export http_proxy
[/I][/COLOR]
```[COLOR=#000000]
[/COLOR]


Are you missing the "h" in "http_proxy"?

Do you require a proxy to access the internet?

---

