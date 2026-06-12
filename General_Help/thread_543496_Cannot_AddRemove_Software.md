---
title: "Cannot Add/Remove Software"
date: 2007-09-05
forum: General Help
---

### Post by roygeva on 2007-09-05
Hi, all...
This after a stupid mistake i've made in the users/groups section - 
When i've disabled all of the users accesses (instead of allowing).
I've fixed most of it by entering the groups file and re-adding the root and username to the services...
What's still wrong is that i'm unable to install or update the system.
Thanks alot,
Roy.

---

### Post by roygeva on 2007-09-05
boolie@boolie-pc:~$ sudo aptitude update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US     
Get:2 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty Release.gpg [191B]                    
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Translation-en_US                  
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US           
Get:5 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US       
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/restricted Translation-en_US            
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Translation-en_US              
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/multiverse Translation-en_US            
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Translation-en_US                  
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Translation-en_US              
Get:6 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates Release.gpg [191B]            
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US     
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Translation-en_US          
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/restricted Translation-en_US    
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty Release                                 
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release [44.6kB]               
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                          
Get:9 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]                 
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages                
Get:10 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]                    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                   
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Packages                           
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/restricted Packages                     
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Sources                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                           
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/restricted Sources                      
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Packages                       
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Sources                        
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/multiverse Packages                     
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/multiverse Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release                              
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Packages                           
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Packages                       
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Packages                   
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                  
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/restricted Packages             
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Sources                    
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages [20.9kB]        
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources               
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages [14B]     
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages [39.3kB]    
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                        
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages [2916B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Fetched 108kB in 2s (50.2kB/s)    
Reading package lists... Done
W: Duplicate sources.list entry [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Packages (/var/lib/apt/lists/il.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/il.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
boolie@boolie-pc:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
boolie@boolie-pc:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  libk3b2 libk3b2-mp3 libkrb53 libwrap0 linux-headers-2.6.20-16 
  linux-headers-2.6.20-16-generic linux-image-2.6.20-16-generic 
7 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1491kB/34.3MB of archives. After unpacking 45.1kB will be used.
Do you want to continue? [Y/n/?] y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libkrb53 1.4.4-5ubuntu3.2 [412kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main libk3b2 1.0.3-0ubuntu3~feisty1 [1034kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe libk3b2-mp3 1.0.3-0ubuntu3~feisty1 [44.7kB]
Fetched 1491kB in 2m9s (11.6kB/s)                                               
Preconfiguring packages ...
dpkg: syntax error: unknown group `root' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
boolie@boolie-pc:~$

---

### Post by roygeva on 2007-09-06
anyone?

---

### Post by zipperback on 2007-09-06
> **roygeva said:**
> anyone?


If you changed your access privileges for your root account then you may have created even greater problems for yourself than what you are currently dealing with,

Reinstall and don't make changes to your root accounts access privileges.

- Jack 
- zipperback

---

### Post by roygeva on 2007-09-06
Thanks,
Surely there's a better way...?

---

### Post by zipperback on 2007-09-10
> **roygeva said:**
> Thanks,
Surely there's a better way...?

Not really. If you corrupted your access rights with your root administrator account, then you would be better off just reinstalling.

You could also boot the live cd, mount the hard drive in question, and try to manually reset the permissions using the root account of the live cd, however, if it were me, I would probably just reinstall and accept it as a lesson learned. Also, the root administrative account should only be used for administration of the system because you can mess a lot of stuff up on your system.

Use a standard user level account for standard system access.

- zipperback
:guitar:

---

### Post by roygeva on 2007-09-16
Bumped

---

### Post by mnealon on 2007-09-24
look at the /etc/groups file

it should have

> **root: x:0:**

as the first line. Add this, then try again. I had the same problem and this seemed to fix it for me. Note there shouldn't be a space between root and the  x:0: but if I didn't do it like this then I get a smiley.

HTH
Mal

---

### Post by strabes on 2007-09-24
The following two lines are important:> W: Duplicate sources.list entry [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Packages (/var/lib/apt/lists/il.archive.ubuntu.com_ubuntu_d ists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/il.archive.ubuntu.com_ubuntu_d ists_feisty_universe_binary-i386_Packages)

You should edit your sources.list by running:```
sudo gedit /etc/apt/sources.list
```

Then replace all the contents with the contents from [here](http://www.psychocats.net/ubuntu/sources#feisty).

Then run:```
sudo rm /var/lib/apt/lists/lock && sudo apt-get update
```

---

### Post by rsambuca on 2007-09-24
> **strabes said:**
> The following two lines are important:

You should edit your sources.list by running:```
sudo gedit /etc/apt/sources.list
```


It should actually be ```
[COLOR="Red"]gksudo[/COLOR] gedit /etc/apt/sources.list
```

---

### Post by strabes on 2007-09-24
> **rsambuca said:**
> It should actually be ```
[COLOR="Red"]gksudo[/COLOR] gedit /etc/apt/sources.list
```

It [doesn't really matter](http://www.psychocats.net/ubuntu/graphicalsudo) for apps as simple as gedit. Use it if you want.

---

### Post by rsambuca on 2007-09-24
> **strabes said:**
> It [doesn't really matter](http://www.psychocats.net/ubuntu/graphicalsudo) for apps as simple as gedit. Use it if you want.

I am well aware of the fact it *happens* to work with gedit.  However, as good computing practice, you should use gksudo for any application that requires root privileges within the Xserver.

---

### Post by maybeway36 on 2007-09-24
Actually it could be gksu. gksudo is a symlink to gksu I believe, since the two apps "merged."

---

### Post by rsambuca on 2007-09-24
> **maybeway36 said:**
> Actually it could be gksu. gksudo is a symlink to gksu I believe, since the two apps "merged."

Yup!

---

