---
title: "504 Gateway Timing Out While Running sudo apt-get update"
date: 2012-10-21
forum: General Help
---

### Post by Thelinuxgeek on 2012-10-21
I'm getting 504 errors every time I try to update, whether through the software updater or through the terminal. Here's the complete list:

isaac@Flappy:~$ sudo apt-get update
[sudo] password for isaac: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal InRelease                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates InRelease           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports InRelease         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main amd64 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted amd64 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe amd64 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources
  504  Gateway Time-out [IP: 91.189.92.152 80]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages
  504  Gateway Time-out [IP: 91.189.92.152 80]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages
  504  Gateway Time-out [IP: 91.189.92.152 80]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  504  Gateway Time-out [IP: 91.189.92.152 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages)  504  Gateway Time-out [IP: 91.189.92.152 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  504  Gateway Time-out [IP: 91.189.92.152 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


Anyone got advice on how to avoid timing out?

---

### Post by claracc on 2012-10-22
When I click in any of the problematic url's, I obtain:

> Not Found

The requested URL /ubuntu/dists/quantal/main/source/Sources was not found on this server.
Apache/2.2.8 (Ubuntu) Server at extras.ubuntu.com Port 80

So, I think it is a problem with the server you are using to get updates.

I would try to change the server in the software sources.

---

### Post by Thelinuxgeek on 2012-10-22
> **claracc said:**
> When I click in any of the problematic url's, I obtain:



So, I think it is a problem with the server you are using to get updates.

I would try to change the server in the software sources.

I'll try it. Hopefully this will be fixed soon!

---

### Post by manurincon on 2012-10-23
It seems the problem is only with the "extras" server. (IP 91.189.92.152: 80) You can deactivate it till it works with a hash in the sources.list file (/etc/apt/sources.list).

---

### Post by nekroskoma on 2012-10-25
im having this same problem, i dont want to disable these sources since im trying to install somehting from them

so ill wait for a solution

---

