---
title: "[SOLVED] Some repository error-sudo apt-get update fails"
date: 2008-04-01
forum: General Help
---

### Post by hunter_te on 2008-04-01
How do you go about solving such update problems?

Please Help 



```

ABC@The-C2D-Machine:~$ sudo apt-get update
[sudo] password for ABC:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Ign http://ppa.launchpad.net gutsy/main Translation-en_IN                      
Get:1 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_IN               
Get:2 http://hendrik.kaju.pri.ee gutsy Release.gpg [189B]                      
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Translation-en_IN              
Get:3 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/main Translation-en_IN                     
Get:4 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_IN       
Hit http://ppa.launchpad.net gutsy Release                                     
Hit http://archive.canonical.com gutsy Release                                 
Ign http://archive.ubuntu.com gutsy/universe Translation-en_IN                 
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_IN               
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_IN               
Get:5 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]               
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_IN         
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_IN             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_IN           
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_IN     
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_IN     
Hit http://security.ubuntu.com gutsy-security Release                          
Ign http://ppa.launchpad.net gutsy/main Packages                               
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_IN       
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_IN       
Hit http://archive.ubuntu.com gutsy Release                                    
Hit http://archive.canonical.com gutsy/partner Packages                        
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://archive.ubuntu.com gutsy-updates Release                            
Ign http://ppa.launchpad.net gutsy/main Sources                                
Hit http://archive.canonical.com gutsy/partner Sources                         
Hit http://hendrik.kaju.pri.ee gutsy Release                                   
Err http://hendrik.kaju.pri.ee gutsy Release                                   
  
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://archive.ubuntu.com gutsy/main Packages                              
Hit http://archive.ubuntu.com gutsy/universe Packages                          
Hit http://archive.ubuntu.com gutsy/restricted Packages                      
Hit http://ppa.launchpad.net gutsy/main Packages                               
Hit http://archive.ubuntu.com gutsy/multiverse Packages                        
Hit http://archive.ubuntu.com gutsy-updates/universe Packages                  
Hit http://archive.ubuntu.com gutsy-updates/main Packages                      
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages                
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages                
Hit http://ppa.launchpad.net gutsy/main Sources                                
[B]Get:6 http://hendrik.kaju.pri.ee gutsy Release [6702B]                         
Ign http://hendrik.kaju.pri.ee gutsy Release                                   
Ign http://hendrik.kaju.pri.ee gutsy/screenlets Packages                       
Err http://hendrik.kaju.pri.ee gutsy/screenlets Packages                       
  404 Not Found
Fetched 6895B in 1m17s (89B/s)
Failed to fetch http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
W: GPG error: http://hendrik.kaju.pri.ee gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/B]
ABC@The-C2D-Machine:~$ 

```

:confused:

---

### Post by JLB on 2008-04-01
[http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) is the problem. Comment it out in your /etc/apt/sources.lst file or uncheck it in "repositories" menu in synaptic. You should doublecheck the repository information from that site. You also appear to need to import their gpg signature as well.

---

### Post by hunter_te on 2008-04-01
Thanks JLB.

I un-ticked that repository. Looks like something for the screenlet. Not so important anyways. and dont understand that site's language.

---

### Post by JLB on 2008-04-01
Glad you got it sorted out.

---

