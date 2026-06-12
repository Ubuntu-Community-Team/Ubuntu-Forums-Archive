---
title: "Sweet Home 3D failed to install"
date: 2012-11-12
forum: General Help
---

### Post by lumaja on 2012-11-12
Install from Ubuntu Question #206121   




___@___-G41M-Combo:~$ sudo add-apt-repository ppa:upubuntu-com/graphics 
 [sudo] password for luis:  
 You are about to add the following PPA to your system: 
   
  More info: [https://launchpad.net/~upubuntu-com/+archive/graphics](https://launchpad.net/~upubuntu-com/+archive/graphics) 
 Press [ENTER] to continue or ctrl-c to cancel adding it 
  
 gpg: keyring `/tmp/tmpyoytAp/secring.gpg' created 
 gpg: keyring `/tmp/tmpyoytAp/pubring.gpg' created 
 gpg: requesting key E06E6293 from hkp server keyserver.ubuntu.com 
 gpg: /tmp/tmpyoytAp/trustdb.gpg: trustdb created 
 gpg: key E06E6293: public key "Launchpad PPA for upubuntu.com" imported 
 gpg: Total number processed: 1 
 gpg:               imported: 1  (RSA: 1) 
 OK 
 ___@___-G41M-Combo:~$ sudo apt-get update 
 Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise InRelease 
 Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates InRelease                      
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release.gpg                            
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release.gpg                    
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                              
 Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                       
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                       
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release                                
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release                        
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                            
 Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                     
 Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                       
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Sources                       
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe i386 Packages                 
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe TranslationIndex              
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Sources               
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe i386 Packages         
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe TranslationIndex      
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                
 Hit [http://dl.google.com](http://dl.google.com) stable Release                                         
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11,9 kB]                        
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Translation-en                
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                         
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Translation-en        
 Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise InRelease                            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                  
 Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                              
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources                
 Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib i386 Packages                
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                    
 Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                           
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages          
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex       
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib TranslationIndex             
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [7 486 B]                   
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [9 829 B]             
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                      
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_ZA              
 Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_ZA                          
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                 
 Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                             
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en_ZA            
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en               
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_ZA                     
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                        
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
   404  Not Found 
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
   404  Not Found 
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Fetched 29,3 kB in 10s (2 823 B/s)                                              
 W: Failed to fetch [http://ppa.launchpad.net/atarero/atareo/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/atarero/atareo/ubuntu/dists/precise/main/source/Sources)  404  Not Found 
  
 W: Failed to fetch [http://ppa.launchpad.net/atarero/atareo/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/atarero/atareo/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found 
  
 E: Some index files failed to download. They have been ignored, or old ones used instead. 
 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) 
 E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 
 ____@____-G41M-Combo:~$ sudo apt-get install sweethome-3d 
 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) 
 E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 
 ____@____-G41M-Combo:~$

---

### Post by dino99 on 2012-11-12
i propose you make some cleaning into your repos, its the mess there.
if you are running precise, why the oneiric repo ? and the google ones ?

---

### Post by lumaja on 2012-11-12
Thank you for a quick response.
 I am running Precise Pangolin.
 Still very new with Ubuntu and this is above me
 repos is this for Repository? And don’t know about the others.
 Please help me to fix this.

---

### Post by lumaja on 2012-11-15
n Repositories unmarked the references to oneiric and google and tried to install Sweet Home again.
 It stopped with “You may want to run apt-get update to correct these problems ”, which I did but generate other problems and as I am not sure about this I am contacting you again.
 Terminal:
 

 luis@luis-G41M-Combo:~$ sudo add-apt-repository ppa:upubuntu-com/graphics  
 [sudo] password for luis:  
 You are about to add the following PPA to your system:  
   
  More info: [https://launchpad.net/~upubuntu-com/+archive/graphics](https://launchpad.net/~upubuntu-com/+archive/graphics)  
 Press [ENTER] to continue or ctrl-c to cancel adding it  
 

 gpg: keyring `/tmp/tmp6zxyBo/secring.gpg' created  
 gpg: keyring `/tmp/tmp6zxyBo/pubring.gpg' created  
 gpg: requesting key E06E6293 from hkp server keyserver.ubuntu.com  
 gpg: /tmp/tmp6zxyBo/trustdb.gpg: trustdb created  
 gpg: key E06E6293: public key "Launchpad PPA for upubuntu.com" imported  
 gpg: Total number processed: 1  
 gpg:               imported: 1  (RSA: 1)  
 OK  
 luis@luis-G41M-Combo:~$ sudo apt-get update  
 Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise InRelease  
 Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates InRelease                      
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release.gpg                            
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                              
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                  
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release.gpg                    
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                       
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release                                
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                            
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release                        
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                
 Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise InRelease                            
 Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]           
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                  
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Sources                       
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe i386 Packages                 
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe TranslationIndex              
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Sources               
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe i386 Packages         
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe TranslationIndex      
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                    
 Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49,6 kB]             
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Translation-en                
 Hit [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib i386 Packages                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                  
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                               
 Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Translation-en        
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex               
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib TranslationIndex             
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                         
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                      
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [16,9 kB]    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [56,1 kB]  
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex       
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en         
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_ZA              
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_ZA            
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en_ZA            
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                        
 Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en               
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
   404  Not Found  
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
   404  Not Found  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Fetched 123 kB in 11s (10,7 kB/s)                                               
 W: Failed to fetch [http://ppa.launchpad.net/atarero/atareo/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/atarero/atareo/ubuntu/dists/precise/main/source/Sources)  404  Not Found  
 

 W: Failed to fetch [http://ppa.launchpad.net/atarero/atareo/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/atarero/atareo/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found  
 

 E: Some index files failed to download. They have been ignored, or old ones used instead.  
 luis@luis-G41M-Combo:~$ sudo apt-get install sweethome-3d  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Some packages could not be installed. This may mean that you have  
 requested an impossible situation or if you are using the unstable  
 distribution that some required packages have not yet been created  
 or been moved out of Incoming.  
 The following information may help to resolve the situation:  
   
 The following packages have unmet dependencies:  
  sweethome-3d : Depends: java-wrappers but it is not installable  
                 Depends: libfreehep-graphicsio-svg-java but it is not going to be installed  
                 Depends: libbatik-java but it is not installable  
 W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages) 
 W: You may want to run apt-get update to correct these problems  
 E: Unable to correct problems, you have held broken packages.  
 luis@luis-G41M-Combo:~$ apt-get  
 apt 0.8.16~exp12ubuntu10.3 for i386 compiled on Aug 20 2012 22:34:51  
 Usage: apt-get [options] command  
        apt-get [options] install|remove pkg1 [pkg2 ...]  
        apt-get [options] source pkg1 [pkg2 ...]  
 

 apt-get is a simple command line interface for downloading and  
 installing packages. The most frequently used commands are update  
 and install.  
 

 Commands:  
    update - Retrieve new lists of packages  
    upgrade - Perform an upgrade  
    install - Install new packages (pkg is libc6 not libc6.deb)  
    remove - Remove packages  
    autoremove - Remove automatically all unused packages  
    purge - Remove packages and config files  
    source - Download source archives  
    build-dep - Configure build-dependencies for source packages  
    dist-upgrade - Distribution upgrade, see apt-get(8)  
    dselect-upgrade - Follow dselect selections  
    clean - Erase downloaded archive files  
    autoclean - Erase old downloaded archive files  
    check - Verify that there are no broken dependencies  
    changelog - Download and display the changelog for the given package  
    download - Download the binary package into the current directory  
 

 Options:  
   -h  This help text.  
   -q  Loggable output - no progress indicator  
   -qq No output except for errors  
   -d  Download only - do NOT install or unpack archives  
   -s  No-act. Perform ordering simulation  
   -y  Assume Yes to all queries and do not prompt  
   -f  Attempt to correct a system with broken dependencies in place  
   -m  Attempt to continue if archives are unlocatable  
   -u  Show a list of upgraded packages as well  
   -b  Build the source package after fetching it  
   -V  Show verbose version numbers  
   -c=? Read this configuration file  
   -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp  
 See the apt-get(8), sources.list(5) and apt.conf(5) manual  
 pages for more information and options. 
                        This APT has Super Cow Powers.  
 luis@luis-G41M-Combo:~$

---

### Post by slickymaster on 2012-11-15
It looks like you have severall problems with the packages, it has unfulfilled dependancies.

Try to contact the manager of that package source because there are at list two URLs poiting to nowhere.

---

### Post by lumaja on 2012-11-17
Contact Sweet Home and this is they answer.
    
 When using Ubuntu 12.04 you should do the following:
- download SH3D 3.7 using the green button [here]("http://www.sweethome3d.com/download.jsp") or version 3.6 [here]("http://sourceforge.net/projects/sweethome3d/files/SweetHome3D/SweetHome3D-3.6/").
- unzip the downloaded file.
- drag the unzipped directory where you want it.
- right-click the file ***SweetHome3D***, choose *Properties*, then *Permissions* and make sure that you *Allow executing file as program*.
 

 On downloaded page there is a warning : I**f you don't want to care about the Java configuration of your system.**
 

 File name is:**SweetHome3D-3.7-linux-x86.tgz**
 

 I downloaded the file but dint install I need advise.
 1 – Is there any issues with Java on my system? And is it worth to     have it or possible many troubles ahead.
 2 – is the file above the correct one.
 3 – there others files, one is for Linux.
 

 

             [SIZE=4]**Launch Sweet Home **[/SIZE] 
 

 

                                                               Under Linux:
                                           Choose to open the SweetHome3D.jnlp                 downloaded file with javaws program                 that you'll find in the bin                 directory of the JRE (Java Runtime Environment).
                             Again which of the two should install.
 I would like to have this application on my computer I depreciate very much to achieve this.
 

 Thank you

---

### Post by stinkeye on 2012-11-17
**@ lumaja**
In Quantal, I can install sweethome3d without adding any 3rd party repositories.
Think it's in the universe repository for precise as well.
Why do you want to add the upubuntu-com/graphics ppa?

As sweethome3d is a java app it will install openjdk java as a dependency if you don't have java installed.
All I had to do was run...
```
sudo apt-get install sweethome3d
``` 

If you find it too complicated to fix your sources list and dependency issues,
you might find it easier to backup your personal files and do a fresh Ubuntu install.

PS: When posting terminal output or code please use the code button.
Highlight your code then click the # button.
or
Press the # button and then paste between the code blocks.
eg [ code][COLOR="Magenta"]paste here[/COLOR][ /code]
[ATTACH]227306[/ATTACH] <----pic

---

### Post by slickymaster on 2012-11-17
You should take a look at [Sweet Home 3D FAQ's webpage]("http://www.sweethome3d.com/faq.jsp#installation") because there are several answers addressing your doubts, but one thing seems to be clear, you must have java installed in your system in order to run Sweet Home 3D.

In order to know if you have it installed just open your terminal and type **java -version** or just **javac**, if it returns something, then you have java installed.
Otherwise, there is also the possibility that the path variables do not contain the java path. So use **locate jdk** or **locate java** to see if you have the java binary. Don't forget to run **updatedb** if you are using locate for the first time.

---

### Post by lumaja on 2012-11-18
[SIZE=3]Thank you for your response[/SIZE]

  [SIZE=4]**To Slickymaster**[/SIZE]
  [SIZE=3]Checking for java if is installed:[/SIZE]
 luis@luis-G41M-Combo:~$ javac  
 The program 'javac' can be found in the following packages:  
  * default-jdk  
  * ecj  
  * gcj-4.6-jdk  
  * openjdk-6-jdk  
  * gcj-4.5-jdk  
  * openjdk-7-jdk  
 Try: sudo apt-get install <selected package>  
 luis@luis-G41M-Combo:~$ java -version  
 java version "1.6.0_24"  
 OpenJDK Runtime Environment (IcedTea6 1.11.4) (6b24-1.11.4-1ubuntu0.12.04.1)  
 OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)  
  [SIZE=3]luis@luis-G41M-Combo:~$ [/SIZE] 
   [SIZE=3]Is this the correct java?[/SIZE]
  

  

  [SIZE=3]To [SIZE=4]**Stinkeye**[/SIZE][/SIZE]
  [SIZE=3][SIZE=4]I went[/SIZE][SIZE=4]to Quantal site search for SweetHome but I didn’t saw the app to download, only a reference.[/SIZE][/SIZE]
  [SIZE=4]Looking for a site to download SweetHome I found upUbuntu with explanation how to download and the reference to [/SIZE][SIZE=4]graphics ppa[/SIZE][SIZE=4].[/SIZE]
  [SIZE=4]The “[/SIZE][SIZE=4]Press the [/SIZE][SIZE=4]**# button**[/SIZE][SIZE=4] and then paste between the code blocks” didn’t understand, the terminal output follows:[/SIZE]
  

 luis@luis-G41M-Combo:~$ sudo apt-get install sweethome3d  
 [sudo] password for luis:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Some packages could not be installed. This may mean that you have  
 requested an impossible situation or if you are using the unstable  
 distribution that some required packages have not yet been created  
 or been moved out of Incoming.  
 The following information may help to resolve the situation:  
 

 The following packages have unmet dependencies:  
  sweethome3d : Depends: java-wrappers but it is not installable  
                Depends: libfreehep-graphicsio-svg-java but it is not going to be installed  
                Depends: libbatik-java but it is not installable  
 W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages) 
 W: You may want to run apt-get update to correct these problems  
 E: Unable to correct problems, you have held broken packages.  
  [SIZE=4]luis@luis-G41M-Combo:~$ [/SIZE]

---

### Post by stinkeye on 2012-11-18
> **lumaja said:**
> [SIZE=3]Thank you for your response[/SIZE]

  
  [SIZE=3]To [SIZE=4]**Stinkeye**[/SIZE][/SIZE]
  [SIZE=3][SIZE=4]I went[/SIZE][SIZE=4]to Quantal site search for SweetHome but I didn&#8217;t saw the app to download, only a reference.[/SIZE][/SIZE]
  [SIZE=4]Looking for a site to download SweetHome I found upUbuntu with explanation how to download and the reference to [/SIZE][SIZE=4]graphics ppa[/SIZE][SIZE=4].[/SIZE]
  [SIZE=4]The &#8220;[/SIZE][SIZE=4]Press the [/SIZE][SIZE=4]**# button**[/SIZE][SIZE=4] and then paste between the code blocks&#8221; didn&#8217;t understand, the terminal output follows:[/SIZE]
  

 luis@luis-G41M-Combo:~$ sudo apt-get install sweethome3d  
 [sudo] password for luis:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Some packages could not be installed. This may mean that you have  
 requested an impossible situation or if you are using the unstable  
 distribution that some required packages have not yet been created  
 or been moved out of Incoming.  
 The following information may help to resolve the situation:  
 

 The following packages have unmet dependencies:  
  sweethome3d : Depends: java-wrappers but it is not installable  
                Depends: libfreehep-graphicsio-svg-java but it is not going to be installed  
                Depends: libbatik-java but it is not installable  
 W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages) 
 W: You may want to run apt-get update to correct these problems  
 E: Unable to correct problems, you have held broken packages.  
  [SIZE=4]luis@luis-G41M-Combo:~$ [/SIZE]

What I'm saying is you should be able to install **sweethome3d** by searching
in the software centre.
It is in the universe repository which is enabled by default.
Just did a quick layout and seems to work fine.
[ATTACH]227323[/ATTACH]  [ATTACH]227324[/ATTACH]  [ATTACH]227329[/ATTACH]

It won't install at the moment because of the mess with your sources list.
So you can bugga around trying to fix your packages and sources or
do a fresh install of Ubuntu and just install from the software centre.
You can't just add sources willy-nilly, as they may upgrade packages 
where something you want to install may not work with the updated packages. 

After inserting terminal output in a forum thread,
highlight what you pasted with left mouse and click the # symbol.
[ATTACH]227325[/ATTACH]

---

### Post by slickymaster on 2012-11-18
[SIZE=4]**To Slickymaster**[/SIZE]
  [SIZE=3]Checking for java if is installed:[/SIZE]
 luis@luis-G41M-Combo:~$ javac  
 The program 'javac' can be found in the following packages:  
  * default-jdk  
  * ecj  
  * gcj-4.6-jdk  
  * openjdk-6-jdk  
  * gcj-4.5-jdk  
  * openjdk-7-jdk  
 Try: sudo apt-get install <selected package>  
 luis@luis-G41M-Combo:~$ java -version  
 java version "1.6.0_24"  
 OpenJDK Runtime Environment (IcedTea6 1.11.4) (6b24-1.11.4-1ubuntu0.12.04.1)  
 OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)  
  [SIZE=3]luis@luis-G41M-Combo:~$ [/SIZE] 
   [SIZE=3]Is this the correct java?[/SIZE]
  

  

Sweet Home 3D requires Java 1.5 at minimum to run properly and in your case you have 1.6.0_24, so that's not the problem.
I lean toward what Stinkeye says, your sources list seems to be a mess and you can try to fix your packages and sources, but I would advise against it.
Honestly, I think the best for you to do is to follow Stinkeye advice and do a fresh install of Ubuntu and just install Sweet Home 3D from the software center.

---

