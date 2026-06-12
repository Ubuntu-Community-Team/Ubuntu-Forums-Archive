---
title: "apt-get conflict with LC_TYPE=&quot;zh_CN.GB18030&quot;?"
date: 2007-12-10
forum: General Help
---

### Post by sandorf on 2007-12-10
Hi, I've just installed Gusty. I make intensive use of text files encoded in GB Chinese so I generated the zh_CN.GB18030 locale and set LC_CTYPE="zh_CN.GB18030" in /etc/environment. Other locale settings were kept as default. I also added Chinese in the language support dialog box and checked "Enable support to enter complex characters". Scim worked properly after that.

But later that day I found 'sudo apt-get update' didn't work and constantly reported the "404 not found" error, while my network connection was certainly working well. I proceeded to undo what I have done to /etc/environment and unchecked the "Enable support to enter complex characters" checkbox. (myteriously after a reboot the checkbox remained checked) Then apt-get update worked fine.

Is this a known bug of Gutsy? I really need the GB Chinese support so please give me some clue. Thanks!

---

### Post by sandorf on 2007-12-12
does anybody has anything to say on this strange problem?

---

### Post by sandorf on 2007-12-13
I'm still pested by this problem...

---

### Post by sandorf on 2007-12-16
This problem is still annoying me. And I don't have any clue! Funny I'm the only one in the world to have this problem!

---

### Post by sandorf on 2007-12-17
up

---

### Post by sandorf on 2007-12-21
Nobody experienced this? Can you believe this f*cking Gusty will fail me on such common settings?


[COLOR="Red"]fang@fang-desktop:~$ export LC_CTYPE="zh_CN.GBK"
fang@fang-desktop:~$ sudo apt-get update[/COLOR]
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release.gpg
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US                                                
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US                                          
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release                                                               
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Packages                                                         
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Packages                                                   
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Packages                                                         
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Packages                                                   
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign [http://cl.naist.jp](http://cl.naist.jp) gutsy Release.gpg                                                                                                     
Ign [http://cl.naist.jp](http://cl.naist.jp) gutsy/all Translation-en_US                                                                                           
Ign [http://cl.naist.jp](http://cl.naist.jp) gutsy Release                                                                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                                                                                           
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US                                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US                       
Ign [http://cl.naist.jp](http://cl.naist.jp) gutsy/all Packages                                                  
Ign [http://cl.naist.jp](http://cl.naist.jp) gutsy/all Sources                                                   
Err [http://cl.naist.jp](http://cl.naist.jp) gutsy/all Packages                            
  404 Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Err [http://cl.naist.jp](http://cl.naist.jp) gutsy/all Sources                             
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources     
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
  404 Not Found [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources               
58% [Waiting for headers] [Waiting for headers] [Waiting for headers]
[COLOR="Red"]fang@fang-desktop:~$ export LC_CTYPE="en_US.UTF-8"
fang@fang-desktop:~$ sudo apt-get update[/COLOR]
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release.gpg
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US                                                
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US                                          
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release                                                               
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Packages                                                         
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Packages                                                   
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Packages                                                         
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Packages                                                   
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://cl.naist.jp](http://cl.naist.jp) gutsy Release.gpg [189B]                                                                                            
Ign [http://cl.naist.jp](http://cl.naist.jp) gutsy/all Translation-en_US                                                                                           
Hit [http://cl.naist.jp](http://cl.naist.jp) gutsy Release                                                                                                         
Hit [http://cl.naist.jp](http://cl.naist.jp) gutsy/all Packages                                                                                                    
Hit [http://cl.naist.jp](http://cl.naist.jp) gutsy/all Sources                             
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US     
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages [1075kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
76% [7 Packages 767960/1075kB 71%]

---

