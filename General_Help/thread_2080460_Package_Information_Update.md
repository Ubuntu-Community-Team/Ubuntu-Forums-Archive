---
title: "Package Information Update"
date: 2012-11-04
forum: General Help
---

### Post by rbscairns on 2012-11-04
My Update Manager is telling me:

> This package information was last updated 46 days ago. Press the 'Check' button below to check for new software updated.

I then press the 'Check' button and a check is made. The result is there is no change in the "46 days ago" statement and "There are no updates to install."

I am trying to update my package information.

In terminal, I then did an apt-get update and the following was returned:

```
richard@richard:~$ sudo apt-get update
[sudo] password for richard: 
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://packages.medibuntu.org precise InRelease                            
Ign http://au.archive.ubuntu.com precise InRelease                             
Ign http://ppa.launchpad.net precise InRelease                             
Ign http://au.archive.ubuntu.com precise-updates InRelease                     
Ign http://au.archive.ubuntu.com precise-backports InRelease                   
Get:1 http://au.archive.ubuntu.com precise Release.gpg [198 B]                 
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://au.archive.ubuntu.com precise-updates Release.gpg                   
Ign http://ppa.launchpad.net precise InRelease                                 
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://security.ubuntu.com precise-security Release.gpg                    
Get:3 http://packages.medibuntu.org precise Release.gpg [198 B]                
Hit http://au.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://archive.canonical.com precise Release                               
Hit http://au.archive.ubuntu.com precise Release                               
Get:4 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Ign http://au.archive.ubuntu.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Err http://extras.ubuntu.com precise Release                                   
  
Hit http://security.ubuntu.com precise-security Release                        
Hit http://au.archive.ubuntu.com precise-updates Release                       
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://au.archive.ubuntu.com precise-backports Release                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:5 http://packages.medibuntu.org precise Release [6,851 B]                  
Ign http://au.archive.ubuntu.com precise/main Sources/DiffIndex                
Ign http://au.archive.ubuntu.com precise/restricted Sources/DiffIndex          
Ign http://au.archive.ubuntu.com precise/universe Sources/DiffIndex            
Ign http://au.archive.ubuntu.com precise/multiverse Sources/DiffIndex          
Ign http://au.archive.ubuntu.com precise/main i386 Packages/DiffIndex          
Hit http://security.ubuntu.com precise-security/main Sources                   
Ign http://au.archive.ubuntu.com precise/restricted i386 Packages/DiffIndex    
Ign http://au.archive.ubuntu.com precise/universe i386 Packages/DiffIndex      
Ign http://au.archive.ubuntu.com precise/multiverse i386 Packages/DiffIndex    
Hit http://au.archive.ubuntu.com precise/main TranslationIndex                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise Release                                   
Hit http://au.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://au.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://au.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://au.archive.ubuntu.com precise-updates/main Sources                  
Hit http://au.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://au.archive.ubuntu.com precise-updates/universe Sources              
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://ppa.launchpad.net precise Release                                   
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://au.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://au.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://au.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://au.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://au.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://au.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://au.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://au.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://au.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://au.archive.ubuntu.com precise-backports/main Sources                
Hit http://au.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://au.archive.ubuntu.com precise-backports/universe Sources            
Hit http://au.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://au.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://au.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Hit http://au.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://au.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://au.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://au.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://au.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://au.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://au.archive.ubuntu.com precise/main Sources                          
Hit http://au.archive.ubuntu.com precise/restricted Sources                    
Hit http://au.archive.ubuntu.com precise/universe Sources                      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://au.archive.ubuntu.com precise/multiverse Sources                    
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://au.archive.ubuntu.com precise/main i386 Packages                    
Hit http://au.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://au.archive.ubuntu.com precise/universe i386 Packages                
Hit http://au.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://au.archive.ubuntu.com precise/main Translation-en                   
Hit http://au.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://au.archive.ubuntu.com precise/restricted Translation-en             
Hit http://au.archive.ubuntu.com precise/universe Translation-en               
Hit http://au.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://au.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://au.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://au.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://au.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://au.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://au.archive.ubuntu.com precise-backports/restricted Translation-en   
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Hit http://au.archive.ubuntu.com precise-backports/universe Translation-en     
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Ign http://packages.medibuntu.org precise/free Translation-en
Ign http://packages.medibuntu.org precise/non-free Translation-en_US
Ign http://packages.medibuntu.org precise/non-free Translation-en
Fetched 7,635 B in 45s (166 B/s)
Reading package lists... Done
W: GPG error: http://au.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 83FBA1751378B444 Launchpad PPA for LibreOffice Packaging
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
richard@richard:~$
```

Where do I go from here to update my data package information?

---

### Post by ibjsb4 on 2012-11-04
BADSIG is fixable.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

