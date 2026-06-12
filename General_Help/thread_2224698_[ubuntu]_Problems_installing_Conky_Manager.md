---
title: "[ubuntu] Problems installing Conky Manager"
date: 2014-05-17
forum: General Help
---

### Post by claes2 on 2014-05-17
I'm having problems installing Conky Manager getting these errors:

user@chrubuntu:~$ sudo apt-add-repository ppa:teejee2008/ppa
[sudo] password for user:  
 More info: [https://launchpad.net/~teejee2008/+archive/ppa](https://launchpad.net/~teejee2008/+archive/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpblj1d7_b/secring.gpg' created
gpg: keyring `/tmp/tmpblj1d7_b/pubring.gpg' created
gpg: requesting key 2D0F61F0 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpblj1d7_b/trustdb.gpg: trustdb created
gpg: key 2D0F61F0: public key "Launchpad PPA for Tony George" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
user@chrubuntu:~$ sudo apt-get install conky-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to locate package conky-manager

---

### Post by grumblebum2 on 2014-05-23
Did you update your available packages after installing the teejee2008 ppa?
```
sudo apt-get update

sudo apt-get install conky-manager
```

---

### Post by claes2 on 2014-05-23
> **grumblebum2 said:**
> Did you update your available packages after installing the teejee2008 ppa?
```
sudo apt-get update

sudo apt-get install conky-manager
```

I get this error when I try the update command:

user@chrubuntu:~$ sudo apt-get update
E: The method driver /usr/lib/apt/methods/https could not be found.
N: Is the package apt-transport-https installed?
E: The method driver /usr/lib/apt/methods/https could not be found.
N: Is the package apt-transport-https installed?


Has anyone seen this before?

---

### Post by grumblebum2 on 2014-05-23
What does this give you...
```
sudo apt-get install apt-transport-https
```

---

### Post by claes2 on 2014-05-23
> **grumblebum2 said:**
> What does this give you...
```
sudo apt-get install apt-transport-https
```

I got this:

user@chrubuntu:~$ sudo apt-get install apt-transport-https
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apt-transport-https
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
Need to get 25.1 kB of archives.
After this operation, 238 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main apt-transport-https amd64 1.0.1ubuntu2 [25.1 kB]
Fetched 25.1 kB in 0s (45.4 kB/s)        
Selecting previously unselected package apt-transport-https.
(Reading database ... 179567 files and directories currently installed.)
Preparing to unpack .../apt-transport-https_1.0.1ubuntu2_amd64.deb ...
Unpacking apt-transport-https (1.0.1ubuntu2) ...
Setting up apt-transport-https (1.0.1ubuntu2) ...
user@chrubuntu:~$ 

Then I tried: 
sudo apt-get update

again and got this (yay):

user@chrubuntu:~$ sudo apt-get update
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                        
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                            
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                           
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1347 B]                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                   
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages        
Get:3 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1203 B]       
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1211 B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease                           
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                    
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease   
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty InRelease     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg [933 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg            
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty InRelease
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release.gpg [933 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release    
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]              
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release [58.5 kB]
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [14.0 kB]            
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [14.0 kB]                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                      
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [14.0 kB]                         
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release [58.5 kB]        
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [14.0 kB]                       
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [814 B]               
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [814 B]
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [13.2 kB]             
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [13.2 kB]              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [1641 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [1659 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [2291 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                     
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [2305 B]               
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources [41.4 kB]           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en                 
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources [14 B]        
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources [26.6 kB]       
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en                 
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en                 
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources [2234 B]      
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages [98.1 kB]    
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages [14 B] 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                          
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages [66.9 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                          
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [7089 B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [96.4 kB]     
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]  
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [67.1 kB] 
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages [7273 B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en [46.7 kB]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en           
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en [31.9 kB]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources [15.6 kB]          
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources [14 B]       
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources [4212 B]       
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Sources [687 B]      
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main amd64 Packages [49.4 kB]   
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted amd64 Packages [14 B]
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe amd64 Packages [17.7 kB]
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse amd64 Packages [1154 B]
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages [47.5 kB]    
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages [14 B] 
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages [17.7 kB]
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages [1404 B]
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en [23.1 kB]   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en            
Fetched 935 kB in 20s (46.4 kB/s)                                                
Reading package lists... Done


Now trying: 

sudo apt-get install conky-manager


user@chrubuntu:~$ sudo apt-get install conky-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  conky-all libaudclient2 libid3tag0 libimlib2 liblua5.1-0 libxmmsclient6
  p7zip-full python-wnck realpath
Suggested packages:
  apcupsd audacious moc mpd xmms2 p7zip-rar
The following NEW packages will be installed:
  conky-all conky-manager libaudclient2 libid3tag0 libimlib2 liblua5.1-0
  libxmmsclient6 p7zip-full python-wnck realpath
0 upgraded, 10 newly installed, 0 to remove and 47 not upgraded.
Need to get 3426 kB of archives.
After this operation, 8242 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe libaudclient2 amd64 3.4.3-1 [12.4 kB]
Get:2 [http://ppa.launchpad.net/teejee2008/ppa/ubuntu/](http://ppa.launchpad.net/teejee2008/ppa/ubuntu/) trusty/main conky-manager amd64 1.2.0.1 [1089 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main liblua5.1-0 amd64 5.1.5-5 [173 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libid3tag0 amd64 0.15.1b-10ubuntu1 [28.9 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libimlib2 amd64 1.4.6-2 [171 kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe libxmmsclient6 amd64 0.8+dfsg-9 [60.4 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe conky-all amd64 1.9.0-4 [293 kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe p7zip-full amd64 9.20.1~dfsg.1-4 [1561 kB]
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main python-wnck amd64 2.32.0+dfsg-3 [23.2 kB]
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main realpath amd64 1.19 [14.5 kB]
Fetched 3426 kB in 14s (236 kB/s)                                                
Selecting previously unselected package libaudclient2:amd64.
(Reading database ... 179573 files and directories currently installed.)
Preparing to unpack .../libaudclient2_3.4.3-1_amd64.deb ...
Unpacking libaudclient2:amd64 (3.4.3-1) ...
Selecting previously unselected package liblua5.1-0:amd64.
Preparing to unpack .../liblua5.1-0_5.1.5-5_amd64.deb ...
Unpacking liblua5.1-0:amd64 (5.1.5-5) ...
Selecting previously unselected package libid3tag0.
Preparing to unpack .../libid3tag0_0.15.1b-10ubuntu1_amd64.deb ...
Unpacking libid3tag0 (0.15.1b-10ubuntu1) ...
Selecting previously unselected package libimlib2.
Preparing to unpack .../libimlib2_1.4.6-2_amd64.deb ...
Unpacking libimlib2 (1.4.6-2) ...
Selecting previously unselected package libxmmsclient6.
Preparing to unpack .../libxmmsclient6_0.8+dfsg-9_amd64.deb ...
Unpacking libxmmsclient6 (0.8+dfsg-9) ...
Selecting previously unselected package conky-all.
Preparing to unpack .../conky-all_1.9.0-4_amd64.deb ...
Unpacking conky-all (1.9.0-4) ...
Selecting previously unselected package p7zip-full.
Preparing to unpack .../p7zip-full_9.20.1~dfsg.1-4_amd64.deb ...
Unpacking p7zip-full (9.20.1~dfsg.1-4) ...
Selecting previously unselected package python-wnck.
Preparing to unpack .../python-wnck_2.32.0+dfsg-3_amd64.deb ...
Unpacking python-wnck (2.32.0+dfsg-3) ...
Selecting previously unselected package realpath.
Preparing to unpack .../realpath_1.19_amd64.deb ...
Unpacking realpath (1.19) ...
Selecting previously unselected package conky-manager.
Preparing to unpack .../conky-manager_1.2.0.1_amd64.deb ...
Unpacking conky-manager (1.2.0.1) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up libaudclient2:amd64 (3.4.3-1) ...
Setting up liblua5.1-0:amd64 (5.1.5-5) ...
Setting up libid3tag0 (0.15.1b-10ubuntu1) ...
Setting up libimlib2 (1.4.6-2) ...
Setting up libxmmsclient6 (0.8+dfsg-9) ...
Setting up conky-all (1.9.0-4) ...
Setting up p7zip-full (9.20.1~dfsg.1-4) ...
Setting up python-wnck (2.32.0+dfsg-3) ...
Setting up realpath (1.19) ...
Setting up conky-manager (1.2.0.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Processing triggers for menu (2.1.46ubuntu1) ...
user@chrubuntu:~$ 


Thank you! Before I mark the thread as Solved might I ask why I was getting that error and the significance of the command that changed it and allowed me to update?

---

### Post by grumblebum2 on 2014-05-23
Don't really know what was wrong.
Your error message was asking... 
```
E: The method driver /usr/lib/apt/methods/https could not be found.
 N: Is the package apt-transport-https installed?
```
So just checked to see if it was installed.

**apt-transport-https** is a default installed package.

---

### Post by claes2 on 2014-05-23
Thank you!  Marking Solved.

---

