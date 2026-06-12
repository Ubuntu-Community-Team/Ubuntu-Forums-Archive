---
title: "Broken packages"
date: 2016-05-14
forum: General Help
---

### Post by Billisnice on 2016-05-14
Ubuntu Base
 Application plug in library

I get the package is broken

I have tried 

sudo apt-get --fix-broken install

sudo rm /var/lib/apt/lists/* -vf   
sudo apt-get update 

alt-get install-f

How to get ride of the stuff?

sudo apt-get clean  
sudo apt-get autoclean 
sudo apt-get autoremove

sudo dpkg --configure -a 
sudo apt-get update

I have tried the software center and it is still there?

---

### Post by grahammechanical on 2016-05-14
Have you tried removing the package? Whatever package it is. You do want to remove that package? I am not sure what you are trying to do. Most of those commands are irrelevant to fixing a broken package installation.

Regards.

---

### Post by Billisnice on 2016-05-14
How do you remove a broken package in  16.04?

ubuntu is not ready for prime time. My wife's chromebook just works...

---

### Post by oldos2er on 2016-05-14
Please copy and paste the complete output of ```
sudo apt update; sudo apt-get install -f
```

---

### Post by Billisnice on 2016-05-14
I hope this tell you something...thanks

[sudo] password for bill: 
```
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [93.3 kB]    
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:4 [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) xenial InRelease         
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]   
Hit:6 [http://ppa.launchpad.net/nicola-onorata/desktop/ubuntu](http://ppa.launchpad.net/nicola-onorata/desktop/ubuntu) xenial InRelease  
Hit:7 [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) xenial InRelease 
Hit:8 [http://ppa.launchpad.net/ubuntu-mate-dev/xenial-mate/ubuntu](http://ppa.launchpad.net/ubuntu-mate-dev/xenial-mate/ubuntu) xenial InRelease
Hit:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Fetched 188 kB in 27s (6,766 B/s)                                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
8 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gedit-common gir1.2-gtksource-3.0 gir1.2-secret-1 gir1.2-totem-1.0
  gir1.2-totem-plparser-1.0 gnome-icon-theme gnome-icon-theme-symbolic
  libdmapsharing-3.0-2 libgpod-common libgpod4 libsgutils2-2 python3-mako
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
```

---

### Post by wildmanne39 on 2016-05-15
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Bucky Ball on 2016-05-15
Yes, that does tell us something. Run these two one after the other. Report any errors from the last one. 
```

sudo apt update
sudo apt full-upgrade
```

To help us help you, please read the link in my signature at the bottom of this post 'Tips for effective posting'. It will save some time and help you get up and running, hopefully, sooner rather than having to waste posts fishing for info before we know what you're trying to do.

Good luck. ;)

---

### Post by Billisnice on 2016-05-15
```

Errors were encountered while processing:
 /var/cache/apt/archives/libpeas-1.0-0_1.18.0-2~ubuntu16.04.1~ppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks

---

### Post by oldos2er on 2016-05-15
I don't see any "broken package" errors. So let's try clearing the cache then running the commands Bucky gave you in post #7. ```
sudo apt clean
```

---

### Post by CantankRus on 2016-05-15
> **Billisnice said:**
> ```

Errors were encountered while processing:
 /var/cache/apt/archives/libpeas-1.0-0_1.18.0-2~ubuntu16.04.1~ppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks
What do you use "ppa:nicola-onorata/desktop" for.
That appears to be where the "libpeas-1.0-0_1.18.0-2~ubuntu16.04.1~ppa1_amd64.deb"  comes from.

---

### Post by Billisnice on 2016-05-15
I have no idea about "ppa:nicola-onorata/desktop"   I unclicked the nicola in my ppa and it seems to be working ok now...thanks

```

http://ppa.launchpad.net/nicola-onorata/desktop/ubuntu

```

---

