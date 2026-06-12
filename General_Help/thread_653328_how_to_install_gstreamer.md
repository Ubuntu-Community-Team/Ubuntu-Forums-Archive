---
title: "how to install gstreamer"
date: 2007-12-29
forum: General Help
---

### Post by cloggedone on 2007-12-29
It is not in Add/Remove programs, I cannot use terminal (apt-get is broken). Any other way?

---

### Post by taurus on 2007-12-29
How does it break?  Post the outputs of these two commands from a terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by cloggedone on 2007-12-29
> **taurus said:**
> How does it break?  Post the outputs of these two commands from a terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

update:
```
shane@shane-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release 
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Hit http://us.archive.ubuntu.com gutsy-updates Release
Hit http://security.ubuntu.com gutsy-security/main Packages         
Hit http://us.archive.ubuntu.com gutsy/main Packages                
Hit http://us.archive.ubuntu.com gutsy/restricted Packages          
Hit http://us.archive.ubuntu.com gutsy/main Sources                 
Hit http://us.archive.ubuntu.com gutsy/restricted Sources           
Hit http://security.ubuntu.com gutsy-security/restricted Packages   
Hit http://security.ubuntu.com gutsy-security/main Sources          
Hit http://security.ubuntu.com gutsy-security/restricted Sources    
Hit http://us.archive.ubuntu.com gutsy/universe Packages            
Hit http://us.archive.ubuntu.com gutsy/universe Sources             
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages          
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources           
Hit http://security.ubuntu.com gutsy-security/universe Packages     
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 3B in 1s (2B/s)  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

upgrade:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by taurus on 2007-12-29
Do you happen to have synaptic or Add/Remove window open?  You must close it before you run those commands from a terminal.

Are you trying to install codecs so you can play music or movie on your Gutsy?

---

### Post by SOULRiDER on 2007-12-29
Reboot, if youre still getting that error type this ina  terminal
```
sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a
```

GStreamer is already installed in Ubuntu, but you might wanna check out [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by taurus on 2007-12-29
> **SOULRiDER said:**
> 
If this post has helpful, Say Thanks by pressing theThank You button on this post!


The line in your sig is just lame.  :roll:

---

### Post by SOULRiDER on 2007-12-29
> **taurus said:**
> The line in your sig is just lame.  :roll:

And these two posts are 100% on-topic.

---

