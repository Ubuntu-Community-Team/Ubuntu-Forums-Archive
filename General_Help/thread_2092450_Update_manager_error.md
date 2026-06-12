---
title: "Update manager error"
date: 2012-12-07
forum: General Help
---

### Post by Philip Gray on 2012-12-07
Good evening

I have an extremely irritating problem. I installed some add-ons for Nautilus in 12.04LTS including scripts and emblems via a PPA (LP-PPA-nae-team). When I run 'Update Manager' they show up in the list of items to be installed. When I select the 'Update' button I get the error message as per the attached screenshot.  Ubuntu refuses to install these updates which I want. 

My question is:- How do I tell the system to install them. I want emblems and this is the only way that i could find to install them. Since the Nautilus team decided to drop an item that everybody loves and uses, this is the only way to get them back. I really do not understand the logic behind this move.

I am extremely irritated by this because Ubuntu is preventing me from doing what I want to do on my system. How do I get around this. My stand point is 'My computer  (Blikkie) does not tell me what I can and cannot do'. I am the boss. It does what I tell it to do. Not the other way around. Here it, (Blikkie), is telling me what I can and cannot do which is not acceptable. Classic case of the tail waging the dog.

I have checked the 'Settings' button options but I do not see any setting that can resolve this. Any help to resolve this will be greatly appreciated.

I Know I could do this via the terminal. This is not a viable option for me because the 12.04 modem manager does not work with my 3G SIM card. I am having to use the 11.04 modem manager. I have reported this to Launchpad. if I do the updates via the command prompt; firstly they do not always work and secondly; the 12.04 modem manager is reinstalled. I then have to remove it via synaptic and reinstall the 11.-4 via gdebi which is a real nuisance.

Regards
Philip

P.S. In South Africa Blikkie stands for Blikkbrein which is Afrikaans for Tin brain in English.  It is a fond term some of us use to refer to our PCs.

---

### Post by Kirk Schnable on 2012-12-07
This kind of thing can happen from time to time when you're using a third party PPA. 

Ubuntu's package manager uses a GPG key, which is like a unique signature, to identify a PPA server. Ideally, this prevents servers from impersonating a real repository software server. 

From time to time, these GPG keys may expire or be updated for some reason or another. When this happens, you have two possible ways to fix it, typically. 

1) Find the new GPG key for the repository, and install it using apt-key. 
2) Remove the PPA from your system. (Re-adding it with apt-add-repository will probably get the newest GPG key for you automatically). 

If you can provide me with some information on this PPA, such as your /etc/apt/sources.list file, or any relevant files in /etc/apt/sources.list.d/ I might be able to provide you with more specific advice on commands you could run to resolve the issue.

---

### Post by Jason80513 on 2012-12-07
If you are sure you trust that PPA, you can try running the update from the command line. 

sudo aptitude update
sudo aptitude full-upgrade

It should prompt you to ask you whether or not you trust the PPA, and then allow the update to continue.

---

### Post by Kirk Schnable on 2012-12-07
> **Jason80513 said:**
> If you are sure you trust that PPA, you can try running the update from the command line. 

sudo aptitude update
sudo aptitude full-upgrade

It should prompt you to ask you whether or not you trust the PPA, and then allow the update to continue.

For whatever reason, the original poster seems to want to only use the graphical package manager utilities. Doing what you've suggested is only a temporary solution to allow a package to be installed. The PPA keys should still be repaired, ideally.

---

### Post by Philip Gray on 2012-12-12
Hi Kirk Schnable

Thank you for yr reply. I have zipped the source.list file. When I tried to upload the source.list file I received an 'invalid file' response. The PPA name above the updates is: 'LP-PPA-nae-team'.


Hi Jason80513

The reason I do not want to do the updates via the terminal is because 12.04 will re-install the modem manager that comes with 12.04 . My 3G modem does not work with it. I have logged an incident with launchpad. To get an internet connection I have had to install modem package 'modemmanager_0.4+git.20110124t203624.00b6cce-2ubuntu1_i386.deb'.

Regards
Philip

---

### Post by Philip Gray on 2012-12-13
Hi Kirk Schnable

I went through my 'Software Sources' and found these two entries:
[http://ppa.launchpad.net/nae-team/ppa/ubuntu](http://ppa.launchpad.net/nae-team/ppa/ubuntu)
[http://ppa.launchpad.net/nae-team/ppa/ubuntu](http://ppa.launchpad.net/nae-team/ppa/ubuntu) (Source Code)

I also found this website:
[https://launchpad.net/~nae-team/+archive/ppa](https://launchpad.net/~nae-team/+archive/ppa)

Regards
Philip

---

### Post by Kirk Schnable on 2012-12-13
Unfortunately I've been very busy with finals week, so this is the first time I'm checking back with the forums.  I am on my tablet at the moment so I have no readily available means to open your compressed archive at the moment.

If you can paste me the complete output of
```
sudo apt-get update
```

I can probably use that to figure out which repository is not authenticated (and you can probably make a pretty good guess yourself).

---

### Post by Philip Gray on 2013-01-03
Hi Kirk Schnable

Happy new year. I hope your finals went well. My internet cap ran out last month. Here is the output from 'sudo apt-get update'

```
philip@philip-MS-7529:~$ sudo apt-get update
[sudo] password for philip: 
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise InRelease                             
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports InRelease                   
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://www.remastersys.com](http://www.remastersys.com) lucid/ InRelease                                
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://www.remastersys.com](http://www.remastersys.com) lucid/ Release.gpg                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Ign [http://www.remastersys.com](http://www.remastersys.com) lucid/ Release                                  
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports Release                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/main Sources                          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Sources                      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/restricted Sources            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11,9 kB]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Ign [http://www.remastersys.com](http://www.remastersys.com) lucid/ Packages/DiffIndex                       
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/main Translation-en_GB                
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/multiverse Translation-en_GB          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/restricted Translation-en_GB          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Translation-en_GB            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/main Translation-en_GB        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/restricted Translation-en_GB  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Translation-en_GB    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/restricted Translation-en   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports/universe Translation-en     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [13,0 kB]                  
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [8 167 B]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Err [http://www.remastersys.com](http://www.remastersys.com) lucid/ Sources                                  
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                    
Hit [http://www.remastersys.com](http://www.remastersys.com) lucid/ Packages                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Ign [http://www.remastersys.com](http://www.remastersys.com) lucid/ Translation-en_GB               
Ign [http://www.remastersys.com](http://www.remastersys.com) lucid/ Translation-en                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Fetched 33,9 kB in 23s (1 431 B/s)                                             
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8AA1FAA3F055C03
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0C14D55CE7242835
W: Failed to fetch [http://www.remastersys.com/repository/lucid/Sources](http://www.remastersys.com/repository/lucid/Sources)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
philip@philip-MS-7529:~$
``` 


Regards
Philip

---

### Post by Kirk Schnable on 2013-01-03
> **Philip Gray said:**
> Happy new year. I hope your finals went well.
Yep!  Thanks.


> **Philip Gray said:**
> My internet cap ran out last month.
Ouch...


> **Philip Gray said:**
>  ```
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8AA1FAA3F055C03
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0C14D55CE7242835
W: Failed to fetch [http://www.remastersys.com/repository/lucid/Sources](http://www.remastersys.com/repository/lucid/Sources)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
philip@philip-MS-7529:~$
```

It looks like we may have several issues.  

1. Your PPA GPG keys are not all matching up with what's on the servers.  Specifically, you're missing the key for "A8AA1FAA3F055C03" and "0C14D55CE7242835".

Try this...
```
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A8AA1FAA3F055C03
``````
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0C14D55CE7242835
``````
sudo apt-get update
```See if that gets rid of the GPG errors...  If you get any errors during the procedure and you're not sure how to troubleshoot them, paste them in a code box and I'd be happy to look over them.


2.  It looks like [http://www.remastersys.com/repository/lucid/Sources](http://www.remastersys.com/repository/lucid/Sources) is gone.  We will need to remove this software source from your system and then run **apt-get update**.  That will resolve the 404 error.

If you need help finding where this software source is, then give me the outputs of:
```
cat /etc/apt/sources.list
``````
ls -la /etc/apt/sources.list.d/
```If you think you can find and remove this source on your own, please feel free to give it a try.  Once the source is removed, run **apt-get update** again.

If you need help determining if your output is okay, or need any further assistance, please don't hesitate to ask!

---

