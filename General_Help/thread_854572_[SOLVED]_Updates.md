---
title: "[SOLVED] Updates"
date: 2008-07-09
forum: General Help
---

### Post by pikabuntu on 2008-07-09
One time my computer locked up when I was updating it and I didn't know what else to do, so I shut it down.  Now, it acts strange with updates.  It always says something like "Last update was 53 days ago" and stuff like that.  What can I do to fix this?

---

### Post by Elfy on 2008-07-09
What error do you get if you run this in a terminal- please paste output

```
sudo apt-get update
```

If no error

```
sudo apt-get upgrade
```

---

### Post by pmlxuser on 2008-07-09
just do a sudo apt-get check  (this checks if there are broken dependencies- which i believ is the case)

there-after just do 
sudo apt-get update (it will reconfigure the updates to show the right info)

---

### Post by youthforlinux on 2008-07-09
does dpkg give errors when you try to install software...
try ```
sudo dpkg --configure -a
```

---

### Post by pikabuntu on 2008-07-09
forest pixie this is what i got: 

zach@Ubuntu:~$ sudo apt-get update
[sudo] password for zach: 
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release.gpg
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US                                
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US                          
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release                                               
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages                                         
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages                                   
Err cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages                                         
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages                                   
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [189B]                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                                                              
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                      
Get:2 [http://archive.canonical.com](http://archive.canonical.com) hardy Release [6998B]                                   
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                                           
Get:4 [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Release.gpg [189B]                                          
Ign [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Translation-en_US                                             
Get:5 [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Release [692B]                    
Ign [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Release                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                           
Get:6 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources [826B]                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US           
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]     
Ign [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US                       
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg [189B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                          
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages [2432B]                                
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]                           
Get:11 [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Packages [21.7kB]        
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources [1024B]                                                                  
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release [58.5kB]                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources                                                                        
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages [15.3kB]                                                 
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages [6626B]                                                  
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages [71.2kB]                                                   
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages [278kB]                                                        
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources [2279B]                                                   
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources [907B]                                                    
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources [15.5kB]                                                    
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources [79.3kB]                                                        
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages [3465B]                                                 
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages [6156B]                                                 
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages [21.1kB]                                                  
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages [31.0kB]                                                      
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources [14B]                                                    
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources [906B]                                                   
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources [3308B]                                                    
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources [7805B]                                                        
Fetched 722kB in 26s (27.3kB/s)                                                                                             
W: GPG error: [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 058A05E90C4ECFEC
W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
zach@Ubuntu:~$

---

### Post by pmlxuser on 2008-07-09
> **pikabuntu said:**
> forest pixie this is what i got: 

zach@Ubuntu:~$ sudo apt-get update
[sudo] password for zach: 

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
zach@Ubuntu:~$

just go to Synaptic Package manager >Settings>Repositories Uncheck CDROM Ubuntu -- and run command again

---

### Post by pikabuntu on 2008-07-09
> **pmlxuser said:**
> just do a sudo apt-get check  (this checks if there are broken dependencies- which i believ is the case)

there-after just do 
sudo apt-get update (it will reconfigure the updates to show the right info)

after i did this :

zach@Ubuntu:~$ sudo apt-get check
[sudo] password for zach: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
zach@Ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release.gpg
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US                                
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US                          
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release                                               
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages                                         
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages                                   
Err cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages                                         
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages                                   
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US                                                            
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                                                                          
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                             
Get:1 [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Release.gpg [189B]         
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                                                            
Ign [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Translation-en_US                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages        
Get:3 [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Release [692B]             
Ign [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Ign [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Get:4 [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Packages [21.7kB]
Fetched 22.6kB in 2s (8694B/s)   
W: GPG error: [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 058A05E90C4ECFEC
W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
zach@Ubuntu:~$

---

### Post by pikabuntu on 2008-07-09
> **pmlxuser said:**
> just go to Synaptic Package manager >Settings>Repositories Uncheck CDROM Ubuntu -- and run command again

W: GPG error: [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 058A05E90C4ECFEC
W: You may want to run apt-get update to correct these problems
zach@Ubuntu:~$

EDIT: Also, what should i do if it locks up like that again in the middle of an update or something like that?

---

### Post by pikabuntu on 2008-07-09
> **youthforlinux said:**
> does dpkg give errors when you try to install software...
try ```
sudo dpkg --configure -a
```

zach@Ubuntu:~$ sudo dpkg --configure -a
[sudo] password for zach: 
zach@Ubuntu:~$

---

### Post by Elfy on 2008-07-10
If it's still not working post sources list please

```
cat /etc/apt/sources.list
```

---

### Post by youthforlinux on 2008-07-10
well dpkg isn't broken really its probably your sources.list file also for [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) edgy/  your using the edgy repo and your're using hardy...i checked there is a hardy one to correct this problem remove the current archive.ubuntulinux.jp entry in /etc/apt/sources.list and then add this instead:

deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) hardy/

then in the terminal:

```
sudo aptitude install ubuntu-ja-keyring
``` to correct the error

then try:
 ```
sudo aptitude update
```

at least this will fix the one problem i just tested it out

---

