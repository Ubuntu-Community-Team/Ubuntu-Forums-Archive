---
title: "Update manager vs apt-get"
date: 2008-01-16
forum: General Help
---

### Post by thelugnut on 2008-01-16
I used Update Manager to check if my system was up-to-date.
The indication was "There were no new updates".

I then used <sudo apt-get update and received :

james@james-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy Release
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release               
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy/main Packages                
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy/universe Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy/universe Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 3B in 1s (3B/s)  
Reading package lists... Done

Since I thought the two procedures would give the same results, I was surprised.

Is there an explanation for this?

Thanks

The Lugnut

---

### Post by MobiusNZ on 2008-01-16
When you run sudo apt-get update, all you really do is re-download the repo lists, hence the output.
To do an update from the terminal, you have to run sudo apt-get dist-upgrade after running apt-get update.

The Update manager combines these tasks

---

### Post by thelugnut on 2008-01-16
I'm sorry, but I still do not understand the difference.

I see, using the Update manager, that My system is up-to-date.

But the terminal <sudo> input shows a group of security dwnloads.

Could you detail it a bit more for me?

I am more than a little bit dense on this.

Thanks

---

### Post by onlyconnect on 2008-01-16
> I see, using the Update manager, that My system is up-to-date.

But the terminal <sudo> input shows a group of security dwnloads.

Actually, what you saw was not security *updates* that had not yet been applied, but rather the data which which apt determines whether they are needed.

This is what the previous post tried to explain.

Tim

---

### Post by MobiusNZ on 2008-01-16
When you run 
```
sudo apt-get update
```
apt-get runs through your /etc/apt/sources.list file and checks the internet servers for the relative package lists.

If the list is newer, you see a Get at the start of the line, saying its downloading that list. (like you have Get:1 [http://li.archive.ubuntu.com](http://li.archive.ubuntu.com) gutsy Release.gpg [191B]

If the list is the same version, you see Hit at the start.

Once the *lists* are up-to-date, apt-get then checks the lists to see if any of your installed software can be updated based on the versions available in the list. From here you can then choose to update those apps with sudo apt-get dist-upgrade

In a nutshell, apt-get update updates the lists, apt-get dist-upgrade updates the programs

---

### Post by thelugnut on 2008-01-16
O.K. ! Thanks for the responses. I really appreciate them.
These responses will definitely go into my notebook.
I didn't pick the name "Lugnut" for nothing.

---

### Post by Circus-Killer on 2008-01-16
why is everyone saying dist-upgrade? the OP never mentioned upgrading to a newer version.

to update from the command-line using apt-get, use the following two commands:

```

sudo apt-get update
sudo apt-get upgrade

```

the first one just upgrades the list of available packages, the second one upgrades the actual packages. the first one is just needed so that apt-get can see if there are new packages or not.

whether you use update manager or apt-get makes no difference. update manager is just a front-end for apt-get.

(dist-upgrade is only used when upgrading to newer version of ubuntu, eg. upgrading from ubuntu 6.10 to ubuntu 7.04)

---

### Post by bryncoles on 2008-01-16
very useful, informative thread. thank you for starting it, and thanks to everyone who participated! :-D

---

### Post by kevdog on 2008-01-16
Just a suggestion, but you should probably remove your cdrom install disk from your list of repository.

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US

Possibly you have done this in the /etc/apt/sources list.  Either remove or comment the line out.  If it is already, I apologize.

---

