---
title: "Why am I asked for the CD?"
date: 2007-04-20
forum: General Help
---

### Post by Zdravko on 2007-04-20
Why am I asked for the CD when I try to install C++ compilers?
> zdravko@ubuntu:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libneon26 libxcb1 libxcb-xlib0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 3682kB/8050kB of archives.
After unpacking 33.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main linux-libc-dev 2.6.20-15.27 [664kB]
Media change: please insert the disc labeled
 'Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.2)'
in the drive '/cdrom/' and press enter


---

### Post by etherealremnant on 2007-04-20
open terminal and type:

sudo nano /etc/apt/sources.list

Remove the line that refers to the CD near the top of it. Save it using Ctrl-O. Then update your repos and the problem should be solved.

---

### Post by Zdravko on 2007-04-20
How do I upgrade the repos?

---

### Post by shinythings on 2007-04-20
```
sudo aptitude update
```

---

### Post by Zdravko on 2007-04-20
Why do I get this?
> zdravko@ubuntu:~$ sudo aptitude update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                                                                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                                                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                                                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                                                                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                                                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                                                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                                                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages                                                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                                                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages                                                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources                                                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources                                                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages                                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources                                                                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources                                                                                             
Fetched 3B in 1m25s (0B/s)                                                                                                                                   
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache


---

### Post by zenwalker on 2007-04-20
Its checking the sources repo and its health like that while updating itself with the repos.

Dont worry, it wont do any harm for you nor for your system. So enjoy.

Oh sorry i forgot about that error. While accessing with apt or synptic or simialr. Dont open up other application like that. Also do that with root permission.

---

### Post by Zdravko on 2007-04-20
Nope, there is no other application like that... What to do now?

---

### Post by Zdravko on 2007-04-20
Bump!

---

### Post by shinythings on 2007-04-20
There must be some other process open. Possibilities include: another terminal with apt-get or aptitude, the update manager, synaptic package manager or add/remove applications.

---

### Post by Zdravko on 2007-04-20
Yup! I managed it. Thanks!

---

