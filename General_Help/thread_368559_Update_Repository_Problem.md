---
title: "Update Repository Problem"
date: 2007-02-23
forum: General Help
---

### Post by rwhillman on 2007-02-23
I am unable to update through update manager.  I get this message --
Could not download all repository indexes

When I run sudo apt-get update, same result -- I think this is the part that may be the problem

Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/Release.gpg](http://www.getautomatix.com/apt/dists/edgy/Release.gpg)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (82.165.193.29). - connect (111 Connection refused)
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2](http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (82.165.193.29). - connect (111 Connection refused)

Help appreciated.

---

### Post by r4ik on 2007-02-23
Try this (Dapper link on page)

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

copy and paste :)

---

### Post by Nythain on 2007-02-23
failing to fetch updates from any given server shouldnt affect your ability to update anything except whats on that server, wich you're box wouldnt know had a new version anyway cause it couldnt get teh list from the server you couldnt connect to... so if automatix is particulary what you are trying to upgrade, then yes, that would be causing your problem... but any software on any other repos should still be upgradable...

are there any more errors while you try to update, and have you run sudo apt-get upgrade after the sudo apt-get update

---

### Post by rwhillman on 2007-02-23
On the sudo apt-get upgrade, here is what I get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by rwhillman on 2007-02-23
I should add it seems to be related to getautomatix.

---

### Post by Nythain on 2007-02-23
what does your /etc/apt/sources.list file look like... did automatix remove all the repo entries with its own... in other words when you sudo apt-get update does it try to connect to any other repos besides the automatix???

if so, and apt-get upgrade says there's nothing to upgrade then you are good, minus a newer version of automatix wich last i hear recently was down for a bit

---

### Post by rwhillman on 2007-02-23
It does seem to be going to other repositories.  Here is the full response to update --

Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (82.165.193.29). - connect (111 Connection refused)
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (82.165.193.29). - connect (111 Connection refused)
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US             
Get:2 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US       
Get:5 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]                  
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US       
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US                
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                          
Get:8 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg [191B]                          
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                           
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release                                       
Get:9 [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy Release.gpg [191B]             
Ign [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Translation-en_US         
Ign [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Translation-en_US         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources                         
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages              
Hit [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources               
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages                         
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources               
Hit [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Packages
Fetched 199B in 1s (126B/s)
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/Release.gpg](http://www.getautomatix.com/apt/dists/edgy/Release.gpg)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (82.165.193.29). - connect (111 Connection refused)
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2](http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (82.165.193.29). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Nythain on 2007-02-23
ok, thats what i was hoping for... that error/warning message was just letting you know it couldnt get a new package list from automatix... the rest of your system should be fully upgraded since sudo apt-get upgrade returned no new upgrades to install or remove...

if you get that error any more, pay attention to the repo, and wether or not the other repos worked fine... like i said earlier, automatix is down atm i heard in another post... so i wouldnt fret, you are in the clear

---

### Post by rwhillman on 2007-02-23
Thanks for the help and assurance.   Much appreciated.

---

