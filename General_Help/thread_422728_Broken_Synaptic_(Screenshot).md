---
title: "Broken Synaptic? (Screenshot)"
date: 2007-04-25
forum: General Help
---

### Post by UltraSonicSite on 2007-04-25
[IMG]http://img.photobucket.com/albums/v64/ultrasonicsite/Screenshot-2.png[/IMG]
Because of a broken file (It doesn't exist but Synaptic thinks it does) it won't just DELETE. As a result everything else wont work until THAT gets taken care of O.O

---

### Post by taurus on 2007-04-25
Try to run these two commands from a terminal and see what happens.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by UltraSonicSite on 2007-04-25
```
[b]uss@uss-desktop:~$ sudo aptitude update
Password:[/b]
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US           
Get:2 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Ign http://archive.canonical.com dapper-commercial/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Get:3 http://ubuntu.beryl-project.org feisty Release.gpg [191B]      
Get:4 http://us.archive.ubuntu.com feisty Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                  
Hit http://archive.canonical.com dapper-commercial Release           
Hit http://security.ubuntu.com feisty-security Release               
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_US    
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US 
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:5 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]            
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US          
Hit http://ubuntu.beryl-project.org feisty Release                              
Hit http://archive.canonical.com dapper-commercial/main Packages                
Hit http://security.ubuntu.com feisty-security/main Packages         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release                         
Hit http://ubuntu.beryl-project.org feisty/main Packages                        
Hit http://security.ubuntu.com feisty-security/restricted Packages              
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-updates/universe Sources
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Sources
Fetched 195B in 1s (138B/s)
Reading package lists... Done
**uss@uss-desktop:~$ sudo aptitude upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
[b]The following packages have unmet dependencies:
  spring-mod-ba: Depends: spring-scripts which is a virtual package.
uss@uss-desktop:~$ sudo apt-get remove spring-mod-ba[/b]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-14 linux-headers-2.6.20-14-generic libdevil1c2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  spring-mod-ba
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
**1 not fully installed or removed.**
Need to get 0B of archives.
After unpacking 7860kB disk space will be freed.
**Do you want to continue [Y/n]? y**
(Reading database ... 152841 files and directories currently installed.)
Removing spring-mod-ba ...
/var/lib/dpkg/info/spring-mod-ba.postrm: 31: spring-modupdate: not found
dpkg: error processing spring-mod-ba (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 spring-mod-ba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by UltraSonicSite on 2007-04-25
Any ideas as to the problem?

---

### Post by UltraSonicSite on 2007-04-25
Bump

---

### Post by UltraSonicSite on 2007-04-25
I got it working again:

> /var/lib/dpkg/status and remove all [actual file you want to delete/fix] entries

---

