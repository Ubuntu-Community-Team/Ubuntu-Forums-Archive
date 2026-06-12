---
title: "remove medibuntu"
date: 2007-04-28
forum: General Help
---

### Post by DougieFresh4U on 2007-04-28
I need to get rid of medibuntu but its not in my repos list. so how can I get rid of it? when I do **gksudo gedit /etc/apt/sources.list** its not there, but if I do updates in terminal its there.

---

### Post by K.Mandla on 2007-04-28
Is that a repository or a metapackage? If it's a repository and it's still accessing it, delete it completely from your sources.list file and then ...
```
sudo aptitude update
```
If it's a package, you should be able to tell if it's installed with ... 
```
dpkg -l medibuntu
```
Was that of the least bit of help at all, or had you already tried those things? :?

---

### Post by zvacet on 2007-04-28
Maybe is still in your backup of source list.Just cross my mind.

---

### Post by floke on 2007-04-28
Why do you need to get rid of it?
(just curious)

---

### Post by DougieFresh4U on 2007-04-28
> **K.Mandla said:**
> Is that a repository or a metapackage? If it's a repository and it's still accessing it, delete it completely from your sources.list file and then ...
```
sudo aptitude update
```
If it's a package, you should be able to tell if it's installed with ... 
```
dpkg -l medibuntu
```
Was that of the least bit of help at all, or had you already tried those things? :?

this is what I get, thanks for suggestions
dougie@DougiesToyBox:~$ sudo aptitude update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]                                             
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US                                     
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US 
Get:5 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]         
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release [57.2kB]             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources        
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                   
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources  
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages [1050kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages [7628B]                                                            
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources [296kB]                                                                   
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources [2022B]                                                            
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages [3682kB]                                                            
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages [147kB]                                                           
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources [1118kB]                                                             
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources [50.0kB]                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources                                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources                                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources                                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources                                                             
Fetched 6411kB in 1m5s (98.4kB/s)                                                                                            
Reading package lists... Done
dougie@DougiesToyBox:~$ dpkg -l medibuntu
No packages found matching medibuntu.

---

### Post by DougieFresh4U on 2007-04-28
> **Steve.K said:**
> Why do you need to get rid of it?
(just curious)

i have changed one of my machines to "Gutsy" and when I do updates medibuntu is still listed as Feisty. It's not in my sources list for me to change or comment out

---

### Post by taurus on 2007-04-28
Post your /etc/apt/sources.list because I see you have medibuntu from Feisty release in your Gutsy!

```
cat /etc/apt/sources.list
```

---

### Post by floke on 2007-04-28
i guess the only reason you had medibuntu was for the restricted codecs (like me). 
Simply comment them out in your sources list once all your media play fine and forget about them.
* EDIT * Sorry  - just read previous post - you can edit it out through Synaptic - deselect it as a repository.

---

### Post by DougieFresh4U on 2007-04-28
> **taurus said:**
> Post your /etc/apt/sources.list because I see you have medibuntu from Feisty release in your Gutsy!

```
cat /etc/apt/sources.list
```

Thank you 7 here you go
dougie@DougiesToyBox:~$ cat /etc/apt/sources.list
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse 

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-04-28
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by DougieFresh4U on 2007-04-28
> **taurus said:**
> ```
sudo aptitude
sudo aptitude upgrade
```

Whoa!! I've never seen what popped up when I'sudo aptitude'!! What do I select as is it asked some questions about installed, not installed etc.?

---

### Post by taurus on 2007-04-28
Just cancel it with <Ctrl>c.  Then, run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by DougieFresh4U on 2007-04-28
> **taurus said:**
> Just cancel it with <Ctrl>c.  Then, run

```
sudo aptitude update
sudo aptitude upgrade
```

It's still there:
dougie@DougiesToyBox:~$ sudo aptitude update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US                                           
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US           
Get:3 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US     
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                                                                        
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                                                                    
Fetched 5B in 25s (0B/s)                                                                                                    
Reading package lists... Done
dougie@DougiesToyBox:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
dougie@DougiesToyBox:~$

---

### Post by DougieFresh4U on 2007-04-28
**hello!!**

---

### Post by bapoumba on 2007-04-29
Hello :)
Do you have an /etc/apt/apt.conf file (to mix several ubuntu versions) or /etc/apt/preferences to pin a specific package version ?

---

### Post by DougieFresh4U on 2007-04-29
> **bapoumba said:**
> Hello :)
Do you have an /etc/apt/apt.conf file (to mix several ubuntu versions) or /etc/apt/preferences to pin a specific package version ?

Not sure what you mean but did find this:
[B]// allowed (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu feisty-security";
//	"Ubuntu feisty-updates";
};

// never update the packages in this list
Unattended-Upgrade::Package-Blacklist {
//	"vim";
};[/B]

---

### Post by lalala on 2007-04-30
You've a sources.list.d folder with a medibuntu.list file inside.

```

ls /etc/apt/sources.list.d/

sudo rm //ect/apt/sources.list.d/medibuntu.list

sudo apt-get update

```

enjoy!

---

### Post by DougieFresh4U on 2007-04-30
Please some one help me get rid of this medibuntu. I found some thing in etc/apt. a medibuntu folder but it tells me I don't have permissions to rid it. how can I get permission
thank you to any one who can help

---

### Post by DougieFresh4U on 2007-04-30
> **lalala said:**
> You've a sources.list.d folder with a medibuntu.list file inside.

```

ls /etc/apt/sources.list.d/

sudo rm //ect/apt/sources.list.d/medibuntu.list

sudo apt-get update

```

enjoy!

dougie@DougiesToyBox:~$ ls /etc/apt/sources.list.d/
medibuntu.list
dougie@DougiesToyBox:~$ sudo rm //ect/apt/sources.list.d/medibuntu.list
rm: cannot remove `//ect/apt/sources.list.d/medibuntu.list': No such file or directory
dougie@DougiesToyBox:~$

---

### Post by Nythain on 2007-04-30
sudo rm //ect/apt/sources.list.d/medibuntu.list

should probably read more like

sudo rm /etc/apt/sources.list.d/medibuntu.list

see if that helps

---

### Post by DougieFresh4U on 2007-04-30
> **Nythain said:**
> sudo rm //ect/apt/sources.list.d/medibuntu.list

should probably read more like

sudo rm /etc/apt/sources.list.d/medibuntu.list

see if that helps

Thank you so much. that was bugging me for days, and now it's fixed. thanks to all who gave input:) :)

---

