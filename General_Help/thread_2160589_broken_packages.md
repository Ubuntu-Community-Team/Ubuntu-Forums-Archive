---
title: "broken packages"
date: 2013-07-07
forum: General Help
---

### Post by mkocs on 2013-07-07
hi :)
i'm quite new to ubuntu and i tried to install Synaptic, but since 2 days i always get this message: 
> mko@ubuntu:~$ sudo apt-get install synaptic
[sudo] password for mko: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 synaptic : Depends: libept1.4.12 (>= 1.0.9) but it is not installable
            Recommends: rarian-compat but it is not installable
_**E: Unable to correct problems, you have held broken packages.**_
mko@ubuntu:~$ 

when i try to download it from the software-center i get this:
> The following packages have unmet dependencies:

synaptic: Depends: libc6 (>= 2.14) but 2.17-0ubuntu5 is to be installed
          Depends: libept1.4.12 (>= 1.0.9) but it is not going to be installed
          Depends: libgcc1 (>= 1:4.1.1) but 1:4.7.3-1ubuntu1 is to be installed
          Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.28.0-0ubuntu1 is to be installed
          Depends: libglib2.0-0 (>= 2.14.0) but 2.36.0-1ubuntu2 is to be installed
          Depends: libgtk-3-0 (>= 3.0.0) but 3.6.4-0ubuntu8 is to be installed
          Depends: libpango1.0-0 (>= 1.14.0) but 1.32.5-0ubuntu1 is to be installed
          Depends: libstdc++6 (>= 4.6) but 4.7.3-1ubuntu1 is to be installed
          Depends: libvte-2.90-9 (>= 1:0.27.2) but 1:0.34.2-0ubuntu2 is to be installed

I used Google to find a solution, but nothing helped. 
i tried "sudo apt-get install -f" but then i get: 
> mko@ubuntu:~$ sudo apt-get install -f
[sudo] password for mko: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove_** and 1 not upgraded.**_
mko@ubuntu:~$ 

1 not upgraded? is this the broken package?
I tried everything i found on Google. I also opened the Software-Center, which suddenly said something like "There are broken packages, let me repair them". I clicked the REPAIR-Button but nothing happened. 

I use Ubuntu 13.04 (64bit).


Thanks for your help,
mko :D

---

### Post by kleenex on 2013-07-07
Hi **mkocs**. Please try something like:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Max Blyss on 2013-07-07
sudo apt-get dist-upgrade might upgrade the non-upgraded package for ya there...

---

### Post by mkocs on 2013-07-07
@kleenex
> mko@ubuntu:~$ sudo apt-get clean
[sudo] password for mko: 
mko@ubuntu:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://repository.spotify.com](http://repository.spotify.com) stable Release.gpg                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release.gpg                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://repository.spotify.com](http://repository.spotify.com) stable Release                               
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates Release.gpg                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release.gpg                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce Release                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates Release                            
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages/DiffIndex    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages/DiffIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release                        
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe amd64 Packages                
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-de               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-de                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe amd64 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en_US     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-de        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-de              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-de                        
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-de
Err [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages
  gnutls_handshake() failed: A TLS packet with unexpected length was received.
Err [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages             
  gnutls_handshake() failed: A TLS packet with unexpected length was received.
Err [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/main Sources                     
  404  Not Found [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/restricted Sources
  404  Not Found [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/universe Sources
  404  Not Found [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/multiverse Sources
  404  Not Found [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/main amd64 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/universe amd64 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/main i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/restricted i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/main Translation-de
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/multiverse Translation-de
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/restricted Translation-de
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) sauce-security/universe Translation-de
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-de
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/main Sources     
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/main Translation-de
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/multiverse Translation-de
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/restricted Translation-de
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce/universe Translation-de
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/main Translation-de
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/multiverse Translation-de
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/restricted Translation-de
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-updates/universe Translation-de
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/main Translation-de
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/multiverse Translation-de
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/restricted Translation-de
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/universe Translation-de
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/sauce-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/sauce-security/main/source/Sources)  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/sauce-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/sauce-security/restricted/source/Sources)  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/sauce-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/sauce-security/universe/source/Sources)  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/sauce-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/sauce-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/sauce-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/sauce-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/sauce-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/sauce-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/sauce-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/sauce-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/sauce-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/sauce-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/sauce-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/sauce-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/sauce-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/sauce-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/sauce-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/sauce-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/sauce-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/sauce-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/sauce/main/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/sauce/restricted/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/sauce/universe/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/sauce/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/sauce-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/sauce-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/sauce-updates/universe/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/sauce-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-updates/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-updates/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-updates/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-updates/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-updates/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-updates/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-updates/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu/dists/precise/main/binary-amd64/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu/dists/precise/main/binary-amd64/Packages)  gnutls_handshake() failed: A TLS packet with unexpected length was received.

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/sauce-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-backports/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/sauce-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-backports/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/sauce-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-backports/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/sauce-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-backports/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-backports/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-backports/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-backports/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-backports/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-backports/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-backports/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-backports/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/sauce-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/sauce-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu/dists/precise/main/binary-i386/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu/dists/precise/main/binary-i386/Packages)  gnutls_handshake() failed: A TLS packet with unexpected length was received.

E: Some index files failed to download. They have been ignored, or old ones used instead.
mko@ubuntu:~$ sudo apt-get upgrade
[sudo] password for mko: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  five-or-more
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2.628 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates/universe five-or-more amd64 1:3.8.0-0ubuntu1.1 [2.628 kB]
Fetched 2.628 kB in 34s (77,2 kB/s)                                            
(Reading database ... 265963 files and directories currently installed.)
Preparing to replace five-or-more 1:3.8.0-0ubuntu1 (using .../five-or-more_1%3a3.8.0-0ubuntu1.1_amd64.deb) ...
Unpacking replacement five-or-more ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for man-db ...
Setting up five-or-more (1:3.8.0-0ubuntu1.1) ...
mko@ubuntu:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 synaptic : Depends: libept1.4.12 (>= 1.0.9) but it is not installable
            Recommends: rarian-compat but it is not installable
E: Unable to correct problems, you have held broken packages.
mko@ubuntu:~$ 

hmm it didn't help :( but thanks for the tip :D

@Max Blyss
> mko@ubuntu:~$ sudo apt-get dist-upgrade
[sudo] password for mko: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mko@ubuntu:~$ 



thank you for your help!

---

### Post by grahammechanical on 2013-07-07
May I suggest that you remove any PPAs from your software sources. They are useful for initially installing software but often cause problems like this after installation. Another thing that concerns me is that you are on raring but you have repositories for something called sauce. I am running Saucy Salamander and I see stuff like [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Translation-en_GB.

I am not worried when I see Ign for some of these repositories because it only indicates that some packages are being held because they are dependent on other packages that are not yet in the repositories. But In your case I wonder why you have repositories for stuff called [http://archive.ubuntu.com](http://archive.ubuntu.com) sauce-backports/main Translation-en_US.

Regards.

---

### Post by mkocs on 2013-07-07
1. What are PPAs? :D
2. How can i remove them?

Sorry for this dumb questions, but I'm totally new to this. Does someone have something like a "Beginner's guide" for Ubuntu/Linux?

thanks,
mko

---

### Post by mc4man on 2013-07-07
post rsults of below
(did you try to add "saucy" & use 'sauce' instead?
```
 cat /etc/apt/sources.list
```
```
ls /etc/apt/sources.list.d
```

---

### Post by deadflowr on 2013-07-07
What Ubuntu version is sauce?
I would recommend deleting all references to that.
Stick the raring repos for now.

---

### Post by mkocs on 2013-07-08
@mc4man
```
**mko@ubuntu:~$  cat /etc/apt/sources.list**
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ sauce main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ sauce main restricted
deb-src http://archive.ubuntu.com/ubuntu/ sauce main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ sauce-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ sauce-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ sauce universe
deb-src http://archive.ubuntu.com/ubuntu/ sauce universe
deb http://archive.ubuntu.com/ubuntu/ sauce-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ sauce-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ sauce multiverse
deb-src http://archive.ubuntu.com/ubuntu/ sauce multiverse
deb http://archive.ubuntu.com/ubuntu/ sauce-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ sauce-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ sauce-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ sauce-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu sauce-security main restricted
deb-src http://security.ubuntu.com/ubuntu sauce-security main restricted
deb http://security.ubuntu.com/ubuntu sauce-security universe
deb-src http://security.ubuntu.com/ubuntu sauce-security universe
deb http://security.ubuntu.com/ubuntu sauce-security multiverse
deb-src http://security.ubuntu.com/ubuntu sauce-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu sauce partner
# deb-src http://archive.canonical.com/ubuntu sauce partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu sauce main
# deb-src http://extras.ubuntu.com/ubuntu sauce main
deb http://repository.spotify.com stable non-free

deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://security.ubuntu.com/ubuntu/ raring-security universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
**mko@ubuntu:~$ ls /etc/apt/sources.list.d**
canonical-qt5-edgers-qt5-proper-raring.list
canonical-qt5-edgers-qt5-proper-raring.list.save
nilarimogard-webupd8-raring.list
nilarimogard-webupd8-raring.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
ubuntu-sdk-team-ppa-raring.list
ubuntu-touch-coreapps-drivers-daily-raring.list
ubuntu-touch-coreapps-drivers-daily-raring.list.save
webupd8team-pulseaudio-eq-raring.list
webupd8team-pulseaudio-eq-raring.list.save
mko@ubuntu:~$ 

```

@deadflowr
i don't know which version this is :D

---

### Post by mkocs on 2013-07-08
i tried to update to 13.10 but i couldn't. It came to the 2nd step and then stopped because of this "http://security.ubuntu.com/ubuntu/dists/sauce-security/main/source/Sources".  What is this sauce? 
I can't install ANY software. 

mko

---

### Post by deadflowr on 2013-07-08
> **mkocs said:**
> i tried to update to 13.10 but i couldn't. It came to the 2nd step and then stopped because of this "http://security.ubuntu.com/ubuntu/dists/sauce-security/main/source/Sources".  What is this sauce? 
I can't install ANY software. 

mko

Like I wrote before, remove/comment out all instances of sauce from the sources.list.
Then run an update and see what else needs fixing.
To do this run
```
gksu gedit /etc/apt/sources.list
```
and then add a# symbol to the front of every line that has sauce in it.

Then save and run an update.

Example
This line
```
[COLOR=#000000][FONT=Ubuntu Mono]deb http://archive.ubuntu.com/ubuntu/ sauce main restricted[/FONT][/COLOR]
```

changes to this
```
#[COLOR=#000000][FONT=Ubuntu Mono]deb http://archive.ubuntu.com/ubuntu/ sauce main restricted[/FONT][/COLOR]
```

---

### Post by mkocs on 2013-07-09
okay i changed it to this now:
```
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ sauce main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
#deb http://archive.ubuntu.com/ubuntu/ sauce main restricted
#deb-src http://archive.ubuntu.com/ubuntu/ sauce main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://archive.ubuntu.com/ubuntu/ sauce-updates main restricted
#deb-src http://archive.ubuntu.com/ubuntu/ sauce-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
#deb http://archive.ubuntu.com/ubuntu/ sauce universe
#deb-src http://archive.ubuntu.com/ubuntu/ sauce universe
#deb http://archive.ubuntu.com/ubuntu/ sauce-updates universe
#deb-src http://archive.ubuntu.com/ubuntu/ sauce-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb http://archive.ubuntu.com/ubuntu/ sauce multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ sauce multiverse
#deb http://archive.ubuntu.com/ubuntu/ sauce-updates multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ sauce-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://archive.ubuntu.com/ubuntu/ sauce-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ sauce-backports main restricted universe multiverse

#deb http://security.ubuntu.com/ubuntu sauce-security main restricted
#deb-src http://security.ubuntu.com/ubuntu sauce-security main restricted
#deb http://security.ubuntu.com/ubuntu sauce-security universe
#deb-src http://security.ubuntu.com/ubuntu sauce-security universe
#deb http://security.ubuntu.com/ubuntu sauce-security multiverse
#deb-src http://security.ubuntu.com/ubuntu sauce-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu sauce partner
# deb-src http://archive.canonical.com/ubuntu sauce partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu sauce main
# deb-src http://extras.ubuntu.com/ubuntu sauce main
deb http://repository.spotify.com stable non-free

deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://security.ubuntu.com/ubuntu/ raring-security universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-proposed universe
```

Terminal throws this:
```
mko@ubuntu:~$ sudo apt-get update
Hit http://repository.spotify.com stable Release.gpg
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://security.ubuntu.com raring-security Release.gpg                     
Hit http://repository.spotify.com stable Release                     
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://security.ubuntu.com raring-security Release               
Hit http://us.archive.ubuntu.com raring Release.gpg                            
Hit http://repository.spotify.com stable/non-free amd64 Packages     
Hit http://ppa.launchpad.net raring Release.gpg                      
Hit http://repository.spotify.com stable/non-free i386 Packages      
Hit http://security.ubuntu.com raring-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates Release.gpg          
Hit http://ppa.launchpad.net raring Release.gpg                      
Hit http://security.ubuntu.com raring-security/universe i386 Packages
Hit http://ppa.launchpad.net raring Release.gpg                      
Hit http://us.archive.ubuntu.com raring-proposed Release.gpg         
Hit http://ppa.launchpad.net raring Release                          
Hit http://security.ubuntu.com raring-security/universe Translation-en         
Hit http://us.archive.ubuntu.com raring Release                                
Hit http://ppa.launchpad.net raring Release                                    
Hit http://ppa.launchpad.net raring Release                                    
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit http://us.archive.ubuntu.com raring-updates Release                        
Hit http://ppa.launchpad.net raring Release                                    
Hit https://private-ppa.launchpad.net precise Release                          
Hit http://ppa.launchpad.net raring Release                                    
Hit http://us.archive.ubuntu.com raring-proposed Release                       
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit http://ppa.launchpad.net raring/main amd64 Packages                        
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit https://private-ppa.launchpad.net precise/main i386 Packages     
Hit http://us.archive.ubuntu.com raring/universe amd64 Packages                
Hit http://us.archive.ubuntu.com raring/universe i386 Packages                 
Ign http://repository.spotify.com stable/non-free Translation-en_US  
Hit http://ppa.launchpad.net raring/main amd64 Packages              
Ign http://security.ubuntu.com raring-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com raring/universe Translation-en      
Ign http://repository.spotify.com stable/non-free Translation-en     
Ign http://security.ubuntu.com raring-security/universe Translation-de
Hit http://us.archive.ubuntu.com raring/universe Translation-de      
Ign http://repository.spotify.com stable/non-free Translation-de     
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe i386 Packages
Hit http://ppa.launchpad.net raring/main amd64 Packages
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en
Hit http://ppa.launchpad.net raring/main amd64 Packages
Hit http://us.archive.ubuntu.com raring-proposed/universe amd64 Packages
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://us.archive.ubuntu.com raring-proposed/universe i386 Packages
Hit http://ppa.launchpad.net raring/main amd64 Packages
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://us.archive.ubuntu.com raring-proposed/universe Translation-en
Hit http://us.archive.ubuntu.com raring-proposed/universe Translation-de
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-de
Ign http://us.archive.ubuntu.com raring-proposed/universe Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-de
Ign http://ppa.launchpad.net raring/main Translation-de
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-de
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-de
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-de
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-de
Reading package lists... Done
mko@ubuntu:~$
```

No errors! :D thank you

---

### Post by claracc on 2013-07-09
> **mkocs said:**
> i tried to update to 13.10 but i couldn't. It came to the 2nd step and then stopped because of this "http://security.ubuntu.com/ubuntu/dists/sauce-security/main/source/Sources".  What is this sauce? 
I can't install ANY software. 

mko

When I write in browser this address: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) sauce main restricted I obtain this answer:
```
Not Found

The requested URL /ubuntu/ sauce main restricted was not found on this server.
Apache/2.2.22 (Ubuntu) Server at archive.ubuntu.com Port 80
```

As all your sources.list file is full of "sauce" packages and they are not found, you have problems updating. You don't know what sauce is but I neither. I know about saucy, the ubuntu development release (13.10)

I think, the best thing to do is to regenerate your sources.list file in one of the two ways provided by this thread:

[http://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories](http://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories)

Try then to update and if all works well, then you can add the third party repositories (as you have for spotify).

---

### Post by mkocs on 2013-07-09
Ok, everything is working now! 

Thank y'all! :D

---

### Post by mkocs on 2013-07-09
And special thanks to: [**[COLOR=#000000]deadflowr[/COLOR]**]("http://ubuntuforums.org/member.php?u=1276577")! 
He/she fixed my problems :D

---

