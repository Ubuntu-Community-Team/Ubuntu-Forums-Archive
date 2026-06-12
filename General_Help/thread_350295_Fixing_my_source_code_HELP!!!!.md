---
title: "Fixing my source code HELP!!!!"
date: 2007-01-31
forum: General Help
---

### Post by Tobster on 2007-01-31
HELP!!!!!

Guys,

After I installed  AUtomatix I damaged my source code some how!  Can't install any updates!  :( 

Could someone copy there working source code for me so that I can just copy and paste it

Thanks

Toby

---

### Post by taurus on 2007-01-31
Why don't you paste your /etc/apt/sources.list so people can help you to fix it.  Otherwise, here is one you can use.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by ~LoKe on 2007-01-31
```
sudo cp /etc/apt/sources.list~ /etc/apt/sources.list
```

---

### Post by Tobster on 2007-01-31
Thanks

How do i get it again

Toby

---

### Post by ~LoKe on 2007-01-31
> **Tobster said:**
> Thanks

How do i get it again

Toby

```
cat /etc/apt/sources.list
```
In the terminal.
**EDIT:** Or,
```
sudo gedit /etc/apt/sources.list
```
If you plan on modifying it.

---

### Post by Tobster on 2007-01-31
toby@toby-desktop:~$ sudo cp /etc/apt/sources.list~ /etc/apt/sources.list
Password:
cp: cannot stat `/etc/apt/sources.list~': No such file or directory
toby@toby-desktop:~$

---

### Post by Tobster on 2007-01-31
toby@toby-desktop:~$ cat /etc/apt/sources.list

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END

#AUTOMATIX BLEEDER REPOS START

deb [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) binary/

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
#AUTOMATIX BLEEDER REPOS END
toby@toby-desktop:~$

---

### Post by Tobster on 2007-01-31
Still having problems  I got this now:

toby@toby-desktop:~$ sudo aptitude update
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_GB                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_GB                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_GB                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_GB                 
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Get:3 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_GB            
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_GB         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages [940kB]                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources           
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [31.2kB] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [3432B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_GB         
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages [5974B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources [274kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources [1436B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages  
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources [1068kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages 
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources [45.0kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [62.6kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages [14B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources [18.9kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Fetched 2451kB in 6s (378kB/s)                                                  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
toby@toby-desktop:~$

---

### Post by Tobster on 2007-01-31
Please could someone help me with the above

---

### Post by Tobster on 2007-01-31
here a screen shot of Systematic :(

---

### Post by JamieC on 2007-01-31
Looks like your local repository is corrupt, run the following command:
```

sudo dpkg --configure -a

```

---

### Post by Tobster on 2007-01-31
Thanks  I got this now:

toby@toby-desktop:~$ sudo dpkg --configure -a
Password:
Setting up libssl0.9.7 (0.9.7k-3) ...

Setting up vmware-player-kernel-modules-2.6.17-10 (2.6.17.7-10.1) ...

Setting up vmware-player-kernel-modules (2.6.17.10) ...
toby@toby-desktop:~$

---

### Post by JamieC on 2007-01-31
> **Tobster said:**
> Thanks  I got this now:

toby@toby-desktop:~$ sudo dpkg --configure -a
Password:
Setting up libssl0.9.7 (0.9.7k-3) ...

Setting up vmware-player-kernel-modules-2.6.17-10 (2.6.17.7-10.1) ...

Setting up vmware-player-kernel-modules (2.6.17.10) ...
toby@toby-desktop:~$

Seems like those packages were not installed completely. Now you should be good to go:
```

sudo apt-get update

```

---

### Post by Tobster on 2007-01-31
WOW  That fixed it :guitar:   I so happy now  Thanks buddy

---

### Post by JamieC on 2007-01-31
No problem, you're welcome.

Although this is somewhat unrelated, if you plan on editing your apt sources, I suggest you backup the current file so it can be restored if neccessary:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list~

```

Some editors will create a backup for you anyway.

---

