---
title: "sudo apt-get update error"
date: 2014-02-27
forum: General Help
---

### Post by David_Dahan on 2014-02-27
Hi! I'm having some problems with the sudo apt-get update command. I am running Ubuntu 13.10
When I run the command it gives me the error
```

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I don't know how to fix this...

Here is the full result of the "sudo apt-get update" command

```

david@HP-G6:/$ sudo apt-get update
Ign http://mirrors.us.kernel.org saucy InRelease
Ign http://mirrors.us.kernel.org saucy-updates InRelease                                                                                                   
Ign http://mirrors.us.kernel.org saucy-backports InRelease                                                                                                 
Ign http://extras.ubuntu.com saucy InRelease                        
Ign http://archive.canonical.com saucy InRelease                     
Ign http://ppa.launchpad.net saucy InRelease                         
Ign http://mirrors.us.kernel.org saucy-security InRelease                                  
Hit http://mirrors.us.kernel.org saucy Release.gpg                                         
Hit http://mirrors.us.kernel.org saucy-updates Release.gpg                                 
Hit http://extras.ubuntu.com saucy Release.gpg                                             
Hit http://archive.canonical.com saucy Release.gpg                                         
Ign http://ppa.launchpad.net saucy InRelease                         
Hit http://mirrors.us.kernel.org saucy-backports Release.gpg                               
Hit http://mirrors.us.kernel.org saucy-security Release.gpg                                
Hit http://extras.ubuntu.com saucy Release                                                 
Hit http://archive.canonical.com saucy Release                                              
Ign http://ppa.launchpad.net saucy InRelease                         
Hit http://mirrors.us.kernel.org saucy Release                                              
Hit http://mirrors.us.kernel.org saucy-updates Release                                                            
Hit http://mirrors.us.kernel.org saucy-backports Release                                                          
Hit http://extras.ubuntu.com saucy/main Sources                                                                   
Ign http://ppa.launchpad.net saucy InRelease                                                                      
Hit http://archive.canonical.com saucy/partner Sources                                     
Hit http://mirrors.us.kernel.org saucy-security Release              
Hit http://mirrors.us.kernel.org saucy/main Sources                                                               
Hit http://extras.ubuntu.com saucy/main amd64 Packages                                     
Ign http://ppa.launchpad.net saucy InRelease                         
Hit http://mirrors.us.kernel.org saucy/restricted Sources                                  
Hit http://archive.canonical.com saucy/partner amd64 Packages                              
Hit http://mirrors.us.kernel.org saucy/universe Sources                                    
Hit http://extras.ubuntu.com saucy/main i386 Packages                
Hit http://mirrors.us.kernel.org saucy/multiverse Sources                                  
Ign http://ppa.launchpad.net saucy InRelease                                               
Hit http://archive.canonical.com saucy/partner i386 Packages                               
Hit http://mirrors.us.kernel.org saucy/main amd64 Packages           
Get:1 https://launchpad.net saucy InRelease [9,880 B]                                      
Ign http://ppa.launchpad.net saucy InRelease                                                                           
Hit http://mirrors.us.kernel.org saucy/restricted amd64 Packages                                                       
Hit http://mirrors.us.kernel.org saucy/universe amd64 Packages                                         
Ign https://launchpad.net saucy InRelease                                                              
Hit http://ppa.launchpad.net saucy Release.gpg                                                         
Hit http://mirrors.us.kernel.org saucy/multiverse amd64 Packages                          
Hit http://mirrors.us.kernel.org saucy/main i386 Packages                                 
Hit http://mirrors.us.kernel.org saucy/restricted i386 Packages                           
Hit http://ppa.launchpad.net saucy Release.gpg                      
Hit http://mirrors.us.kernel.org saucy/universe i386 Packages       
Ign https://launchpad.net saucy Release.gpg                                               
Hit http://mirrors.us.kernel.org saucy/multiverse i386 Packages                           
Hit http://ppa.launchpad.net saucy Release.gpg                                            
Hit http://mirrors.us.kernel.org saucy/main Translation-en_CA                             
Hit http://mirrors.us.kernel.org saucy/main Translation-en                                
Hit http://ppa.launchpad.net saucy Release.gpg                                            
Hit http://mirrors.us.kernel.org saucy/multiverse Translation-en    
Ign https://launchpad.net saucy Release                             
Hit http://ppa.launchpad.net saucy Release.gpg                                            
Hit http://mirrors.us.kernel.org saucy/restricted Translation-en                          
Hit http://mirrors.us.kernel.org saucy/universe Translation-en_CA                         
Hit http://mirrors.us.kernel.org saucy/universe Translation-en                            
Hit http://ppa.launchpad.net saucy Release.gpg                      
Hit http://mirrors.us.kernel.org saucy-updates/main Sources                               
Hit http://mirrors.us.kernel.org saucy-updates/restricted Sources                         
Hit http://ppa.launchpad.net saucy Release.gpg                                            
Ign http://extras.ubuntu.com saucy/main Translation-en_CA                                 
Hit http://mirrors.us.kernel.org saucy-updates/universe Sources     
Hit http://ppa.launchpad.net saucy Release                          
Hit http://mirrors.us.kernel.org saucy-updates/multiverse Sources                                                
Ign http://archive.canonical.com saucy/partner Translation-en_CA                          
Ign http://extras.ubuntu.com saucy/main Translation-en              
Hit http://mirrors.us.kernel.org saucy-updates/main amd64 Packages  
Hit http://mirrors.us.kernel.org saucy-updates/restricted amd64 Packages
Hit http://ppa.launchpad.net saucy Release                          
Hit http://mirrors.us.kernel.org saucy-updates/universe amd64 Packages                     
Ign http://archive.canonical.com saucy/partner Translation-en       
Hit http://mirrors.us.kernel.org saucy-updates/multiverse amd64 Packages
Hit http://ppa.launchpad.net saucy Release    
Hit http://mirrors.us.kernel.org saucy-updates/main i386 Packages    
Hit http://mirrors.us.kernel.org saucy-updates/restricted i386 Packages
Hit http://mirrors.us.kernel.org saucy-updates/universe i386 Packages
Hit http://mirrors.us.kernel.org saucy-updates/multiverse i386 Packages
Hit http://mirrors.us.kernel.org saucy-updates/main Translation-en_CA
Hit http://ppa.launchpad.net saucy Release
Hit http://mirrors.us.kernel.org saucy-updates/main Translation-en   
Hit http://mirrors.us.kernel.org saucy-updates/multiverse Translation-en
Hit http://ppa.launchpad.net saucy Release    
Hit http://mirrors.us.kernel.org saucy-updates/restricted Translation-en
Hit http://ppa.launchpad.net saucy Release    
Hit http://mirrors.us.kernel.org saucy-updates/universe Translation-en
Hit http://ppa.launchpad.net saucy Release    
Hit http://mirrors.us.kernel.org saucy-backports/main Sources        
Hit http://mirrors.us.kernel.org saucy-backports/restricted Sources
Hit http://ppa.launchpad.net saucy/main Sources
Hit http://mirrors.us.kernel.org saucy-backports/universe Sources
Hit http://mirrors.us.kernel.org saucy-backports/multiverse Sources
Hit http://mirrors.us.kernel.org saucy-backports/main amd64 Packages
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Hit http://mirrors.us.kernel.org saucy-backports/restricted amd64 Packages
Hit http://mirrors.us.kernel.org saucy-backports/universe amd64 Packages
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://mirrors.us.kernel.org saucy-backports/multiverse amd64 Packages
Hit http://mirrors.us.kernel.org saucy-backports/main i386 Packages
Hit http://mirrors.us.kernel.org saucy-backports/restricted i386 Packages
Hit http://mirrors.us.kernel.org saucy-backports/universe i386 Packages
Hit http://mirrors.us.kernel.org saucy-backports/multiverse i386 Packages
Hit http://mirrors.us.kernel.org saucy-backports/main Translation-en
Hit http://ppa.launchpad.net saucy/main Sources
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Hit http://mirrors.us.kernel.org saucy-backports/multiverse Translation-en
Hit http://mirrors.us.kernel.org saucy-backports/restricted Translation-en
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://mirrors.us.kernel.org saucy-backports/universe Translation-en
Hit http://mirrors.us.kernel.org saucy-security/main Sources
Hit http://mirrors.us.kernel.org saucy-security/restricted Sources
Hit http://mirrors.us.kernel.org saucy-security/universe Sources
Hit http://mirrors.us.kernel.org saucy-security/multiverse Sources
Hit http://mirrors.us.kernel.org saucy-security/main amd64 Packages
Hit http://ppa.launchpad.net saucy/main Sources
Hit http://mirrors.us.kernel.org saucy-security/restricted amd64 Packages
Hit http://mirrors.us.kernel.org saucy-security/universe amd64 Packages
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Hit http://mirrors.us.kernel.org saucy-security/multiverse amd64 Packages
Hit http://mirrors.us.kernel.org saucy-security/main i386 Packages
Hit http://mirrors.us.kernel.org saucy-security/restricted i386 Packages
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://mirrors.us.kernel.org saucy-security/universe i386 Packages
Hit http://mirrors.us.kernel.org saucy-security/multiverse i386 Packages
Hit http://mirrors.us.kernel.org saucy-security/main Translation-en
Hit http://mirrors.us.kernel.org saucy-security/multiverse Translation-en
Hit http://mirrors.us.kernel.org saucy-security/restricted Translation-en
Hit http://ppa.launchpad.net saucy/main Sources
Hit http://mirrors.us.kernel.org saucy-security/universe Translation-en
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://ppa.launchpad.net saucy/main Sources
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://ppa.launchpad.net saucy/main Sources
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://ppa.launchpad.net saucy/main Sources
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Ign http://mirrors.us.kernel.org saucy/multiverse Translation-en_CA
Ign http://mirrors.us.kernel.org saucy/restricted Translation-en_CA
Hit http://ppa.launchpad.net saucy/main i386 Packages
Ign http://mirrors.us.kernel.org saucy-updates/multiverse Translation-en_CA
Ign http://mirrors.us.kernel.org saucy-updates/restricted Translation-en_CA
Ign http://mirrors.us.kernel.org saucy-updates/universe Translation-en_CA
Ign http://mirrors.us.kernel.org saucy-backports/main Translation-en_CA
Ign http://mirrors.us.kernel.org saucy-backports/multiverse Translation-en_CA
Ign http://mirrors.us.kernel.org saucy-backports/restricted Translation-en_CA
Ign http://mirrors.us.kernel.org saucy-backports/universe Translation-en_CA
Ign http://mirrors.us.kernel.org saucy-security/main Translation-en_CA
Ign http://mirrors.us.kernel.org saucy-security/multiverse Translation-en_CA
Ign http://mirrors.us.kernel.org saucy-security/restricted Translation-en_CA
Ign http://mirrors.us.kernel.org saucy-security/universe Translation-en_CA
Err https://launchpad.net saucy/main Sources
  
Err https://launchpad.net saucy/main amd64 Packages
  
Err https://launchpad.net saucy/main i386 Packages
  
Ign https://launchpad.net saucy/main Translation-en_CA
Ign https://launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_CA
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_CA
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_CA
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_CA
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_CA
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_CA
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_CA
Ign http://ppa.launchpad.net saucy/main Translation-en
W: Failed to fetch https://launchpad.net/~ubuntu-wine/+archive/ppa/dists/saucy/main/source/Sources  

W: Failed to fetch https://launchpad.net/~ubuntu-wine/+archive/ppa/dists/saucy/main/binary-amd64/Packages  

W: Failed to fetch https://launchpad.net/~ubuntu-wine/+archive/ppa/dists/saucy/main/binary-i386/Packages  

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by slickymaster on 2014-02-27
Please refer to these tutorials: [Error when updating packages?]("http://askubuntu.com/questions/65911/how-can-i-fix-a-404-error-when-updating-packages") and [“Failed to fetch” errors for PPAs…]("http://blog.launchpad.net/ppa/failed-to-fetch-errors-for-ppas")

---

