---
title: "No cnijfilter?"
date: 2014-01-31
forum: General Help
---

### Post by Steve_Badger on 2014-01-31
Hi everybody, 

I just installed Ubuntu 13.10 on this laptop but I have been using linux for a year now. This laptop will not work with my Canon MX880 series printer even though my other laptop with Linux Mint 16 Petra does. The reason is I can't find the cnijfilter for it. My Mint laptop has it and works just fine but I cannot find the filter through Synaptic Package Manager or grab it in from the terminal but I can with the Mint laptop. I have all the other drivers installed just fine but the printer just doesn't work without this filter. 

Tried just getting it from terminal and this is what I get. Again, my other laptop with Mint 16 can do this fine.

sudo apt-get install cnijfilter-mx880series
Reading package lists... Done
Building dependency tree       m
Reading state information... Done
E: Unable to locate package cnijfilter-mx880series


Is there any way for me to get this? I don't have a printer without it.

Thanks.

---

### Post by dragonfly41 on 2014-01-31
[http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html](http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html)

---

### Post by Steve_Badger on 2014-01-31
> **dragonfly41 said:**
> [http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html](http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html)


I've already tried this. It didn't work. It can't find it for whatever reason.

$ sudo apt-get install cnijfilter-mx880series
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cnijfilter-mx880series

---

### Post by deadflowr on 2014-01-31
Did you run a package update first, after adding the ppa
```
sudo apt-get update
```
hopefully the ppa still exists, and if it doesn't then the update will output errors.
When the update finishes, then run the install command.

---

### Post by Steve_Badger on 2014-01-31
> **deadflowr said:**
> Did you run a package update first, after adding the ppa
```
sudo apt-get update
```
hopefully the ppa still exists, and if it doesn't then the update will output errors.
When the update finishes, then run the install command.

Yeah I tried this already but here it is anyway. My system is already up to date. I've also done the apt-get upgrade as well.

Any other ideas?


$ sudo apt-get update
[sudo] password for steve: 
Ign [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 InRelease
Hit [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 Release.gpg                             
Hit [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy InRelease                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease                        
Hit [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/contrib amd64 Packages        
Hit [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/contrib i386 Packages         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates InRelease                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg                                 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg [933 B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports InRelease                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release.gpg                             
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release [49.6 kB]              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release.gpg [933 B]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main amd64 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                          
Ign [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/contrib Translation-en_US               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release [49.6 kB]    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources [27.9 kB]         
Ign [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/contrib Translation-en                  
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources [14 B]      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports Release              
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources [8,372 B]     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Sources                            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources [691 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Sources             
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main amd64 Packages [78.5 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main amd64 Packages                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted amd64 Packages               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe amd64 Packages        
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted amd64 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse amd64 Packages        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe amd64 Packages [31.3 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main i386 Packages               
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse amd64 Packages [1,160 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted i386 Packages         
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages [78.2 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse i386 Packages
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages [31.6 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages [1,401 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Sources [68.7 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Sources [14 B]    
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Sources [45.9 kB]   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en          
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Sources [1,357 B] 
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main amd64 Packages [196 kB] 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US     
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted amd64 Packages [14 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe amd64 Packages [134 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US       
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse amd64 Packages [1,567 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main i386 Packages [195 kB]  
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe i386 Packages [135 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse i386 Packages [1,774 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main amd64 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US
Fetched 1,141 kB in 26s (43.4 kB/s)
Reading package lists... Done

---

### Post by deadflowr on 2014-01-31
You have an openprinting repo, but you didn't add the one from the link.
```
sudo add-apt-repository ppa:michael-gruz/canon
```
then run the update command again.

---

### Post by Steve_Badger on 2014-01-31
> **deadflowr said:**
> You have an openprinting repo, but you didn't add the one from the link.
```
sudo add-apt-repository ppa:michael-gruz/canon
```
then run the update command again.

Okay. I added it and ran the update command and this is what I got.

steve@steve-VGN-FW140E:~$ sudo add-apt-repository ppa:michael-gruz/canon
[sudo] password for steve: 
 
 More info: [https://launchpad.net/~michael-gruz/+archive/canon](https://launchpad.net/~michael-gruz/+archive/canon)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmphha68c/secring.gpg' created
gpg: keyring `/tmp/tmphha68c/pubring.gpg' created
gpg: requesting key 3F7B4A1D from hkp server keyserver.ubuntu.com
gpg: /tmp/tmphha68c/trustdb.gpg: trustdb created
gpg: key 3F7B4A1D: public key "Launchpad Misakovi" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
steve@steve-VGN-FW140E:~$ sudo apt-get update
Ign [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 InRelease
Hit [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 Release.gpg                             
Hit [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy InRelease                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Hit [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/contrib amd64 Packages                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Hit [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/contrib i386 Packages                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates InRelease                       
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg [933 B]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports InRelease                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release [49.6 kB]              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                                
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release.gpg [933 B]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main amd64 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports Release.gpg                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                          
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources [27.9 kB]         
Ign [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/contrib Translation-en_US               
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release [49.6 kB]             
Ign [http://www.openprinting.org](http://www.openprinting.org) lsb3.2/contrib Translation-en                  
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources [14 B]      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports Release                       
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources [8,372 B]     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Sources                            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources [691 B]     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Sources                      
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main amd64 Packages [78.5 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Sources                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main amd64 Packages                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse amd64 Packages               
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted amd64 Packages [14 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe amd64 Packages [31.3 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main i386 Packages                      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages                         
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted i386 Packages       
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse amd64 Packages [1,160 B]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                          
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe i386 Packages         
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages [78.2 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en        
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages [31.6 kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages [1,401 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Sources [68.7 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en          
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Sources [14 B]    
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Sources [45.9 kB]   
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Sources [1,357 B] 
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main amd64 Packages [196 kB] 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US       
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted amd64 Packages [14 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe amd64 Packages [134 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse amd64 Packages [1,567 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main i386 Packages [195 kB]  
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe i386 Packages [135 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse i386 Packages [1,774 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main amd64 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US
Fetched 1,141 kB in 31s (36.6 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by deadflowr on 2014-01-31
I see that ppa hasn't been updated for quite a while.
first let's remove it
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo add-apt-repository --remove ppa:michael-gruz/canon[/FONT][/COLOR]
```
The run
```
sudo add-apt-repository ppa:michael-gruz/canon-trunk
```
now try updating it.
then install

You can also delete the old-dead-ppa file in the sources.list.d folder. if you want.
should be
```
sudo rm /etc/apt/sources.list.d/michael-gruz-canon-saucy.list
```
but run
```
ls /etc/apt/sources.list.d
```
first to be sure.
 removing the file should not be needed.

---

### Post by Steve_Badger on 2014-01-31
Perfect! It worked.  I ran through those steps and then reconfigured the printer. Thank you very much!

---

