---
title: "Broken update Manager on Ubuntu 12.4"
date: 2014-01-24
forum: General Help
---

### Post by andyhunt26 on 2014-01-24
Hello I've had a lot of trouble with my update manager of late,and really love some help. One day, I went to update my system,and given an error mesage. I have taken a few steps to fix the problem. I have unchecked all 3rd party sources including Ubuntu parters  after trying update my system with the comman line using apt-get install upgrade. The out-put explaine that some of the dependaces where not meet,so I ran apt-get install upgrades -f,but it did nothing to currect the issuie. I then wanted to install the sybaptic updater tool to remove broken packages,but I did not install because of you guessed it missing dependant files. Below is a print of of my command promped.

```

Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [5,311 B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,797 B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [377 kB] 
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [4,811 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,178 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex [72 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [72 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex [73 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [334 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [135 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [94.5 kB]
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,650 B]
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:46 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:48 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Get:49 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [56.1 kB]
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg                               
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                     
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg                          
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_US                    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages/DiffIndex         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages/DiffIndex     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Fetched 3,004 kB in 1min 15s (39.5 kB/s)   
W: Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

```

anditsu@anditsu-Inspiron-1525:~$ sudo rm/ var/lib/dpkg/lock
sudo: rm/: command not found
anditsu@anditsu-Inspiron-1525:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libav-tools : Depends: libavcodec53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavcodec-extra-53 (< 4:0.8.8.99) but it is not installed
               Depends: libavdevice53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavdevice-extra-53 (< 4:0.8.8.99) but it is not installed
               Depends: libavfilter2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavfilter-extra-2 (< 4:0.8.8.99) but it is not installed
               Depends: libavformat53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavformat-extra-53 (< 4:0.8.8.99) but it is not installed
               Depends: libavutil51 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavutil-extra-51 (< 4:0.8.8.99) but it is not installed
               Depends: libpostproc52 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libpostproc-extra-52 (< 4:0.8.8.99) but it is not installed
               Depends: libswscale2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libswscale-extra-2 (< 4:0.8.8.99) but it is not installed
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try using -f.
anditsu@anditsu-Inspiron-1525:~$ apt-get update -f
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
anditsu@anditsu-Inspiron-1525:~$ sudo apt-get update -f
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                           
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                       
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                           
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                          
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_US                                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                            
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg                                      
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages/DiffIndex                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
W: Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

```

anditsu@anditsu-Inspiron-1525:~$ man apt-get
anditsu@anditsu-Inspiron-1525:~$ dbkg man
No command 'dbkg' found, did you mean:
 Command 'dpkg' from package 'dpkg' (main)
 dbkg: command not found
```

```

anditsu@anditsu-Inspiron-1525:~$ sudo apt-get upgrade
[sudo] password for anditsu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libav-tools : Depends: libavcodec53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavcodec-extra-53 (< 4:0.8.8.99) but it is not installed
               Depends: libavdevice53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavdevice-extra-53 (< 4:0.8.8.99) but it is not installed
               Depends: libavfilter2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavfilter-extra-2 (< 4:0.8.8.99) but it is not installed
               Depends: libavformat53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavformat-extra-53 (< 4:0.8.8.99) but it is not installed
               Depends: libavutil51 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavutil-extra-51 (< 4:0.8.8.99) but it is not installed
               Depends: libpostproc52 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libpostproc-extra-52 (< 4:0.8.8.99) but it is not installed
               Depends: libswscale2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libswscale-extra-2 (< 4:0.8.8.99) but it is not installed
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try using -f.
anditsu@anditsu-Inspiron-1525:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
anditsu@anditsu-Inspiron-1525:~$ apt-get dist-upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
anditsu@anditsu-Inspiron-1525:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libav-tools : Depends: libavcodec53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavcodec-extra-53 (< 4:0.8.8.99) but it is not installed
               Depends: libavdevice53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavdevice-extra-53 (< 4:0.8.8.99) but it is not installed
               Depends: libavfilter2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavfilter-extra-2 (< 4:0.8.8.99) but it is not installed
               Depends: libavformat53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavformat-extra-53 (< 4:0.8.8.99) but it is not installed
               Depends: libavutil51 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavutil-extra-51 (< 4:0.8.8.99) but it is not installed
               Depends: libpostproc52 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libpostproc-extra-52 (< 4:0.8.8.99) but it is not installed
               Depends: libswscale2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libswscale-extra-2 (< 4:0.8.8.99) but it is not installed
E: Unmet dependencies. Try using -f.

```
```

anditsu@anditsu-Inspiron-1525:~$ synaptic package manager
The program 'synaptic' is currently not installed.  You can install it by typing:
sudo apt-get install synaptic

```
```

anditsu@anditsu-Inspiron-1525:~$ sudo apt-get install synaptic
[sudo] password for anditsu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libav-tools : Depends: libavcodec53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavcodec-extra-53 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libavdevice53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavdevice-extra-53 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libavfilter2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavfilter-extra-2 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libavformat53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavformat-extra-53 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libavutil51 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavutil-extra-51 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libpostproc52 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libpostproc-extra-52 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libswscale2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libswscale-extra-2 (< 4:0.8.8.99) but it is not going to be installed
 synaptic : Depends: libept1.4.12 but it is not going to be installed
            Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
anditsu@anditsu-Inspiron-1525:~$ sudo apt-get install --reinstall update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libav-tools : Depends: libavcodec53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavcodec-extra-53 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libavdevice53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavdevice-extra-53 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libavfilter2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavfilter-extra-2 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libavformat53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavformat-extra-53 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libavutil51 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavutil-extra-51 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libpostproc52 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libpostproc-extra-52 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libswscale2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libswscale-extra-2 (< 4:0.8.8.99) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

anditsu@anditsu-Inspiron-1525:~$ sudo apt-get upgrade
[sudo] password for anditsu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libav-tools : Depends: libavcodec53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavcodec-extra-53 (< 4:0.8.8.99) but it is not installed
               Depends: libavdevice53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavdevice-extra-53 (< 4:0.8.8.99) but it is not installed
               Depends: libavfilter2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavfilter-extra-2 (< 4:0.8.8.99) but it is not installed
               Depends: libavformat53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavformat-extra-53 (< 4:0.8.8.99) but it is not installed
               Depends: libavutil51 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libavutil-extra-51 (< 4:0.8.8.99) but it is not installed
               Depends: libpostproc52 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libpostproc-extra-52 (< 4:0.8.8.99) but it is not installed
               Depends: libswscale2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is installed or
                        libswscale-extra-2 (< 4:0.8.8.99) but it is not installed
E: Unmet dependencies. Try using -f.
anditsu@anditsu-Inspiron-1525:~$ apt-get install upgrade -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
anditsu@anditsu-Inspiron-1525:~$ sudo apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update

```

```

anditsu@anditsu-Inspiron-1525:~$ apt-get install upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
anditsu@anditsu-Inspiron-1525:~$ sudo apt-get install upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package upgrade
anditsu@anditsu-Inspiron-1525:~$ apt-get install -f

```

Thank you for your help!

---

### Post by gifford on 2014-01-24
From a brief look it seems many errors are related to the medibuntu repository which no longer exists.
Here is a link which explains what to do:[http://askubuntu.com/questions/356794/the-medibuntu-project-has-come-to-an-end-what-do-i-do-now](http://askubuntu.com/questions/356794/the-medibuntu-project-has-come-to-an-end-what-do-i-do-now)

---

### Post by andyhunt26 on 2014-01-24
I have also edited the souce list so that none ubuntu stuff was not on the list.

---

### Post by andyhunt26 on 2014-01-24
The web page suggest using the aptitude program. Upon running the suggested command purge the medibuntu influances, the out put said the program was not installed,so I tryed to install it with no luck. I was missing the files needed to do so. Here is the out put, I hope it can give you a better idea of the problem:

```

anditsu@anditsu-Inspiron-1525:~$ sudo rm /var/cache/apt/archives
[sudo] password for anditsu: 
rm: cannot remove `/var/cache/apt/archives': Is a directory
anditsu@anditsu-Inspiron-1525:~$ sudo aptitude purge medibuntu-keyring
[sudo] password for anditsu: 
Sorry, try again.
[sudo] password for anditsu: 
sudo: aptitude: command not found
anditsu@anditsu-Inspiron-1525:~$ aptaptitude purge medibuntu-keyring
aptaptitude: command not found
anditsu@anditsu-Inspiron-1525:~$ rm -f /etc/apt/sources.list.d/medibuntu.list
rm: cannot remove `/etc/apt/sources.list.d/medibuntu.list': Permission denied
anditsu@anditsu-Inspiron-1525:~$ aptitude purge medibuntu-keyring
The program 'aptitude' is currently not installed.  You can install it by typing:
sudo apt-get install aptitude
anditsu@anditsu-Inspiron-1525:~$ rm -f /etc/apt/sources.list.d/medibuntu.list
rm: cannot remove `/etc/apt/sources.list.d/medibuntu.list': Permission denied
anditsu@anditsu-Inspiron-1525:~$ sudo apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 aptitude : Depends: libboost-iostreams1.46.1 (>= 1.46.1-1) but it is not going to be installed
            Depends: libcwidget3 but it is not going to be installed
            Depends: libept1.4.12 but it is not going to be installed
            Recommends: libparse-debianchangelog-perl but it is not going to be installed
 libav-tools : Depends: libavcodec53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavcodec-extra-53 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libavdevice53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavdevice-extra-53 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libavfilter2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavfilter-extra-2 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libavformat53 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavformat-extra-53 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libavutil51 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libavutil-extra-51 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libpostproc52 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libpostproc-extra-52 (< 4:0.8.8.99) but it is not going to be installed
               Depends: libswscale2 (< 4:0.8.8-99) but 4:0.8.9-0ubuntu0.12.04.1 is to be installed or
                        libswscale-extra-2 (< 4:0.8.8.99) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
anditsu@anditsu-Inspiron-1525:~$ apropose pgp

```

Thank for your help!

---

### Post by westie457 on 2014-01-24
The system is trying to tell you a solution.

[COLOR=#000000]E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

in the terminal try ```
sudo apt-get -f install
```

If there are any errors then try ```
sudo dpkg --configure -a
```

Let us know how it goes.

Thank you.[/COLOR]

---

### Post by andyhunt26 on 2014-01-24
I have ran the suggeed command given to me by the system **apt-get install -f  **it did not help. I just ran [COLOR=#000000]sudo dpkg --configure -a here is the out put: [COLOR=#000000]

```

anditsu@anditsu-Inspiron-1525:~$ sudo dpkg --configure -a
[sudo] password for anditsu: 
dpkg: dependency problems prevent configuration of libav-tools:
 libav-tools depends on libavcodec53 (<< 4:0.8.8-99) | libavcodec-extra-53 (<< 4:0.8.8.99); however:
  Version of libavcodec53 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libavcodec-extra-53 is not installed.
 libav-tools depends on libavdevice53 (<< 4:0.8.8-99) | libavdevice-extra-53 (<< 4:0.8.8.99); however:
  Version of libavdevice53 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libavdevice-extra-53 is not installed.
 libav-tools depends on libavfilter2 (<< 4:0.8.8-99) | libavfilter-extra-2 (<< 4:0.8.8.99); however:
  Version of libavfilter2 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libavfilter-extra-2 is not installed.
 libav-tools depends on libavformat53 (<< 4:0.8.8-99) | libavformat-extra-53 (<< 4:0.8.8.99); however:
  Version of libavformat53 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libavformat-extra-53 is not installed.
 libav-tools depends on libavutil51 (<< 4:0.8.8-99) | libavutil-extra-51 (<< 4:0.8.8.99); however:
  Version of libavutil51 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libavutil-extra-51 is not installed.
 libav-tools depends on libpostproc52 (<< 4:0.8.8-99) | libpostproc-extra-52 (<< 4:0.8.8.99); however:
  Version of libpostproc52 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libpostproc-extra-52 is not installed.
 libav-tools depends on libswscale2 (<< 4:0.8.8-99) | libswscale-extra-2 (<< 4:0.8.8.99); however:
  Version of libswscale2 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libswscale-extra-2 is not installed.
dpkg: error processing libav-tools (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libav-tools
anditsu@anditsu-Inspiron-1525:~$ 

```
[/COLOR][/COLOR]

---

### Post by andyhunt26 on 2014-01-24
I have ran the suggeed command given to me by the system **apt-get install -f  **it did not help. I just ran [COLOR=#000000]sudo dpkg --configure -a here is the out put: [COLOR=#000000]
```

anditsu@anditsu-Inspiron-1525:~$ sudo dpkg --configure -a
[sudo] password for anditsu: 
dpkg: dependency problems prevent configuration of libav-tools:
 libav-tools depends on libavcodec53 (<< 4:0.8.8-99) | libavcodec-extra-53 (<< 4:0.8.8.99); however:
  Version of libavcodec53 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libavcodec-extra-53 is not installed.
 libav-tools depends on libavdevice53 (<< 4:0.8.8-99) | libavdevice-extra-53 (<< 4:0.8.8.99); however:
  Version of libavdevice53 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libavdevice-extra-53 is not installed.
 libav-tools depends on libavfilter2 (<< 4:0.8.8-99) | libavfilter-extra-2 (<< 4:0.8.8.99); however:
  Version of libavfilter2 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libavfilter-extra-2 is not installed.
 libav-tools depends on libavformat53 (<< 4:0.8.8-99) | libavformat-extra-53 (<< 4:0.8.8.99); however:
  Version of libavformat53 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libavformat-extra-53 is not installed.
 libav-tools depends on libavutil51 (<< 4:0.8.8-99) | libavutil-extra-51 (<< 4:0.8.8.99); however:
  Version of libavutil51 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libavutil-extra-51 is not installed.
 libav-tools depends on libpostproc52 (<< 4:0.8.8-99) | libpostproc-extra-52 (<< 4:0.8.8.99); however:
  Version of libpostproc52 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libpostproc-extra-52 is not installed.
 libav-tools depends on libswscale2 (<< 4:0.8.8-99) | libswscale-extra-2 (<< 4:0.8.8.99); however:
  Version of libswscale2 on system is 4:0.8.9-0ubuntu0.12.04.1.
  Package libswscale-extra-2 is not installed.
dpkg: error processing libav-tools (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libav-tools
anditsu@anditsu-Inspiron-1525:~$ 

[/COLOR][/COLOR]
```

---

### Post by steeldriver on 2014-01-24
When you run commands, it's important to look at any errors before just blindly carrying on - for example

```

anditsu@anditsu-Inspiron-1525:~$ rm -f /etc/apt/sources.list.d/medibuntu.list
rm: cannot remove `/etc/apt/sources.list.d/medibuntu.list': Permission denied

```

is telling you that the command failed to remove the medibuntu.list file because you didn't use sudo

```

anditsu@anditsu-Inspiron-1525:~$ [COLOR=#0000ff]**sudo**[/COLOR] rm -f /etc/apt/sources.list.d/medibuntu.list

```

Until you successfully remove the medibuntu sources you are unlikely to be able to move forward

---

