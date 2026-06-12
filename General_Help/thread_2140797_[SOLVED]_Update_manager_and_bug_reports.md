---
title: "[SOLVED] Update manager and bug reports"
date: 2013-04-30
forum: General Help
---

### Post by CK000 on 2013-04-30
Greatings,

Every time I run update manager I encounter the message:

System problem detected, would you like to send a bug report. When I send one I get the following message:

It seems you have modified the contents of "/etc/apt/apt.conf.d/10periodic".  Would you like to add the contents of it to your bug report?

What I want to know is what is this file for and why is it being modified without my informed consent?

Thank you in advance for any future assistance.

---

### Post by ibjsb4 on 2013-04-30
There's not much to go wrong with this file.

[ATTACH=CONFIG]242012[/ATTACH]

Whats yours look like?

---

### Post by matt_symes on 2013-04-30
Hi

Let's have a look at your system.

Open a terminal and type (or copy and paste)

```
cat /etc/apt/apt.conf.d/10periodic
```

Post the output back here.

Then type

```
sudo apt-get update
```

and post that back here. Enter your password. It will not be echoed to the screen.

And finally...

```
sudo apt-get upgrade
```

Post that as well. 

Please use code tags in your next post. Highlight the text and hit the # button in the bar above where you are typing your reply.

EDIT:

> What I want to know is what is this file for and why is it being modified without my informed consent?

You will have, at some point, given your informed consent. You may not have realised that the file was going to be updated though.

Kind regards

---

### Post by CK000 on 2013-04-30
Firstly I apologise for I do not understand how to use code tags, where is this # button on the forum? 

SOLVED I found out how to do it I will follow your instructions...

---

### Post by CK000 on 2013-04-30
```
ck@ck-eM250:~$ cat /etc/apt/apt.conf.d/10periodic
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "1";
ck@ck-eM250:~$ 


```

---

### Post by CK000 on 2013-04-30
```
ck@ck-eM250:~$ sudo apt-get update
[sudo] password for ck: 
Hit http://gb.archive.ubuntu.com precise Release.gpg
Hit http://archive.canonical.com precise Release.gpg                                     
Hit http://archive.canonical.com precise Release.gpg                                     
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]                    
Hit http://extras.ubuntu.com precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Get:2 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]                   
Hit http://packages.medibuntu.org precise Release.gpg                
Hit http://dl.google.com stable Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://gb.archive.ubuntu.com precise Release                                         
Hit http://archive.canonical.com precise Release                                         
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]                      
Hit http://extras.ubuntu.com precise Release                                             
Hit http://packages.medibuntu.org precise Release                                        
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://ppa.launchpad.net precise Release.gpg                                         
Hit http://dl.google.com stable Release.gpg                                              
Get:4 http://gb.archive.ubuntu.com precise-updates Release [49.6 kB]                     
Hit http://archive.canonical.com precise Release                                         
Hit http://ppa.launchpad.net precise Release                                             
Hit http://ppa.launchpad.net precise Release                                             
Hit http://ppa.launchpad.net precise Release                                             
Hit http://ppa.launchpad.net precise Release                                             
Hit http://ppa.launchpad.net precise Release                                             
Hit http://dl.google.com stable Release                                                  
Hit http://ppa.launchpad.net precise Release                                             
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                             
Hit http://ppa.launchpad.net precise Release                                             
Hit http://ppa.launchpad.net precise Release                                             
Hit http://ppa.launchpad.net precise Release                                             
Hit http://ppa.launchpad.net precise Release                                             
Hit http://dl.google.com stable Release                                                  
Hit http://ppa.launchpad.net precise Release                                             
Hit http://gb.archive.ubuntu.com precise/restricted Sources
Hit http://gb.archive.ubuntu.com precise/main Sources                  
Hit http://gb.archive.ubuntu.com precise/multiverse Sources            
Hit http://gb.archive.ubuntu.com precise/universe Sources
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex     
Hit http://archive.canonical.com precise/partner Sources               
Get:5 http://gb.archive.ubuntu.com precise/main Translation-en_GB [96.4 kB]              
Hit http://archive.canonical.com precise/partner i386 Packages                           
Ign http://archive.canonical.com precise/partner TranslationIndex                        
Hit http://extras.ubuntu.com precise/main Sources                                        
Hit http://extras.ubuntu.com precise/main i386 Packages                                  
Ign http://extras.ubuntu.com precise/main TranslationIndex                               
Get:6 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]           
Hit http://packages.medibuntu.org precise/free Sources                                   
Hit http://gb.archive.ubuntu.com precise/main Translation-en                             
Get:7 http://gb.archive.ubuntu.com precise/main Translation-en_AU [4,434 B]              
Hit http://gb.archive.ubuntu.com precise/main Translation-fa                             
Get:8 http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB [79.8 kB]        
Hit http://archive.canonical.com precise/partner Sources                                 
Hit http://archive.canonical.com precise/partner i386 Packages                           
Ign http://archive.canonical.com precise/partner TranslationIndex                        
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en                       
Get:9 http://gb.archive.ubuntu.com precise/multiverse Translation-en_AU [94.4 kB]        
Hit http://packages.medibuntu.org precise/non-free Sources                               
Get:10 http://security.ubuntu.com precise-security/main Sources [69.9 kB]                
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Get:11 http://gb.archive.ubuntu.com precise/restricted Translation-en_GB [2,406 B]       
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en                       
Get:12 http://gb.archive.ubuntu.com precise/restricted Translation-en_AU [2,407 B]       
Get:13 http://gb.archive.ubuntu.com precise/universe Translation-en_GB [5,492 B]         
Hit http://gb.archive.ubuntu.com precise/universe Translation-en                         
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Ign http://archive.canonical.com precise/partner Translation-en_GB                       
Get:14 http://security.ubuntu.com precise-security/multiverse Sources [1,389 B]          
Get:15 http://security.ubuntu.com precise-security/universe Sources [24.0 kB]            
Ign http://archive.canonical.com precise/partner Translation-en                          
Ign http://archive.canonical.com precise/partner Translation-en_AU                       
Ign http://archive.canonical.com precise/partner Translation-en_NZ                       
Ign http://archive.canonical.com precise/partner Translation-fa                          
Ign http://extras.ubuntu.com precise/main Translation-en_GB                              
Get:16 http://security.ubuntu.com precise-security/main i386 Packages [259 kB]           
Ign http://archive.canonical.com precise/partner Translation-en_GB                       
Ign http://extras.ubuntu.com precise/main Translation-en                                 
Ign http://extras.ubuntu.com precise/main Translation-en_AU                              
Ign http://extras.ubuntu.com precise/main Translation-en_NZ                              
Ign http://extras.ubuntu.com precise/main Translation-fa                                 
Ign http://archive.canonical.com precise/partner Translation-en                          
Ign http://archive.canonical.com precise/partner Translation-en_AU                       
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Ign http://archive.canonical.com precise/partner Translation-en_NZ                       
Ign http://archive.canonical.com precise/partner Translation-fa                          
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Hit http://dl.google.com stable/main i386 Packages                                       
Ign http://dl.google.com stable/main TranslationIndex                                    
Get:17 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]    
Get:18 http://security.ubuntu.com precise-security/universe i386 Packages [73.4 kB]      
Get:19 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,368 B]    
Hit http://security.ubuntu.com precise-security/main TranslationIndex                    
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex              
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex              
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                
Hit http://security.ubuntu.com precise-security/main Translation-en                      
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                
Hit http://security.ubuntu.com precise-security/restricted Translation-en                
Hit http://security.ubuntu.com precise-security/universe Translation-en                  
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Ign http://ppa.launchpad.net precise/main Translation-en_GB                              
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://ppa.launchpad.net precise/main Translation-en_AU                              
Ign http://ppa.launchpad.net precise/main Translation-en_NZ                              
Ign http://ppa.launchpad.net precise/main Translation-fa                                 
Ign http://ppa.launchpad.net precise/main Translation-en_GB                              
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Ign http://ppa.launchpad.net precise/main Translation-en_AU                              
Ign http://ppa.launchpad.net precise/main Translation-en_NZ                              
Ign http://ppa.launchpad.net precise/main Translation-fa                                 
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Get:20 http://gb.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]         
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Ign http://dl.google.com stable/main Translation-en_GB                                   
Get:21 http://gb.archive.ubuntu.com precise-updates/main Sources [379 kB]                
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Hit http://dl.google.com stable/main i386 Packages                                       
Ign http://dl.google.com stable/main TranslationIndex                                    
Ign http://dl.google.com stable/main Translation-en                                      
Hit http://packages.medibuntu.org precise/free i386 Packages                             
Ign http://dl.google.com stable/main Translation-en_AU                                   
Ign http://dl.google.com stable/main Translation-en_NZ                                   
Hit http://ppa.launchpad.net precise/main Sources                                        
Ign http://dl.google.com stable/main Translation-fa                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Hit http://packages.medibuntu.org precise/non-free i386 Packages                         
Ign http://ppa.launchpad.net precise/main Translation-en_GB                              
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://ppa.launchpad.net precise/main Translation-en_AU                              
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Ign http://ppa.launchpad.net precise/main Translation-en_NZ                              
Ign http://packages.medibuntu.org precise/free TranslationIndex                          
Ign http://ppa.launchpad.net precise/main Translation-fa                                 
Ign http://packages.medibuntu.org precise/non-free TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                               
Ign http://ppa.launchpad.net precise/main Translation-en_GB                              
Get:22 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [6,562 B]         
Get:23 http://gb.archive.ubuntu.com precise-updates/universe Sources [85.8 kB]           
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://ppa.launchpad.net precise/main Translation-en_AU                              
Ign http://ppa.launchpad.net precise/main Translation-en_NZ                              
Ign http://ppa.launchpad.net precise/main Translation-fa                                 
Get:24 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [613 kB]          
Ign http://dl.google.com stable/main Translation-en_GB                                   
Ign http://dl.google.com stable/main Translation-en                                      
Ign http://dl.google.com stable/main Translation-en_AU                                   
Ign http://dl.google.com stable/main Translation-en_NZ                                   
Ign http://ppa.launchpad.net precise/main Translation-en_GB                              
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://dl.google.com stable/main Translation-fa                                      
Get:25 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]   
Get:26 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [199 kB]      
Ign http://ppa.launchpad.net precise/main Translation-en_AU                              
Ign http://ppa.launchpad.net precise/main Translation-en_NZ                              
Ign http://ppa.launchpad.net precise/main Translation-fa                                 
Get:27 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]   
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex                   
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex             
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex               
Get:28 http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB [96.4 kB]     
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en                     
Get:29 http://gb.archive.ubuntu.com precise-updates/main Translation-en_AU [4,434 B]
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-fa                     
Get:30 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB [79.8 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_GB                              
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://ppa.launchpad.net precise/main Translation-en_AU                              
Ign http://ppa.launchpad.net precise/main Translation-en_NZ                              
Ign http://ppa.launchpad.net precise/main Translation-fa                                 
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en               
Get:31 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_AU [94.4 kB]
Get:32 http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB [2,406 B]
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en               
Get:33 http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_AU [2,407 B]
Get:34 http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB [5,492 B] 
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en                 
Ign http://ppa.launchpad.net precise/main Translation-en_GB             
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_AU             
Ign http://ppa.launchpad.net precise/main Translation-en_NZ             
Ign http://ppa.launchpad.net precise/main Translation-fa                
Ign http://ppa.launchpad.net precise/main Translation-en_GB                              
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://ppa.launchpad.net precise/main Translation-en_AU                              
Ign http://ppa.launchpad.net precise/main Translation-en_NZ                              
Ign http://ppa.launchpad.net precise/main Translation-fa
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_AU
Ign http://ppa.launchpad.net precise/main Translation-en_NZ                              
Ign http://ppa.launchpad.net precise/main Translation-fa                                 
Ign http://ppa.launchpad.net precise/main Translation-en_GB                              
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://ppa.launchpad.net precise/main Translation-en_AU             
Ign http://ppa.launchpad.net precise/main Translation-en_NZ             
Ign http://ppa.launchpad.net precise/main Translation-fa
Ign http://ppa.launchpad.net precise/main Translation-en_GB             
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://ppa.launchpad.net precise/main Translation-en_AU                              
Ign http://ppa.launchpad.net precise/main Translation-en_NZ
Ign http://ppa.launchpad.net precise/main Translation-fa
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://ppa.launchpad.net precise/main Translation-en_AU                              
Ign http://ppa.launchpad.net precise/main Translation-en_NZ                              
Ign http://ppa.launchpad.net precise/main Translation-fa                                 
Ign http://ppa.launchpad.net precise/main Translation-en_GB                              
Ign http://ppa.launchpad.net precise/main Translation-en                           
Ign http://ppa.launchpad.net precise/main Translation-en_AU                        
Ign http://ppa.launchpad.net precise/main Translation-en_NZ                        
Ign http://ppa.launchpad.net precise/main Translation-fa                           
Ign http://ppa.launchpad.net precise/main Translation-en_GB                        
Ign http://ppa.launchpad.net precise/main Translation-en                           
Ign http://ppa.launchpad.net precise/main Translation-en_AU             
Ign http://ppa.launchpad.net precise/main Translation-en_NZ             
Ign http://ppa.launchpad.net precise/main Translation-fa                
Ign http://ppa.launchpad.net precise/main Translation-en_GB                              
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://ppa.launchpad.net precise/main Translation-en_AU                              
Ign http://ppa.launchpad.net precise/main Translation-en_NZ                              
Ign http://ppa.launchpad.net precise/main Translation-fa                                 
Ign http://ppa.launchpad.net precise/main Translation-en_GB                              
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://ppa.launchpad.net precise/main Translation-en_AU             
Ign http://ppa.launchpad.net precise/main Translation-en_NZ
Ign http://ppa.launchpad.net precise/main Translation-fa
Ign http://packages.medibuntu.org precise/free Translation-en_GB                   
Ign http://packages.medibuntu.org precise/free Translation-en                      
Ign http://packages.medibuntu.org precise/free Translation-en_AU                   
Ign http://packages.medibuntu.org precise/free Translation-en_NZ                         
Ign http://packages.medibuntu.org precise/free Translation-fa                            
Ign http://packages.medibuntu.org precise/non-free Translation-en_GB                     
Ign http://packages.medibuntu.org precise/non-free Translation-en                        
Ign http://packages.medibuntu.org precise/non-free Translation-en_AU                     
Ign http://packages.medibuntu.org precise/non-free Translation-en_NZ                     
Ign http://packages.medibuntu.org precise/non-free Translation-fa                        
Fetched 2,420 kB in 7s (345 kB/s)                                                        
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ precise/free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_precise_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ precise/non-free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_precise_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/talkplugin/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ck@ck-eM250:~$ 
```

---

### Post by matt_symes on 2013-04-30
Hi

This is the extra line.

```
APT::Periodic::Unattended-Upgrade "1";
```

You have configured unattended security upgrades ? 

You should have the package installed. You can check with

```
dpkg -l unattended-upgrades
```

Can you post the output of the other two commands *apt-get *from my first post please.

EDIT:

For your reference:

[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

Kind regards

---

### Post by CK000 on 2013-04-30
Yes I certainly can post them for you.
```
ck@ck-eM250:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ck@ck-eM250:~$ 
```

---

### Post by CK000 on 2013-04-30
```
ck@ck-eM250:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ck@ck-eM250:~$ 

```

---

### Post by matt_symes on 2013-04-30
Hi
> W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages) 
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise/free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_precise_free_binary-i386_Packages) 
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise/non-free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_precise_non-free_binary-i386_Packages) 
W: Duplicate sources.list entry [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages) 

These are a problem. Open a terminal and type

```
sudo rm -rf /var/lib/apt/lists/*
```

```
sudo mkdir -p /var/lib/apt/lists/partial
```

```
sudo apt-get update
```

Post back any errors and don't forget the *sudo* command.

After that try update manager again.

**EDIT:**
 
Can you also post the output of this command.

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

Kind regards

---

### Post by CK000 on 2013-04-30
I have not posted the entire output of the last command, just the end of it which I believe are the errors, I will post the whole output if requested.

```
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ precise/free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_precise_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ precise/non-free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_precise_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/talkplugin/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ck@ck-eM250:~$ 
```

Thank you.

---

### Post by CK000 on 2013-04-30
This is the output of the last command you requested me to post:-

```
ck@ck-eM250:~$ grep "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:deb-src http://gb.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:deb http://packages.medibuntu.org/ precise free non-free
/etc/apt/sources.list:deb-src http://packages.medibuntu.org/ precise free non-free
/etc/apt/sources.list:deb-src http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list:deb http://archive.canonical.com/ precise partner
/etc/apt/sources.list:deb-src http://archive.canonical.com/ precise partner
/etc/apt/sources.list.d/audacity-team-daily-precise.list:deb http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
/etc/apt/sources.list.d/audacity-team-daily-precise.list:deb-src http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
/etc/apt/sources.list.d/audacity-team-daily-precise.list.save:deb http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
/etc/apt/sources.list.d/audacity-team-daily-precise.list.save:deb-src http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list:deb http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list:deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.save:deb http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.save:deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/f-muriana-ubuntu-builder-precise.list:deb http://ppa.launchpad.net/f-muriana/ubuntu-builder/ubuntu precise main
/etc/apt/sources.list.d/f-muriana-ubuntu-builder-precise.list:deb-src http://ppa.launchpad.net/f-muriana/ubuntu-builder/ubuntu precise main
/etc/apt/sources.list.d/f-muriana-ubuntu-builder-precise.list.save:deb http://ppa.launchpad.net/f-muriana/ubuntu-builder/ubuntu precise main
/etc/apt/sources.list.d/f-muriana-ubuntu-builder-precise.list.save:deb-src http://ppa.launchpad.net/f-muriana/ubuntu-builder/ubuntu precise main
/etc/apt/sources.list.d/google-earth.list:deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/google-earth.list.save:deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/google.list:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/google.list.save:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list.save:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/libreoffice-libreoffice-3-5-precise.list:deb http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-3-5-precise.list:deb-src http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-3-5-precise.list.save:deb http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-3-5-precise.list.save:deb-src http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list:deb http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list:deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list.save:deb http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list.save:deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-ppa-lucid.list.distUpgrade:deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu lucid main
/etc/apt/sources.list.d/lucid-partner.list:deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list.d/lucid-partner.list.distUpgrade:deb http://archive.canonical.com/ubuntu lucid partner
/etc/apt/sources.list.d/lucid-partner.list.save:deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list.d/medibuntu.list:deb http://packages.medibuntu.org/ precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
/etc/apt/sources.list.d/medibuntu.list.save:deb http://packages.medibuntu.org/ precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
/etc/apt/sources.list.d/mrpouit-ppa-precise.list:deb http://ppa.launchpad.net/mrpouit/ppa/ubuntu precise main
/etc/apt/sources.list.d/mrpouit-ppa-precise.list:deb-src http://ppa.launchpad.net/mrpouit/ppa/ubuntu precise main
/etc/apt/sources.list.d/mrpouit-ppa-precise.list.save:deb http://ppa.launchpad.net/mrpouit/ppa/ubuntu precise main
/etc/apt/sources.list.d/mrpouit-ppa-precise.list.save:deb-src http://ppa.launchpad.net/mrpouit/ppa/ubuntu precise main
/etc/apt/sources.list.d/n-muench-programs-ppa-precise.list:deb http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu precise main
/etc/apt/sources.list.d/n-muench-programs-ppa-precise.list:deb-src http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu precise main
/etc/apt/sources.list.d/n-muench-programs-ppa-precise.list.save:deb http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu precise main
/etc/apt/sources.list.d/n-muench-programs-ppa-precise.list.save:deb-src http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list:deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list:deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.save:deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.save:deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/paul-climbing-ppa-precise.list:deb http://ppa.launchpad.net/paul-climbing/ppa/ubuntu precise main
/etc/apt/sources.list.d/paul-climbing-ppa-precise.list:deb-src http://ppa.launchpad.net/paul-climbing/ppa/ubuntu precise main
/etc/apt/sources.list.d/paul-climbing-ppa-precise.list.save:deb http://ppa.launchpad.net/paul-climbing/ppa/ubuntu precise main
/etc/apt/sources.list.d/paul-climbing-ppa-precise.list.save:deb-src http://ppa.launchpad.net/paul-climbing/ppa/ubuntu precise main
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list:deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu precise main
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list:deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu precise main
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list.save:deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu precise main
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list.save:deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu precise main
/etc/apt/sources.list.d/shnatsel-gimp-paint-studio-precise.list:deb http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu precise main
/etc/apt/sources.list.d/shnatsel-gimp-paint-studio-precise.list:deb-src http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu precise main
/etc/apt/sources.list.d/shnatsel-gimp-paint-studio-precise.list.save:deb http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu precise main
/etc/apt/sources.list.d/shnatsel-gimp-paint-studio-precise.list.save:deb-src http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu precise main
/etc/apt/sources.list.d/telepathy-ppa-precise.list:deb http://ppa.launchpad.net/telepathy/ppa/ubuntu precise main
/etc/apt/sources.list.d/telepathy-ppa-precise.list:deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu precise main
/etc/apt/sources.list.d/telepathy-ppa-precise.list.save:deb http://ppa.launchpad.net/telepathy/ppa/ubuntu precise main
/etc/apt/sources.list.d/telepathy-ppa-precise.list.save:deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list:deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save:deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list:deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list:deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.save:deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.save:deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/videolan-stable-daily-precise.list:deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu precise main
/etc/apt/sources.list.d/videolan-stable-daily-precise.list:deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu precise main
/etc/apt/sources.list.d/videolan-stable-daily-precise.list.save:deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu precise main
/etc/apt/sources.list.d/videolan-stable-daily-precise.list.save:deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
ck@ck-eM250:~$ 
```

Thank you and best wishes.

---

### Post by matt_symes on 2013-04-30
Hi

You have a number of duplicate sources in the sources files and these are causing you problems. One of them is also wrong.

> /etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list:deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

/etc/apt/sources.list.d/medibuntu.list:deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
/etc/apt/sources.list:deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free

/etc/apt/sources.list.d/google.list:deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
/etc/apt/sources.list.d/google-talkplugin.list:deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

Open a terminal and type

```
sudo rm /etc/apt/sources.list.d/{medibuntu,google}.list
```

Then copy and paste this into the terminal...

```
sudo sed -i 's/deb http:\/\/archive.canonical.com\/ precise partner//' /etc/apt/sources.list
```

Then run the commands in post #10 again.

Post back errors.

Kind regards

---

### Post by CK000 on 2013-04-30
Hello and thank you very much for your help so far. Having done all that these are the errors, as far as I can ascertain:-

```
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ck@ck-eM250:~$ 

```

---

### Post by matt_symes on 2013-04-30
Hi

We're making progress.

Can you post the output of this command again please.

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

**EDIT:**

I've just edited the above command to add the -n switch to grep. Please use the modified command.

Kind regards

---

### Post by CK000 on 2013-04-30
```
ck@ck-eM250:~$ grep "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:deb-src http://gb.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:deb http://packages.medibuntu.org/ precise free non-free
/etc/apt/sources.list:deb-src http://packages.medibuntu.org/ precise free non-free
/etc/apt/sources.list:deb-src http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list:deb-src http://archive.canonical.com/ precise partner
/etc/apt/sources.list.d/audacity-team-daily-precise.list:deb http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
/etc/apt/sources.list.d/audacity-team-daily-precise.list:deb-src http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
/etc/apt/sources.list.d/audacity-team-daily-precise.list.save:deb http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
/etc/apt/sources.list.d/audacity-team-daily-precise.list.save:deb-src http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list:deb http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list:deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.save:deb http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.save:deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/f-muriana-ubuntu-builder-precise.list:deb http://ppa.launchpad.net/f-muriana/ubuntu-builder/ubuntu precise main
/etc/apt/sources.list.d/f-muriana-ubuntu-builder-precise.list:deb-src http://ppa.launchpad.net/f-muriana/ubuntu-builder/ubuntu precise main
/etc/apt/sources.list.d/f-muriana-ubuntu-builder-precise.list.save:deb http://ppa.launchpad.net/f-muriana/ubuntu-builder/ubuntu precise main
/etc/apt/sources.list.d/f-muriana-ubuntu-builder-precise.list.save:deb-src http://ppa.launchpad.net/f-muriana/ubuntu-builder/ubuntu precise main
/etc/apt/sources.list.d/google-earth.list:deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/google-earth.list.save:deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/google.list.save:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list.save:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/libreoffice-libreoffice-3-5-precise.list:deb http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-3-5-precise.list:deb-src http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-3-5-precise.list.save:deb http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-3-5-precise.list.save:deb-src http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list:deb http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list:deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list.save:deb http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list.save:deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu precise main
/etc/apt/sources.list.d/libreoffice-ppa-lucid.list.distUpgrade:deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu lucid main
/etc/apt/sources.list.d/lucid-partner.list:deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list.d/lucid-partner.list.distUpgrade:deb http://archive.canonical.com/ubuntu lucid partner
/etc/apt/sources.list.d/lucid-partner.list.save:deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list.d/medibuntu.list.save:deb http://packages.medibuntu.org/ precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
/etc/apt/sources.list.d/mrpouit-ppa-precise.list:deb http://ppa.launchpad.net/mrpouit/ppa/ubuntu precise main
/etc/apt/sources.list.d/mrpouit-ppa-precise.list:deb-src http://ppa.launchpad.net/mrpouit/ppa/ubuntu precise main
/etc/apt/sources.list.d/mrpouit-ppa-precise.list.save:deb http://ppa.launchpad.net/mrpouit/ppa/ubuntu precise main
/etc/apt/sources.list.d/mrpouit-ppa-precise.list.save:deb-src http://ppa.launchpad.net/mrpouit/ppa/ubuntu precise main
/etc/apt/sources.list.d/n-muench-programs-ppa-precise.list:deb http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu precise main
/etc/apt/sources.list.d/n-muench-programs-ppa-precise.list:deb-src http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu precise main
/etc/apt/sources.list.d/n-muench-programs-ppa-precise.list.save:deb http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu precise main
/etc/apt/sources.list.d/n-muench-programs-ppa-precise.list.save:deb-src http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list:deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list:deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.save:deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.save:deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/paul-climbing-ppa-precise.list:deb http://ppa.launchpad.net/paul-climbing/ppa/ubuntu precise main
/etc/apt/sources.list.d/paul-climbing-ppa-precise.list:deb-src http://ppa.launchpad.net/paul-climbing/ppa/ubuntu precise main
/etc/apt/sources.list.d/paul-climbing-ppa-precise.list.save:deb http://ppa.launchpad.net/paul-climbing/ppa/ubuntu precise main
/etc/apt/sources.list.d/paul-climbing-ppa-precise.list.save:deb-src http://ppa.launchpad.net/paul-climbing/ppa/ubuntu precise main
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list:deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu precise main
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list:deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu precise main
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list.save:deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu precise main
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list.save:deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu precise main
/etc/apt/sources.list.d/shnatsel-gimp-paint-studio-precise.list:deb http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu precise main
/etc/apt/sources.list.d/shnatsel-gimp-paint-studio-precise.list:deb-src http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu precise main
/etc/apt/sources.list.d/shnatsel-gimp-paint-studio-precise.list.save:deb http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu precise main
/etc/apt/sources.list.d/shnatsel-gimp-paint-studio-precise.list.save:deb-src http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu precise main
/etc/apt/sources.list.d/telepathy-ppa-precise.list:deb http://ppa.launchpad.net/telepathy/ppa/ubuntu precise main
/etc/apt/sources.list.d/telepathy-ppa-precise.list:deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu precise main
/etc/apt/sources.list.d/telepathy-ppa-precise.list.save:deb http://ppa.launchpad.net/telepathy/ppa/ubuntu precise main
/etc/apt/sources.list.d/telepathy-ppa-precise.list.save:deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list:deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save:deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list:deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list:deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.save:deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.save:deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/videolan-stable-daily-precise.list:deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu precise main
/etc/apt/sources.list.d/videolan-stable-daily-precise.list:deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu precise main
/etc/apt/sources.list.d/videolan-stable-daily-precise.list.save:deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu precise main
/etc/apt/sources.list.d/videolan-stable-daily-precise.list.save:deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
ck@ck-eM250:~$ 
```

---

### Post by matt_symes on 2013-04-30
Hi

Open a terminal and copy and paste

```
sudo sed -i 's/deb-src http:\/\/archive.canonical.com\/ precise partner//' /etc/apt/sources.list
```

Then run the commands in post #10 again please.

Post back any errors.

Kind regards

---

### Post by CK000 on 2013-04-30
Hi,

These are the errors having done all that again:-

```
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ck@ck-eM250:~$ 

```

---

### Post by matt_symes on 2013-04-30
Hi

Sorry, going blind here. Well it's almost 1.00am so i am excused.

From the terminal...

```
sudo rm /etc/apt/sources.list.d/lucid-partner.list
```

Then the commands from post #10 again.

Kind regards

---

### Post by CK000 on 2013-04-30
Hello, I can not say exactly where I am due not having enough posts for an avatar and all that. However I agree it's late here too, so you are excused, yes.

I have run all that again and now there are no errors, well certainly no code at the end which I think remarks errors.

---

### Post by matt_symes on 2013-04-30
Hi

> **CK000 said:**
> Hello, I can not say exactly where I am due not having enough posts for an avatar and all that. However I agree it's late here too, so you are excused, yes.

I have run all that again and now there are no errors, well certainly no code at the end which I think remarks errors.

Now run update manager. Do you still get the same problem ? There may be more to look at.

Kind regards

---

### Post by CK000 on 2013-04-30
Hello, and many thanks indeed for all your help sir. I have just run update manager and am glad to report that it reported no problems, no bug reports or anything. It simply worked flawlessly and reported that there were no updates to install. I clicked 'check' still no updates to install.

So, thank you. I certainly think we can now mark this thread as solved. I don't know how to do that on the new forum format, but it does not matter at this late hour.

Many thanks again Sir.

With best wishes.

---

