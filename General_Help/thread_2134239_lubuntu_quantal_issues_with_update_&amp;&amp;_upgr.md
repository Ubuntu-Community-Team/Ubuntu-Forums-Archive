---
title: "lubuntu quantal issues with update &amp;&amp; upgrade"
date: 2013-04-10
forum: General Help
---

### Post by raen on 2013-04-10
Hello. I have a brand-new installation of Lubuntu 12.10 Quantal on an Acer Aspire one D250-1165.

Typing 
```

$ sudo apt-get update && apt-get upgrade

```

gets me
```

Hit http://dl.google.com stable Release.gpg
Hit http://us.archive.ubuntu.com quantal Release.gpg                                          
Hit http://dl.google.com stable Release                                                       
Get:1 http://linux.dropbox.com precise Release.gpg [489 B]                                    
Get:2 http://us.archive.ubuntu.com quantal-updates Release.gpg [933 B]                        
Hit http://us.archive.ubuntu.com quantal Release                                              
Hit http://ppa.launchpad.net quantal Release.gpg                                              
Get:3 http://security.ubuntu.com quantal-security Release.gpg [933 B]                         
Get:4 http://linux.dropbox.com precise Release [2,603 B]                                      
Hit http://dl.google.com stable/main i386 Packages                                            
Hit http://extras.ubuntu.com quantal Release.gpg                                              
Get:5 http://us.archive.ubuntu.com quantal-updates Release [49.6 kB]                          
Hit http://archive.canonical.com quantal Release.gpg                                          
Hit http://ppa.launchpad.net quantal Release                                                  
Get:6 http://security.ubuntu.com quantal-security Release [49.6 kB]                           
Get:7 http://linux.dropbox.com precise/main i386 Packages [1,148 B]                           
Hit http://extras.ubuntu.com quantal Release                                                  
Hit http://archive.canonical.com quantal Release                                              
Hit http://us.archive.ubuntu.com quantal/main Sources                                         
Hit http://us.archive.ubuntu.com quantal/restricted Sources                                   
Hit http://ppa.launchpad.net quantal/main Sources                                             
Hit http://us.archive.ubuntu.com quantal/universe Sources                                     
Hit http://extras.ubuntu.com quantal/main i386 Packages                                       
Hit http://us.archive.ubuntu.com quantal/multiverse Sources                                   
Hit http://archive.canonical.com quantal/partner i386 Packages                                
Hit http://ppa.launchpad.net quantal/main i386 Packages                                       
Hit http://us.archive.ubuntu.com quantal/main i386 Packages                                   
Hit http://us.archive.ubuntu.com quantal/restricted i386 Packages                             
Hit http://us.archive.ubuntu.com quantal/universe i386 Packages                               
Get:8 http://security.ubuntu.com quantal-security/main Sources [38.7 kB]                      
Hit http://us.archive.ubuntu.com quantal/multiverse i386 Packages                             
Ign http://dl.google.com stable/main Translation-en_US                                        
Hit http://us.archive.ubuntu.com quantal/main Translation-en                                  
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en                            
Get:9 http://security.ubuntu.com quantal-security/restricted Sources [1,833 B]                
Ign http://linux.dropbox.com precise/main Translation-en_US                                   
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en                            
Get:10 http://security.ubuntu.com quantal-security/universe Sources [16.1 kB]                 
Ign http://linux.dropbox.com precise/main Translation-en                                      
Hit http://us.archive.ubuntu.com quantal/universe Translation-en                              
Get:11 http://us.archive.ubuntu.com quantal-updates/main Sources [88.2 kB]                    
Get:12 http://security.ubuntu.com quantal-security/multiverse Sources [704 B]                 
Get:13 http://security.ubuntu.com quantal-security/main i386 Packages [104 kB]                
Get:14 http://us.archive.ubuntu.com quantal-updates/restricted Sources [2,564 B]              
Get:15 http://us.archive.ubuntu.com quantal-updates/universe Sources [81.8 kB]                
Get:16 http://us.archive.ubuntu.com quantal-updates/multiverse Sources [3,661 B]              
Get:17 http://us.archive.ubuntu.com quantal-updates/main i386 Packages [225 kB]               
Ign http://extras.ubuntu.com quantal/main Translation-en_US                                   
Ign http://ppa.launchpad.net quantal/main Translation-en_US                                   
Ign http://dl.google.com stable/main Translation-en                                           
Ign http://archive.canonical.com quantal/partner Translation-en_US                            
Ign http://extras.ubuntu.com quantal/main Translation-en                                      
Ign http://ppa.launchpad.net quantal/main Translation-en                                      
Ign http://archive.canonical.com quantal/partner Translation-en                               
Get:18 http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages [4,841 B]        
Get:19 http://security.ubuntu.com quantal-security/restricted i386 Packages [3,531 B]
Get:20 http://us.archive.ubuntu.com quantal-updates/universe i386 Packages [179 kB]  
Get:21 http://security.ubuntu.com quantal-security/universe i386 Packages [45.8 kB]
Get:22 http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages [10.8 kB]      
Hit http://us.archive.ubuntu.com quantal-updates/main Translation-en    
Get:23 http://security.ubuntu.com quantal-security/multiverse i386 Packages [1,402 B]
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en
Hit http://security.ubuntu.com quantal-security/main Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/universe Translation-en
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en
Hit http://security.ubuntu.com quantal-security/restricted Translation-en
Hit http://security.ubuntu.com quantal-security/universe Translation-en 
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://security.ubuntu.com quantal-security/main Translation-en_US
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Fetched 913 kB in 4s (185 kB/s)
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


```

What's with all the ignores and those errors? :confused::(

Thanks,
raen

---

### Post by Frogs Hair on 2013-04-10
Sometimes this message will be displayed if more than one package manager application is open at once.

I'm not sure why Precise Main is showing up but I am not a Dropbox user.  ```
[COLOR=#000000][FONT=Ubuntu Mono]Get:7 http://linux.dropbox.com precise/main i386 Packages
```[/FONT][/COLOR]

---

### Post by raen on 2013-04-10
> **Frogs Hair said:**
> Sometimes this message will be displayed if more than one package manager application is open at once.

I'm not sure why Precise Main is showing up but I am not a Dropbox user.  ```
[COLOR=#000000][FONT=Ubuntu Mono]Get:7 http://linux.dropbox.com precise/main i386 Packages[/FONT][/COLOR]
```

Nice catch. I hadn't noticed that. That was probably an absent-minded error on my part.

As for the ignores and errors, I guess I'll try again after making sure nothing else is open.

Thanks,
raen

---

### Post by raen on 2013-05-18
Duh moment. The problem is that I need to preface both commands with "sudo".

---

