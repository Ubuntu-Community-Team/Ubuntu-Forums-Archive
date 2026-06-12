---
title: "No updates for feisty since a week"
date: 2007-04-24
forum: General Help
---

### Post by vishnumrao on 2007-04-24
Hi all,

My feisty installation has not been finding any updates since a week. No updates have been released or am I missing something? Here is what my sudo apt-get update and sudo apt-get upgrade look like.

vishnumrao@vishnumrao-desktop:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1) feisty/restricted Translation-en_US                                                          
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]                                                                                                 
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                                                                                               
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                                                                                              
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                                                                                                        
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                                                                                                         
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_US                                                                                          
Ign [http://download.skype.com](http://download.skype.com) stable Release                                                                                       
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Packages                                                                             
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages                                                                             
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US                              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US                        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security Release.gpg [191B]                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Translation-en_US                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Translation-en_US                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Translation-en_US                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security Release                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Packages                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Packages              
Get:5 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release  
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]                                                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US                                                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US                                                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US                                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                                                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                                                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages                                                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages                                                                                          
Fetched 6B in 11s (1B/s)                                                                                                                                    
Reading package lists... Done
vishnumrao@vishnumrao-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
vishnumrao@vishnumrao-desktop:~$ 


Any help appreciated.

Thanks,
Vishnu Rao.

---

### Post by Kristopher on 2007-04-24
Yeah my feisty is the same, I guess since its not finding any that there are no updates...yet. Just give it some time.

---

### Post by jojo4u on 2007-04-24
No updates mean everything is fine, so be happy ;)

---

### Post by mdurham on 2007-04-24
> **jojo4u said:**
> No updates mean everything is fine, so be happy ;)

You **MUST** be joking! You are joking, right?

---

### Post by dcstar on 2007-04-24
> **mdurham said:**
> You **MUST** be joking! You are joking, right?

I'm waiting for something to fix whatever broke my OO 2.2 that was working ok on my Feisty Beta system up until a couple of weeks ago - when some sort of update has crippled it!

I'm using my 6.10 system until things settle down (and by the amount of posts in the forums, this could take a while........)

---

