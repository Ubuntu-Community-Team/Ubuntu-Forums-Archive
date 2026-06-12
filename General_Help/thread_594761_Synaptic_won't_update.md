---
title: "Synaptic won't update"
date: 2007-10-28
forum: General Help
---

### Post by eFFeeMMe on 2007-10-28
Hey there. I've looked through the forums but can't find an answer.

I just recently installed Ubuntu 7.10, and it's fine apart from a single, huge problem - the Synaptic and Add/Remove programs won't update their file lists. They download 48 files, but then they reload and no new applications are avaible. They do it all the time.

---

### Post by Joe88 on 2007-10-28
Maybe you should try a system update, i think this updates file lists for synaptic and Add/remove programs:

1.click the system menu
2.click the administration menu
3.then click update manager and when this appears click install updates/check and then install if no updates are listed

---

### Post by eFFeeMMe on 2007-10-28
Hmmmm... No updates are avaible, it says...

---

### Post by taurus on 2007-10-28
Open a terminal and post the outputs of these two commands.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by eFFeeMMe on 2007-10-28
effeemme@effeemme-desktop:~$ sudo apt-get update
[sudo] password for effeemme:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:2 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy Release 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy/main Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Fetched 3B in 3s (1B/s)  
Reading package lists... Done
effeemme@effeemme-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
effeemme@effeemme-desktop:~$


EDIT: Aaaand it happens to be fixed. What could it have been? Do I need to manually update each time?

---

### Post by taurus on 2007-10-28
So there is nothing to upgrade.  Open up firefox and see which version you have on your machine right now.  Gutsy comes with firefox version 2.0.0.6 and the latest in the repos is 2.0.0.8.

---

### Post by eFFeeMMe on 2007-10-28
No, no, it's not that simple. The first time I booted, the system upgraded the installed packages as usual, what was failing to reload was Synaptic's software list. Each time it said it was outdated, but after downloading 48 or so files nothing would change.
Everything was fine apart from that - for instance, Firefox updated itself with no hassle.

---

### Post by taurus on 2007-10-28
So everything is back to normal now?

---

