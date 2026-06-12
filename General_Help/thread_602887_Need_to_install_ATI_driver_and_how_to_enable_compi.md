---
title: "Need to install ATI driver and how to enable compiz"
date: 2007-11-04
forum: General Help
---

### Post by Treeckcold57 on 2007-11-04
I had no idea how to install 8.42.3 ATI driver for AGIXL and Compiz on Ubuntu 7.10 32-bit. (for first time)

thanks.

---

### Post by arkara on 2007-11-04
system>administration>restricted driver manager
and you should be able to install you ati driver from there.

---

### Post by Maestro23 on 2007-11-04
Compiz-Manager: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by Treeckcold57 on 2007-11-04
> **Maestro23 said:**
> Compiz-Manager: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

I tried that...but in thermial, it say "command not found" from I paste it by: 
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main 
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

---

### Post by Maestro23 on 2007-11-04
> **Treeckcold57 said:**
> I tried that...but in thermial, it say "command not found" from I paste it by: 
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main 
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

Did you read "Add to your **/etc/apt/sources.list**".  You need to open that file up with an editor such as gedit and copy/paste those lines in the file and then save.  The file is owned by **root**, so you will need root privileges **(sudo/gksudo).** To edit the file with gedit:

> gksudo gedit /etc/apt/sources.list

---

### Post by Treeckcold57 on 2007-11-04
```
zeb@HP-linux:~$ sudo apt-get update
[sudo] password for zeb:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US            
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release                
Ign http://ppa.launchpad.net feisty Release.gpg                      
Ign http://ppa.launchpad.net feisty/main Translation-en_US          
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release                       
Hit http://ppa.launchpad.net feisty Release                                    
Hit http://security.ubuntu.com gutsy-security/main Packages          
Hit http://us.archive.ubuntu.com gutsy-updates Release
Ign http://ppa.launchpad.net feisty/main Packages                              
Hit http://security.ubuntu.com gutsy-security/restricted Packages    
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Ign http://ppa.launchpad.net feisty/main Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Hit http://security.ubuntu.com gutsy-security/multiverse Sources     
Hit http://us.archive.ubuntu.com gutsy/restricted Sources            
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://ppa.launchpad.net feisty/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://ppa.launchpad.net feisty/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 3B in 0s (4B/s)  
Reading package lists... Done
zeb@HP-linux:~$ sudo apt-get install compiz compizconfig-settings-manager \
> sudo apt-get install compiz compizconfig-settings-manager 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
sudo is already the newest version.
E: Couldn't find package apt-get
zeb@HP-linux:~$ 

```

it say "couldn't find package apt-get"

what suppose i do?

---

### Post by Maestro23 on 2007-11-04
It says you already have compiz running. Do you have an Entry:

System>>Prefs>>Advanced Desktop Effects

If so, that is where you configure the pretty eye-candy.

---

### Post by Treeckcold57 on 2007-11-04
I checked there...it do not appear "advance desktop effect" in perference.

---

### Post by Treeckcold57 on 2007-11-04
Wait a minutes...look like i didnt install it correctly...because compiz manager wasn't in perference.

---

### Post by Maestro23 on 2007-11-04
> **Treeckcold57 said:**
> I checked there...it do not appear "advance desktop effect" in perference.

Try the following command again:

> sudo apt-get install compiz compizconfig-settings-manager

---

### Post by Treeckcold57 on 2007-11-04
thanks...now it appear in perference.

I'll let you know if it goes problem.

---

### Post by Treeckcold57 on 2007-11-04
why it couldn't enable compiz? Because I didnt see 3D effect turn on. What exactly do I need to running?

---

### Post by Treeckcold57 on 2007-11-04
[IMG]http://i3.photobucket.com/albums/y74/GiganticFreeze_6005/problemenable.png[/IMG]

what gave?

---

### Post by Maestro23 on 2007-11-04
Need to make some changes to your** /etc/X11/xorg.conf**  The following link will tell you what to do.  Depending on your card model, you will use XGL or AIGLX.

[http://wiki.compiz-fusion.org/Hardware/ATI](http://wiki.compiz-fusion.org/Hardware/ATI)

---

