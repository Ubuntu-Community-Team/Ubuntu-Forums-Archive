---
title: "linux-headers-3.2.0-76 linux-headers-3.2.0-76-generic removed in error?"
date: 2015-02-25
forum: General Help
---

### Post by Hiflux_Seven on 2015-02-25
On 12.04.5 LST Precise, the software updater removed the linux-headers-3.2.0-76 and linux-headers-3.2.0-76-generic packages for reasons I don't understand.  This I only gleaned from reading /var/log/dpkg.log.

Today a new kernel (linux-image-3.2.0-77 and friends) was installed, *without* the corresponding header files (as the earlier version header files were missing perhaps??)

Any idea why such has happened and what I should do to restore the proper header file(s) for this set of kernel images??

Thanks.

---

### Post by Bucky Ball on 2015-02-25
Please open a terminal and:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Post and and all errors.

---

### Post by Hiflux_Seven on 2015-02-25
See no errors:

```
user@machine:~$ sudo apt-get -q autoremove
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


```
user@machine:~$ sudo apt-get update
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                              
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner TranslationIndex                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                  
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                              
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                        
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en_US                     
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                            
Fetched 594 B in 12s (47 B/s)                                                                      
Reading package lists... Done
```


```
user@machine:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


```
user@machine:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by QIII on 2015-02-25
Hello, HiFlux_Seven!

Please use code tags.  It makes thing much easier to read.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by Bucky Ball on 2015-02-25
The problem I see is that you have Marverick repos enabled and what seem to be PPAs duplicating some of the official Canonical Ubuntu repos. Maverick is 10.10 and is long gone. Open Software Sources (I think it's called in Ubuntu) and unless you have them there for a reasone, disable anything to do with Maverick. Run the update command again, and then please give the output of:

```
uname -a
```

And as QIII mentions, [code] tags, please. Last link in my signature. ;)

---

### Post by Hiflux_Seven on 2015-02-25
Well, I suppose the Maverick repos are enabled because the script(s) never removed them when the system was upgraded to 12.04.  "Software Sources" won't let you do this, so I did it by hand.  Results are the same after update, upgrade & dist-upgrade.  Output of uname:

```

user@machine:~$ uname -a
Linux machine 3.2.0-77-generic-pae #112-Ubuntu SMP Tue Feb 10 15:41:09 UTC 2015 i686 i686 i386 GNU/Linux

```

---

