---
title: "Can't install Steam In 12.10"
date: 2013-01-16
forum: General Help
---

### Post by ChaosChris2009 on 2013-01-16
I receive the error in the attached screenshot when I click the Steam .deb 

I've tried following and using suggested terminal commands from the valve wiki for Linux (Ubuntu 12.10 in my case), still to no avail

[Steam for Linux wiki](https://wiki.ubuntu.com/Valve)

This is the output/error(s) I receive when running the commands via Terminal

```
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$     sudo add-apt-repository ppa:abhshk-btra/rotatingcanvas
You are about to add the following PPA to your system:
 Open source contributions by Rotating Canvas.
http://www.rotatingcanvas.com
 More info: https://launchpad.net/~abhshk-btra/+archive/rotatingcanvas
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpcahf48/secring.gpg' created
gpg: keyring `/tmp/tmpcahf48/pubring.gpg' created
gpg: requesting key 1D9FA06D from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpcahf48/trustdb.gpg: trustdb created
gpg: key 1D9FA06D: public key "Launchpad PPA for abhishekbatra" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get update && sudo apt-get install googleplaylens
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal InRelease
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main Translation-en_US
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main Translation-en
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted Translation-en_US
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted Translation-en
Ign http://archive.ubuntu.com quantal InRelease                                
Ign http://security.ubuntu.com quantal-security InRelease                      
Ign http://ppa.launchpad.net quantal InRelease                                 
Ign http://archive.ubuntu.com quantal-updates InRelease
Get:1 http://security.ubuntu.com quantal-security Release.gpg [933 B]
Ign http://ppa.launchpad.net quantal Release.gpg                               
Hit http://archive.ubuntu.com quantal Release.gpg
Get:2 http://security.ubuntu.com quantal-security Release [49.6 kB]
Ign http://ppa.launchpad.net quantal Release                                 
Get:3 http://archive.ubuntu.com quantal-updates Release.gpg [933 B]          
Hit http://archive.ubuntu.com quantal Release                                  
Get:4 http://archive.ubuntu.com quantal-updates Release [49.6 kB]        
Get:5 http://security.ubuntu.com quantal-security/main i386 Packages [65.8 kB]
Hit http://archive.ubuntu.com quantal/main i386 Packages                       
Get:6 http://security.ubuntu.com quantal-security/restricted i386 Packages [14 B]
Hit http://archive.ubuntu.com quantal/restricted i386 Packages                 
Hit http://security.ubuntu.com quantal-security/main Translation-en   
Hit http://archive.ubuntu.com quantal/main Translation-en
Hit http://security.ubuntu.com quantal-security/restricted Translation-en
Hit http://archive.ubuntu.com quantal/restricted Translation-en
Get:7 http://archive.ubuntu.com quantal-updates/main i386 Packages [169 kB]
Get:8 http://archive.ubuntu.com quantal-updates/restricted i386 Packages [1,979 B]
Ign http://security.ubuntu.com quantal-security/main Translation-en_US         
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US   
Hit http://archive.ubuntu.com quantal-updates/main Translation-en     
Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Hit http://archive.ubuntu.com quantal-updates/restricted Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://archive.ubuntu.com quantal/main Translation-en_US                   
Ign http://archive.ubuntu.com quantal/restricted Translation-en_US             
Ign http://archive.ubuntu.com quantal-updates/main Translation-en_US           
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en_US     
Fetched 338 kB in 6s (48.6 kB/s)                                               
W: Failed to fetch http://ppa.launchpad.net/abhshk-btra/rotatingcanvas/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/abhshk-btra/rotatingcanvas/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

