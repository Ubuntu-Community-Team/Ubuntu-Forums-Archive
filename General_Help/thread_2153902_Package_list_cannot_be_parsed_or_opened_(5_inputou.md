---
title: "Package list cannot be parsed or opened (5: input/output error)"
date: 2013-06-12
forum: General Help
---

### Post by patagriff on 2013-06-12
I cannot open the software center, update manager, synaptic package manager, or even run apt-get check to look for unresolved dependencies because my package list "cannot be parsed or opened". The error message was 'error opening the cache (E: read error- read (5: input/output error), E: The package lists or status file could not be parsed or opened.)' 

The notification from Update Manager said to run the Package Manager from the right click menu (I do not have this option, apparently) or apt-get in a terminal to see what is wrong. When I run apt-get, it attempts to load the package list, gets it 87% read, then stops and tells me it could not load the package list. I am assuming the package list has somehow become corrupted.

I have no idea how to resolve this problem. Any suggestions?

---

### Post by HiImTye on 2013-06-12
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
try refreshing the list```
sudo apt-get update
```then try again. pasting the entire output would be jore helpful. use [code] tags

---

### Post by abbadd0n1 on 2013-06-22
i have a similar problem, though mine produces an error while reading package list when using command 'sudo apt-get update'. 'sudo apt-get' clean didn't solve the issue either.


abbadd0n1@abbadd0n1-PT800-8237:~$ sudo apt-get clean
abbadd0n1@abbadd0n1-PT800-8237:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                      
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release.gpg          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release.gpg         
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages          
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US           
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Translation-en_US
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_raring_universe_binary-i386_Packages (1)
E: The package lists or status file could not be parsed or opened.
abbadd0n1@abbadd0n1-PT800-8237:~$ 

Any help would be appreciated...

---

