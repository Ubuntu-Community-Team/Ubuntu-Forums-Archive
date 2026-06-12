---
title: "Problem updating"
date: 2013-01-15
forum: General Help
---

### Post by trantan on 2013-01-15
Hi everybody, I tried NikTh's way to solver, but my problem is not be solved. How can I do?
Thank in advance.

```
tan@ubuntu:~$ sudo rm -rf /var/lib/apt/lists/*
tan@ubuntu:~$ sudo apt-get clean
tan@ubuntu:~$ sudo apt-get update
Ign http://ftp.us.debian.org lenny Release.gpg                                 
Ign http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://extras.ubuntu.com maverick Release.gpg                              
Ign http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.debian.org lenny/updates Release.gpg                       
Ign http://ftp.us.debian.org/debian/ lenny/contrib Translation-en              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.debian.org/ lenny/updates/contrib Translation-en           
Ign http://ftp.us.debian.org/debian/ lenny/contrib Translation-en_US           
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://ftp.us.debian.org/debian/ lenny/main Translation-en                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.debian.org/ lenny/updates/contrib Translation-en_US        
Ign http://ftp.us.debian.org/debian/ lenny/main Translation-en_US              
Ign http://extras.ubuntu.com maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.debian.org/ lenny/updates/main Translation-en              
Ign http://ftp.us.debian.org/debian/ lenny/non-free Translation-en             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://extras.ubuntu.com maverick/main Sources                             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.debian.org/ lenny/updates/main Translation-en_US           
Ign http://ftp.us.debian.org/debian/ lenny/non-free Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://ftp.us.debian.org lenny Release                                     
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://security.debian.org/ lenny/updates/non-free Translation-en          
Ign http://extras.ubuntu.com maverick/main Sources                             
Ign http://ftp.us.debian.org lenny/main i386 Packages                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://ftp.us.debian.org lenny/contrib i386 Packages                       
Ign http://us.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://ftp.us.debian.org lenny/non-free i386 Packages                      
Err http://extras.ubuntu.com maverick/main Sources                             
  404  Not Found
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://ftp.us.debian.org lenny/main i386 Packages                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Err http://extras.ubuntu.com maverick/main i386 Packages                       
  404  Not Found
Ign http://security.debian.org/ lenny/updates/non-free Translation-en_US       
Ign http://ftp.us.debian.org lenny/contrib i386 Packages                       
Ign http://security.ubuntu.com maverick-security Release             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://security.debian.org lenny/updates Release                           
Ign http://ftp.us.debian.org lenny/non-free i386 Packages                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com maverick-security/main Sources        
Err http://ftp.us.debian.org lenny/main i386 Packages                
  404  Not Found [IP: 128.30.2.36 80]
Ign http://security.debian.org lenny/updates/main i386 Packages      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://security.ubuntu.com maverick-security/restricted Sources  
Err http://ftp.us.debian.org lenny/contrib i386 Packages             
  404  Not Found [IP: 128.30.2.36 80]
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://security.debian.org lenny/updates/contrib i386 Packages   
Ign http://security.ubuntu.com maverick-security/universe Sources    
Err http://ftp.us.debian.org lenny/non-free i386 Packages            
  404  Not Found [IP: 128.30.2.36 80]
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://security.debian.org lenny/updates/non-free i386 Packages
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Ign http://security.ubuntu.com maverick-security/multiverse Sources
Ign http://us.archive.ubuntu.com maverick Release
Ign http://security.debian.org lenny/updates/main i386 Packages
Ign http://security.ubuntu.com maverick-security/main i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates Release
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Ign http://security.debian.org lenny/updates/contrib i386 Packages
Ign http://us.archive.ubuntu.com maverick/main Sources
Ign http://security.ubuntu.com maverick-security/universe i386 Packages
Ign http://us.archive.ubuntu.com maverick/restricted Sources
Ign http://security.debian.org lenny/updates/non-free i386 Packages
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages
Err http://security.debian.org lenny/updates/main i386 Packages
  404  Not Found [IP: 212.211.132.250 80]
Ign http://security.ubuntu.com maverick-security/main Sources
Err http://security.debian.org lenny/updates/contrib i386 Packages
  404  Not Found [IP: 212.211.132.250 80]
Ign http://us.archive.ubuntu.com maverick/universe Sources
Ign http://security.ubuntu.com maverick-security/restricted Sources
Err http://security.debian.org lenny/updates/non-free i386 Packages
  404  Not Found [IP: 212.211.132.250 80]
Ign http://us.archive.ubuntu.com maverick/multiverse Sources
Ign http://security.ubuntu.com maverick-security/universe Sources
Ign http://us.archive.ubuntu.com maverick/main i386 Packages
Ign http://us.archive.ubuntu.com maverick/restricted i386 Packages
Ign http://security.ubuntu.com maverick-security/multiverse Sources
Ign http://us.archive.ubuntu.com maverick/universe i386 Packages
Ign http://security.ubuntu.com maverick-security/main i386 Packages
Ign http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Ign http://security.ubuntu.com maverick-security/universe i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/main Sources
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/restricted Sources
Err http://security.ubuntu.com maverick-security/main Sources
  404  Not Found [IP: 91.189.92.200 80]
Ign http://us.archive.ubuntu.com maverick-updates/universe Sources
Err http://security.ubuntu.com maverick-security/restricted Sources
  404  Not Found [IP: 91.189.92.200 80]
Ign http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Err http://security.ubuntu.com maverick-security/universe Sources
  404  Not Found [IP: 91.189.92.200 80]
Ign http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Err http://security.ubuntu.com maverick-security/multiverse Sources
  404  Not Found [IP: 91.189.92.200 80]
Ign http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Err http://security.ubuntu.com maverick-security/main i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Ign http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Err http://security.ubuntu.com maverick-security/restricted i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Ign http://us.archive.ubuntu.com maverick/main Sources
Err http://security.ubuntu.com maverick-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Ign http://us.archive.ubuntu.com maverick/restricted Sources
Ign http://us.archive.ubuntu.com maverick/universe Sources
Err http://security.ubuntu.com maverick-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Ign http://us.archive.ubuntu.com maverick/multiverse Sources
Ign http://us.archive.ubuntu.com maverick/main i386 Packages
Ign http://us.archive.ubuntu.com maverick/restricted i386 Packages
Ign http://us.archive.ubuntu.com maverick/universe i386 Packages
Ign http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/main Sources
Ign http://us.archive.ubuntu.com maverick-updates/restricted Sources
Ign http://us.archive.ubuntu.com maverick-updates/universe Sources
Ign http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Ign http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Err http://us.archive.ubuntu.com maverick/main Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/main Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ftp.us.debian.org/debian/dists/lenny/main/binary-i386/Packages.gz  404  Not Found [IP: 128.30.2.36 80]

W: Failed to fetch http://ftp.us.debian.org/debian/dists/lenny/contrib/binary-i386/Packages.gz  404  Not Found [IP: 128.30.2.36 80]

W: Failed to fetch http://ftp.us.debian.org/debian/dists/lenny/non-free/binary-i386/Packages.gz  404  Not Found [IP: 128.30.2.36 80]

W: Failed to fetch http://security.debian.org/dists/lenny/updates/main/binary-i386/Packages.gz  404  Not Found [IP: 212.211.132.250 80]

W: Failed to fetch http://security.debian.org/dists/lenny/updates/contrib/binary-i386/Packages.gz  404  Not Found [IP: 212.211.132.250 80]

W: Failed to fetch http://security.debian.org/dists/lenny/updates/non-free/binary-i386/Packages.gz  404  Not Found [IP: 212.211.132.250 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Cheesemill on 2013-01-15
Your sources.list is a mess. You are mixing repositories for out of date versions of Ubuntu along with Debian repositories, it's no wonder things aren't working properly.

Can you post the output of...
```
cat /etc/apt/sources.list
```

If you really are using Maverick (10.10) then you should really think about upgrading your OS. 10.10 reached end-of-life nearly a year ago and as such doesn't receive any support, bug-fixes or security updates any more. The repositories for end-of-life versions of Ubuntu are taken off-line, causing some of your issues.

---

### Post by sffvba[e0rt on 2013-01-15
*Thread moved to **General Help** into its own thread.*

Original thread was [http://ubuntuforums.org/showthread.php?t=2028592](http://ubuntuforums.org/showthread.php?t=2028592)


404

---

### Post by ibjsb4 on 2013-01-15
Maverick has reached end of life and Lenny is Debian.

Time for a fresh install.

---

### Post by trantan on 2013-01-15
> **Cheesemill said:**
> Your sources.list is a mess. You are mixing repositories for out of date versions of Ubuntu along with Debian repositories, it's no wonder things aren't working properly.

Can you post the output of...
```
cat /etc/apt/sources.list
```

If you really are using Maverick (10.10) then you should really think about upgrading your OS. 10.10 reached end-of-life nearly a year ago and as such doesn't receive any support, bug-fixes or security updates any more. The repositories for end-of-life versions of Ubuntu are taken off-line, causing some of your issues.

thank you. Now I'm using Ubuntu 11.10. So I have a problem: I cannot create a folder, or edit files in File System. I cannot log in with root account. Can you have me?
Thank you very much!!!

p.s I'm new Linux user, If my question is stupid, please never mind. Thanks.

---

### Post by Maghnus on 2013-07-16
Can I resurrect this thread? I'm have a prob updating.

```
mark@mark-PP150AA-ABA-SR1303WM-NA510:~$ sudo rm -rf /var/lib/apt/lists/*[sudo] password for mark: 
mark@mark-PP150AA-ABA-SR1303WM-NA510:~$ sudo apt-get clean
mark@mark-PP150AA-ABA-SR1303WM-NA510:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,345 B]                            
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]          
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [596 B]                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Get:6 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]                 
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [40.8 kB]            
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg [198 B]                 
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release.gpg                
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg [198 B]      
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed Release.gpg [198 B]       
Get:12 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release [9,759 B]                      
Get:13 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release [5,922 B]                  
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release [40.8 kB]                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:15 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources [2,656 B]          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources [69.1 kB]      
Get:17 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages [4,537 B]    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release [40.8 kB]          
Get:19 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources [2,472 B]                 
Get:20 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [4,266 B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release                    
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release [40.8 kB]        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed Release [40.8 kB]         
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources [877 kB]              
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources [1,964 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources [29.4 kB]  
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources [1,677 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [249 kB] 
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [4,062 B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [71.4 kB]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [3,386 B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [74 B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [71 B]
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en [116 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en [1,494 B]
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en [978 B]
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en [46.7 kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources [5,351 B]       
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources [4,677 kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources [149 kB]        
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages [1,226 kB]      
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages [8,216 B] 
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages [4,468 kB]  
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages [119 kB]  
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex [3,289 B]    
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex [2,265 B]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex [2,263 B]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex [2,640 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main TranslationIndex      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe TranslationIndex  
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources [180 kB]      
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources [3,349 B]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources [72.0 kB] 
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources [3,700 B]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages [440 kB]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [6,645 B]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages [152 kB]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6,363 B]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [72 B]
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages [14 B]
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages [3,296 B]
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages [14 B]
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages [13.6 kB]
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex [72 B]
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex [70 B]
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex [70 B]
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex [73 B]
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/restricted i386 Packages [14 B]
Get:71 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/main i386 Packages [134 kB]
Get:72 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/multiverse i386 Packages [14 B]
Get:73 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/universe i386 Packages [2,351 B]
Get:74 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/main TranslationIndex [73 B]
Get:75 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/multiverse TranslationIndex [70 B]
Get:76 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/restricted TranslationIndex [70 B]
Get:77 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/universe TranslationIndex [72 B]
Get:78 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en [701 kB]       
Get:79 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en [92.6 kB]
Get:80 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en [2,229 B]
Get:81 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en [3,165 kB] 
Get:82 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en [209 kB]
Get:83 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en [3,524 B]
Get:84 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en [1,547 B]
Get:85 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en [92.6 kB]
Get:86 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en [2,292 B]
Get:87 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en [14 B]
Get:88 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en [14 B]
Get:89 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en [11.8 kB]
Get:90 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/main Translation-en [35.8 kB]
Get:91 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/multiverse Translation-en [14 B]
Get:92 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/restricted Translation-en [14 B]
Get:93 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/universe Translation-en [1,552 B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main Sources               
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted Sources         
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe Sources           
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse Sources         
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main i386 Packages         
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted i386 Packages   
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe i386 Packages     
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse i386 Packages   
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main Translation-en        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe Translation-en
Fetched 17.7 MB in 1min 21s (218 kB/s)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
mark@mark-PP150AA-ABA-SR1303WM-NA510:~$ 



```

---

### Post by Irihapeti on 2013-07-16
You are using unsupported versions of Ubuntu that have reached end-of-life status.

You need to either upgrade (which can be risky) or do a clean install of a supported version. To help in choosing a version, it would be useful if you gave us the details of your machine.

Before you do either, I strongly recommend doing a backup of your user files.

---

