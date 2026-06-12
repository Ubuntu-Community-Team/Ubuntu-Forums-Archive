---
title: "Problem with dependencies in file '/var/lib/dpkg/status'"
date: 2016-02-22
forum: General Help
---

### Post by anna16 on 2016-02-22
Hi everyone,

I'm a newbe at Ubuntu... I have the version Xubuntu 14.04. After installing Skype and Libreoffice I couldn't install anything else anymore. After entering sudo apt-get -f install as suggested by my computer I got these lines in the end:

dpkg: parse error, in file '/var/lib/dpkg/status' near line 90 package 'python-pkg-resources':
 Feld »Depends«, ungültiger Paketname »python:any«: Zeichen »:« nicht erlaubt (nur Buchstaben, Ziffern und die Zeichen »-+._«)
E: Sub-process /usr/bin/dpkg returned an error code (2)

I searched through a lot of threads in forums but couldn't find anything useable... Please help me!!!

---

### Post by Bashing-om on 2016-02-22
anna16; Hello;

Well, the control file is not in a happy state.
Let's see what the package management system state is
post back - between code tags - the outputs of terminal commands:
```

LANG=C;sudo apt update
LANG=C;sudo apt upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then we take a look at that status control file.

[INDENT][INDENT]least ways, that is my thoughts
[/INDENT][/INDENT]

---

### Post by anna16 on 2016-02-24
Thank you!

That's the output:
```
Ign cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty InRelease
Ign cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty Release.gpg
Ign cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty Release
Err cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty/multiverse amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty/universe amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty/main Translation-en
Ign cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty/main Translation-de
Ign cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty/multiverse Translation-en
Ign cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty/multiverse Translation-de
Ign cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty/restricted Translation-en
Ign cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty/restricted Translation-de
Ign cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty/universe Translation-en
Ign cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723) trusty/universe Translation-de
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty InRelease                              
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                        
Get:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease [15.4 kB]                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources [6040 B]                    
Get:4 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security InRelease [65.9 kB]         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [29.6 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty Release.gpg                            
Get:6 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/multiverse Sources [5547 B]  
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [11.6 kB]          
Get:8 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/restricted Sources [5352 B]  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:9 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/main Sources [260 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:10 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/universe Sources [150 kB]   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-de                        
Get:11 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.9 kB]
Get:12 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/main amd64 Packages [709 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-de                 
Get:13 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/universe amd64 Packages [338 kB]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Get:14 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:15 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/main Translation-en [359 kB]
Get:16 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/multiverse Translation-en [6947 B]
Get:17 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/restricted Translation-en [3699 B]
Get:18 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/universe Translation-en [180 kB]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/restricted Sources  
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/universe Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/main Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/restricted amd64 Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/universe amd64 Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/main amd64 Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/universe Translation-en
Get:19 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security/multiverse Sources [2767 B]
Get:20 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security/restricted Sources [4035 B]
Get:21 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security/main Sources [105 kB]
Get:22 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security/universe Sources [33.0 kB]
Get:23 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB]
Get:24 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security/main amd64 Packages [428 kB]
Get:25 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security/universe amd64 Packages [124 kB]
Get:26 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security/multiverse amd64 Packages [4990 B]
Get:27 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security/main Translation-en [234 kB]
Get:28 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security/multiverse Translation-en [2570 B]
Get:29 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security/restricted Translation-en [3206 B]
Get:30 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security/universe Translation-en [72.6 kB]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty Release                                
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main Sources                           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main Translation-de                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse Translation-de              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted Translation-de              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe Translation-de                
Fetched 3268 kB in 7s (458 kB/s)                                               
W: Failed to fetch cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723)/dists/trusty/multiverse/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723)/dists/trusty/universe/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Plus this after sudo apt upgrade:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try using -f.
```

---

### Post by Bashing-om on 2016-02-24
anna16; Hey ...

the good news is that I see nothing to panic about. All fixable:
1st is the CDrom advisory.
> 
W: Failed to fetch cdrom://Xubuntu 14.04.1 LTS _Trusty Tahr_ <snip>

You are done and have no need for the CD on the install. In software sources uncheck that box .

2nd: I do expect an obsolete PPA. post back what the sources are that the package manager is working with:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

The version of libreoffice you have installed is very old :
see: [https://launchpad.net/~libreoffice](https://launchpad.net/~libreoffice)
I do not see that version 4.3 is a supported release.
We see what we can do to get libreoffice reverted to what is in our software repository ?

[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-02-24
OK... So this is what I got for you:

```
cat -n /etc/apt/sources.list
     1    # deb cdrom:[Xubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140723)]/ trusty main multiverse restricted universe
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty restricted main
     6    deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty multiverse restricted main universe #Added by software-properties
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty-updates restricted main
    11    deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty-updates multiverse restricted main universe #Added by software-properties
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty universe
    17    deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty-updates universe
    18    
    19    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    20    ## team, and may not be under a free licence. Please satisfy yourself as to 
    21    ## your rights to use the software. Also, please note that software in 
    22    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    23    ## security team.
    24    deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty multiverse
    25    deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    26    
    27    ## N.B. software from this repository may not have been tested as
    28    ## extensively as that contained in the main release, although it includes
    29    ## newer versions of some applications which may provide useful features.
    30    ## Also, please note that software in backports WILL NOT receive any review
    31    ## or updates from the Ubuntu security team.
    32    deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty-backports restricted universe multiverse main
    33    deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty-backports restricted universe multiverse main #Added by software-properties
    34    
    35    deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty-security restricted main
    36    deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty-security multiverse restricted main universe #Added by software-properties
    37    deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty-security universe
    38    deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty-security multiverse
    39    
    40    ## Uncomment the following two lines to add software from Canonical's
    41    ## 'partner' repository.
    42    ## This software is not part of Ubuntu, but is offered by Canonical and the
    43    ## respective vendors as a service to Ubuntu users.
    44    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    45    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    46    
    47    ## This software is not part of Ubuntu, but is offered by third-party
    48    ## developers who want to ship their latest software.
    49    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    50    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    51    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
```
```
k@Anna-PC:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-3-trusty.list <==
deb [http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu) trusty main

==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-3-trusty.list.save <==
deb [http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu) trusty main

==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list <==
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list.save <==
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list <==
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save <==
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main
```

---

### Post by Bashing-om on 2016-02-24
anna16; Well, well ....

Forum procedure: code tags !
Please enclose all outputs in code tags, promotes readability and maintains the formatting.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
---------------------------------

We have duplicate sources for libreoffice !
> 
==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-3-trusty.list <==
deb [http://ppa.launchpad.net/libreoffice...ice-4-3/ubuntu](http://ppa.launchpad.net/libreoffice...ice-4-3/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/libreoffice...ice-4-3/ubuntu](http://ppa.launchpad.net/libreoffice...ice-4-3/ubuntu) trusty main

-bk-
==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list <==
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main


How bout we try and remove the unsupported source list ?
```

sudo rm /etc/apt/sources.list.d/libreoffice-libreoffice-4-3-trusty.list

```
And as well, why is the 'deb-src' line repeated ? post back:
```

cat /etc/apt/sources.list.d/libreoffice-ppa-trusty.list

```
see if a manual edit is warranted .

Next is that it is not a good idea to run the system with the " backports" repo enabled. The way this repo works is that you get the packages that you require from 'upstream' and turn the repo back off. Otherwise there is no telling what undesired side effect will result with newer package installs. Also uncheck this repo in software sources.

once these are done, let's get a fresh perspective of what the package manager sees now.
post back = between code tags = :
```

sudo apt update
sudo apt upgrade
sudo apt-get -f install

```
keeping in mind that there may still be skype to deal with.

[INDENT][INDENT]all in keeping the package manager
[INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-02-25
Hi again.

I unticked the backports repo and after running your first two commands I got this:
```

k@Anna-PC:~$ sudo rm /etc/apt/sources.list.d/libreoffice-libreoffice-4-3-trusty.list
[sudo] password for k: 
k@Anna-PC:~$ sudo rm /etc/apt/sources.list.d/libreoffice-libreoffice-4-3-trusty.list
rm: das Entfernen von »/etc/apt/sources.list.d/libreoffice-libreoffice-4-3-trusty.list&#8220; ist nicht möglich: Datei oder Verzeichnis nicht gefunden
k@Anna-PC:~$ cat /etc/apt/sources.list.d/libreoffice-ppa-trusty.list
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main

```

Then I ran update...:
```

k@Anna-PC:~$ sudo apt update
Ign http://de.archive.ubuntu.com trusty InRelease
Ign http://archive.canonical.com trusty InRelease                         
OK   http://ppa.launchpad.net trusty InRelease                             
Holen: 1 http://de.archive.ubuntu.com trusty-updates InRelease [65,9 kB]       
OK   http://archive.canonical.com trusty Release.gpg                           
OK   http://ppa.launchpad.net trusty InRelease                                 
OK   http://archive.canonical.com trusty Release                               
OK   http://ppa.launchpad.net trusty/main Sources                              
OK   http://archive.canonical.com trusty/partner Sources                       
OK   http://ppa.launchpad.net trusty/main amd64 Packages                       
Holen: 2 http://de.archive.ubuntu.com trusty-security InRelease [65,9 kB]   
OK   http://archive.canonical.com trusty/partner amd64 Packages                
OK   http://ppa.launchpad.net trusty/main Translation-en                       
OK   http://archive.canonical.com trusty/partner Translation-en                
OK   http://ppa.launchpad.net trusty/main Sources                              
OK   http://ppa.launchpad.net trusty/main amd64 Packages                       
OK   http://ppa.launchpad.net trusty/main Translation-en     
Ign http://extras.ubuntu.com trusty InRelease                
Holen: 3 http://extras.ubuntu.com trusty Release.gpg [72 B]  
OK   http://extras.ubuntu.com trusty Release                        
OK   http://extras.ubuntu.com trusty/main Sources                              
OK   http://de.archive.ubuntu.com trusty Release.gpg                           
OK   http://extras.ubuntu.com trusty/main amd64 Packages
Holen: 4 http://de.archive.ubuntu.com trusty-updates/multiverse Sources [5.547 B]
Holen: 5 http://de.archive.ubuntu.com trusty-updates/restricted Sources [5.352 B]
Holen: 6 http://de.archive.ubuntu.com trusty-updates/main Sources [260 kB]
Holen: 7 http://de.archive.ubuntu.com trusty-updates/universe Sources [150 kB]
Holen: 8 http://de.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15,9 kB]
Ign http://extras.ubuntu.com trusty/main Translation-de_DE                     
Ign http://extras.ubuntu.com trusty/main Translation-de
Ign http://extras.ubuntu.com trusty/main Translation-en
Holen: 9 http://de.archive.ubuntu.com trusty-updates/main amd64 Packages [709 kB]
Holen: 10 http://de.archive.ubuntu.com trusty-updates/universe amd64 Packages [338 kB]
Holen: 11 http://de.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13,2 kB]
Holen: 12 http://de.archive.ubuntu.com trusty-updates/main Translation-en [359 kB]
Holen: 13 http://de.archive.ubuntu.com trusty-updates/multiverse Translation-en [6.947 B]
Holen: 14 http://de.archive.ubuntu.com trusty-updates/restricted Translation-en [3.699 B]
Holen: 15 http://de.archive.ubuntu.com trusty-updates/universe Translation-en [180 kB]
Holen: 16 http://de.archive.ubuntu.com trusty-security/multiverse Sources [2.767 B]
Holen: 17 http://de.archive.ubuntu.com trusty-security/restricted Sources [4.035 B]
Holen: 18 http://de.archive.ubuntu.com trusty-security/main Sources [105 kB]
Holen: 19 http://de.archive.ubuntu.com trusty-security/universe Sources [33,0 kB]
Holen: 20 http://de.archive.ubuntu.com trusty-security/restricted amd64 Packages [13,0 kB]
Holen: 21 http://de.archive.ubuntu.com trusty-security/main amd64 Packages [428 kB]
Holen: 22 http://de.archive.ubuntu.com trusty-security/universe amd64 Packages [124 kB]
Holen: 23 http://de.archive.ubuntu.com trusty-security/multiverse amd64 Packages [4.990 B]
Holen: 24 http://de.archive.ubuntu.com trusty-security/main Translation-en [234 kB]
Holen: 25 http://de.archive.ubuntu.com trusty-security/multiverse Translation-en [2.570 B]
Holen: 26 http://de.archive.ubuntu.com trusty-security/restricted Translation-en [3.206 B]
Holen: 27 http://de.archive.ubuntu.com trusty-security/universe Translation-en [72,6 kB]
OK   http://de.archive.ubuntu.com trusty Release                        
OK   http://de.archive.ubuntu.com trusty/multiverse Sources
OK   http://de.archive.ubuntu.com trusty/restricted Sources
OK   http://de.archive.ubuntu.com trusty/main Sources
OK   http://de.archive.ubuntu.com trusty/universe Sources
OK   http://de.archive.ubuntu.com trusty/restricted amd64 Packages
OK   http://de.archive.ubuntu.com trusty/main amd64 Packages
OK   http://de.archive.ubuntu.com trusty/universe amd64 Packages
OK   http://de.archive.ubuntu.com trusty/multiverse amd64 Packages
OK   http://de.archive.ubuntu.com trusty/main Translation-de
OK   http://de.archive.ubuntu.com trusty/main Translation-en
OK   http://de.archive.ubuntu.com trusty/multiverse Translation-de
OK   http://de.archive.ubuntu.com trusty/multiverse Translation-en
OK   http://de.archive.ubuntu.com trusty/restricted Translation-de
OK   http://de.archive.ubuntu.com trusty/restricted Translation-en
OK   http://de.archive.ubuntu.com trusty/universe Translation-de
OK   http://de.archive.ubuntu.com trusty/universe Translation-en
Ign http://de.archive.ubuntu.com trusty/main Translation-de_DE                 
Ign http://de.archive.ubuntu.com trusty/multiverse Translation-de_DE           
Ign http://de.archive.ubuntu.com trusty/restricted Translation-de_DE           
Ign http://de.archive.ubuntu.com trusty/universe Translation-de_DE             
Es wurden 3.206 kB in 6 s geholt (517 kB/s).                                   
Paketlisten werden gelesen... Fertig
k@Anna-PC:~$ sudo apt upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Probieren Sie »apt-get -f install«, um dies zu korrigieren.
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 libreoffice-core : Hängt ab von: libreoffice-common (> 1:4.3.2~rc2) ist aber nicht installiert
 libreoffice-help-en-us : Hängt ab von: libreoffice-l10n-en-us
 libreoffice-l10n-de : Hängt ab von: libreoffice-common ist aber nicht installiert
 libreoffice-l10n-en-gb : Hängt ab von: libreoffice-common ist aber nicht installiert
 libreoffice-l10n-en-za : Hängt ab von: libreoffice-common ist aber nicht installiert
 skype : Hängt ab von: skype-bin ist aber nicht installierbar
E: Unerfüllte Abhängigkeiten. Versuchen Sie, -f zu benutzen.
k@Anna-PC:~$ sudo apt-get -f install
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Abhängigkeiten werden korrigiert ... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  hyphen-de hyphen-en-us libcmis-0.4-4 libqt4-xml libqtcore4 libqtdbus4
  libreoffice-help-de libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-l10n-de libreoffice-l10n-en-gb libreoffice-l10n-en-za
  mysql-common mythes-de mythes-de-ch mythes-en-au mythes-en-us
  openoffice.org-hyphenation qdbus qtchooser qtcore4-l10n xfonts-mathml
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden zusätzlichen Pakete werden installiert:
  fonts-stix libboost-iostreams1.54.0 libreoffice-base-core libreoffice-common
  libreoffice-core libreoffice-l10n-de libreoffice-l10n-en-gb
  libreoffice-l10n-en-za libreoffice-math libreoffice-style-galaxy
  libreoffice-writer uno-libs3 ure
Vorgeschlagene Pakete:
  libreoffice-base libreoffice-style-breeze libreoffice-style-hicontrast
  libreoffice-style-human libreoffice-style-oxygen libreoffice-style-sifr
  libreoffice-style-tango libreoffice-grammarcheck-de
  hunspell-dictionary-en-gb myspell-dictionary-en-gb hyphen-en-gb
  libreoffice-grammarcheck-en-gb hunspell-dictionary-en-za
  myspell-dictionary-en-za hyphen-en-za libreoffice-grammarcheck-en-za
  libreoffice-help-en-za mythes-en-za fonts-crosextra-caladea
  fonts-crosextra-carlito libreoffice-gcj libreoffice-java-common
Die folgenden Pakete werden ENTFERNT:
  python3-uno skype
Die folgenden NEUEN Pakete werden installiert:
  fonts-stix libboost-iostreams1.54.0 libreoffice-common
Die folgenden Pakete werden aktualisiert (Upgrade):
  libreoffice-base-core libreoffice-core libreoffice-l10n-de
  libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-math
  libreoffice-style-galaxy libreoffice-writer uno-libs3 ure
10 aktualisiert, 3 neu installiert, 2 zu entfernen und 516 nicht aktualisiert.
14 nicht vollständig installiert oder entfernt.
Es müssen noch 68,5 MB von 69,2 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 74,4 MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] J
Holen: 1 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main uno-libs3 amd64 5.1.0~rc3-0ubuntu1~trusty0 [870 kB]
Holen: 2 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main libboost-iostreams1.54.0 amd64 1.54.0-4ubuntu3.1 [29,0 kB]
Holen: 3 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main ure amd64 5.1.0~rc3-0ubuntu1~trusty0 [1.712 kB]
Holen: 4 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-math amd64 1:5.1.0~rc3-0ubuntu1~trusty0 [361 kB]
Holen: 5 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-writer amd64 1:5.1.0~rc3-0ubuntu1~trusty0 [7.554 kB]
Holen: 6 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-base-core amd64 1:5.1.0~rc3-0ubuntu1~trusty0 [713 kB]
Holen: 7 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-core amd64 1:5.1.0~rc3-0ubuntu1~trusty0 [31,7 MB]
Holen: 8 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-style-galaxy all 1:5.1.0~rc3-0ubuntu1~trusty0 [1.518 kB]
Holen: 9 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-common all 1:5.1.0~rc3-0ubuntu1~trusty0 [22,6 MB]
Holen: 10 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-l10n-de all 1:5.1.0~rc3-0ubuntu1~trusty0 [504 kB]
Holen: 11 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-l10n-en-gb all 1:5.1.0~rc3-0ubuntu1~trusty0 [492 kB]
Holen: 12 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-l10n-en-za all 1:5.1.0~rc3-0ubuntu1~trusty0 [411 kB]
Es wurden 68,5 MB in 1 min 3 s geholt (1.079 kB/s).                            
dpkg: parse error, in file '/var/lib/dpkg/status' near line 90 package 'python-pkg-resources':
 Feld »Depends«, ungültiger Paketname »python:any«: Zeichen »:« nicht erlaubt (nur Buchstaben, Ziffern und die Zeichen »-+._«)
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by Bashing-om on 2016-02-25
anna16; Hi !

The illiterate American that I am, I do not understand German ,
I can make out that there is still a problem with libfeoffice, skype and a issue reading the status file.

Let's see what we can find out about libreoffice. 
What returns:
```

LANG=C;apt-cache policy libreoffice

```

keeping in mind there is still the parsing error with the status file, and skype has an issue.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by anna16 on 2016-02-25
Oh, sorry. Holen means fetch and hängen ab von dependend of. If there's a bigger understanding problem in language, that's we're I can help. Just ask ;-)

Here's the next report for you:

```

k@Anna-PC:~$ LANG=C;apt-cache policy libreoffice
libreoffice:
  Installed: (none)
  Candidate: 1:5.1.0~rc3-0ubuntu1~trusty0
  Version table:
     1:5.1.0~rc3-0ubuntu1~trusty0 0
        500 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main amd64 Packages
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```

---

### Post by anna16 on 2016-02-25
And about the parse error, it says, that in the package name  »python:any«: the sign »:« is not allowed

---

### Post by QIII on 2016-02-25
anna16 --

You are using a PPA for LibreOffice.  Is there a reason you are doing that rather than using the normal repo?

Your problem lies here:

```
dpkg: parse error, in file '/var/lib/dpkg/status' near line 90 package 'python-pkg-resources':
 Feld »Depends«, ungültiger Paketname »python:any«: Zeichen »:« nicht erlaubt (nur Buchstaben, Ziffern und die Zeichen »-+._«)
```

Take special note of "*Zeichen »:« nicht erlaubt (nur Buchstaben, Ziffern und die Zeichen »-+._«)*".

For the sake of our English-speaking population, that is "*Symbol ":" not allowed (only letters, numerals and the symbols "-+._")*"

For whatever reason, Line 90 of one of your PPA sources contains the name "python:any" in the column "Depends", and the symbol ":" is not allowed.

That is something the PPA maintainer will have to fix.  You might try simply removing the PPA and using the normal Ubuntu repo unless there is something in the version in that PPA that you simply must have.

(Oh, anna, I just realized that "character" is probably a better idiomatic translation than either "sign" or "symbol".  For what it's worth.  We both understand the German.)

---

### Post by anna16 on 2016-02-25
Hi QIII,

where can I remove the PPA and use the normal ubuntu repo. You must know, I'm a complete newbee. Please explain me exactly where to find this and change it. Thank you ;-)

---

### Post by anna16 on 2016-02-25
Ok. I think I unticked the right boxes for PPA. After that I rerun the update. It doesn't really seem different to the post before... See for yourselves:

```

k@Anna-PC:~$ sudo apt update
[sudo] password for k:
Ign http://de.archive.ubuntu.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease     
Ign http://archive.canonical.com trusty InRelease  
OK   http://de.archive.ubuntu.com trusty-updates InRelease
OK   http://archive.canonical.com trusty Release.gpg
OK   http://extras.ubuntu.com trusty Release.gpg   
OK   http://de.archive.ubuntu.com trusty-security InRelease                
OK   http://archive.canonical.com trusty Release                               
OK   http://extras.ubuntu.com trusty Release                                   
OK   http://de.archive.ubuntu.com trusty Release.gpg                        
OK   http://de.archive.ubuntu.com trusty-updates/multiverse Sources
OK   http://archive.canonical.com trusty/partner Sources
OK   http://extras.ubuntu.com trusty/main Sources  
OK   http://de.archive.ubuntu.com trusty-updates/restricted Sources
OK   http://archive.canonical.com trusty/partner amd64 Packages
OK   http://extras.ubuntu.com trusty/main amd64 Packages
OK   http://de.archive.ubuntu.com trusty-updates/main Sources              
OK   http://archive.canonical.com trusty/partner Translation-en            
OK   http://de.archive.ubuntu.com trusty-updates/universe Sources
OK   http://de.archive.ubuntu.com trusty-updates/restricted amd64 Packages
OK   http://de.archive.ubuntu.com trusty-updates/main amd64 Packages
OK   http://de.archive.ubuntu.com trusty-updates/universe amd64 Packages
OK   http://de.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
OK   http://de.archive.ubuntu.com trusty-updates/main Translation-en
OK   http://de.archive.ubuntu.com trusty-updates/multiverse Translation-en
OK   http://de.archive.ubuntu.com trusty-updates/restricted Translation-en
OK   http://de.archive.ubuntu.com trusty-updates/universe Translation-en
OK   http://de.archive.ubuntu.com trusty-security/multiverse Sources
OK   http://de.archive.ubuntu.com trusty-security/restricted Sources
Ign http://extras.ubuntu.com trusty/main Translation-de_DE
Ign http://extras.ubuntu.com trusty/main Translation-de
OK   http://de.archive.ubuntu.com trusty-security/main Sources
Ign http://extras.ubuntu.com trusty/main Translation-en
OK   http://de.archive.ubuntu.com trusty-security/universe Sources
OK   http://de.archive.ubuntu.com trusty-security/restricted amd64 Packages
OK   http://de.archive.ubuntu.com trusty-security/main amd64 Packages
OK   http://de.archive.ubuntu.com trusty-security/universe amd64 Packages
OK   http://de.archive.ubuntu.com trusty-security/multiverse amd64 Packages
OK   http://de.archive.ubuntu.com trusty-security/main Translation-en
OK   http://de.archive.ubuntu.com trusty-security/multiverse Translation-en
OK   http://de.archive.ubuntu.com trusty-security/restricted Translation-en
OK   http://de.archive.ubuntu.com trusty-security/universe Translation-en
OK   http://de.archive.ubuntu.com trusty Release
OK   http://de.archive.ubuntu.com trusty/multiverse Sources
OK   http://de.archive.ubuntu.com trusty/restricted Sources
OK   http://de.archive.ubuntu.com trusty/main Sources
OK   http://de.archive.ubuntu.com trusty/universe Sources
OK   http://de.archive.ubuntu.com trusty/restricted amd64 Packages
OK   http://de.archive.ubuntu.com trusty/main amd64 Packages
OK   http://de.archive.ubuntu.com trusty/universe amd64 Packages
OK   http://de.archive.ubuntu.com trusty/multiverse amd64 Packages
OK   http://de.archive.ubuntu.com trusty/main Translation-de
OK   http://de.archive.ubuntu.com trusty/main Translation-en
OK   http://de.archive.ubuntu.com trusty/multiverse Translation-de
OK   http://de.archive.ubuntu.com trusty/multiverse Translation-en
OK   http://de.archive.ubuntu.com trusty/restricted Translation-de
OK   http://de.archive.ubuntu.com trusty/restricted Translation-en
OK   http://de.archive.ubuntu.com trusty/universe Translation-de
OK   http://de.archive.ubuntu.com trusty/universe Translation-en
Ign http://de.archive.ubuntu.com trusty/main Translation-de_DE
Ign http://de.archive.ubuntu.com trusty/multiverse Translation-de_DE
Ign http://de.archive.ubuntu.com trusty/restricted Translation-de_DE
Ign http://de.archive.ubuntu.com trusty/universe Translation-de_DE
Paketlisten werden gelesen... Fertig
k@Anna-PC:~$ sudo apt upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Probieren Sie »apt-get -f install«, um dies zu korrigieren.
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 libreoffice-core : Hängt ab von: libreoffice-common (> 1:4.3.2~rc2) ist aber nicht installiert
 libreoffice-help-en-us : Hängt ab von: libreoffice-l10n-en-us
 libreoffice-l10n-de : Hängt ab von: libreoffice-common ist aber nicht installiert
 libreoffice-l10n-en-gb : Hängt ab von: libreoffice-common ist aber nicht installiert
 libreoffice-l10n-en-za : Hängt ab von: libreoffice-common ist aber nicht installiert
 skype : Hängt ab von: skype-bin ist aber nicht installierbar
E: Unerfüllte Abhängigkeiten. Versuchen Sie, -f zu benutzen.
k@Anna-PC:~$ sudo apt-get -f install
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Abhängigkeiten werden korrigiert ... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  hyphen-de hyphen-en-us libboost-date-time1.54.0 libclucene-contribs1
  libclucene-core1 libcmis-0.4-4 libexttextcat-2.0-0 libexttextcat-data
  libglew1.10 libhyphen0 liblangtag-common liblangtag1 libmythes-1.2-0
  libneon27-gnutls libqt4-xml libqtcore4 libqtdbus4 libreoffice-style-galaxy
  mysql-common mythes-en-au openoffice.org-hyphenation qdbus qtchooser
  qtcore4-l10n uno-libs3 ure xfonts-mathml
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden Pakete werden ENTFERNT:
  libreoffice-base-core libreoffice-core libreoffice-help-de
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-l10n-de
  libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-math
  libreoffice-writer mythes-de mythes-de-ch mythes-en-us python3-uno skype
0 aktualisiert, 0 neu installiert, 15 zu entfernen und 511 nicht aktualisiert.
14 nicht vollständig installiert oder entfernt.
Nach dieser Operation werden 309 MB Plattenplatz freigegeben.
Möchten Sie fortfahren? [J/n] J
dpkg: parse error, in file '/var/lib/dpkg/status' near line 90 package 'python-pkg-resources':
 Feld »Depends«, ungültiger Paketname »python:any«: Zeichen »:« nicht erlaubt (nur Buchstaben, Ziffern und die Zeichen »-+._«)
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by Bashing-om on 2016-02-25
anna16; Well ...

I am having some level of difficulty deciding on a best means to resolve the libreoffice issue.

@QIII ; Sure glad to have another mind on this !

Generally it is my believe that libreoffice is deeply embedded within the operating system and a real chore to remove it and go back and fix what else the removal of libreoffice  removed.
This situation is compounded by the fact that the package manager "thinks" libreoffice is not installed:
> 
 k@Anna-PC:~$ LANG=C;apt-cache policy libreoffice
libreoffice:
  Installed: (none)
  Candidate: 1:5.1.0~rc3-0ubuntu1~trusty0
  Version table:
     1:5.1.0~rc3-0ubuntu1~trusty0 0
        500 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) trusty/main amd64 Packages

The package manager wants to install a higher version in your install;  what is currently available in the 14.04 software repository:
```

sysop@1404mini:~$ apt-cache show libreoffice
Package: libreoffice
<snip>
Version: 1:4.2.8-0ubuntu4
<snip>
Filename: pool/universe/libr/libreoffice/libreoffice_4.2.8-0ubuntu4_amd64.deb
Size: 26834
<snip>

```

I have in mind to see what we can do with ppa-purge in an attempt to get the libreoffice repo version to install onto your system. I trust that the package manager in in such a state that new software can be installed !
```

sudo apt install ppa-purge
sudo ppa-purge ppa:launchpad.net/libreoffice

```
If that runs, then we need to remove that 3rd party libreoffice source from the system.

A case of right wrong or otherwise.... but,
[INDENT][INDENT][INDENT]do something
[/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-02-25
Thank you so much for your help! This is my latest update:

```

k@Anna-PC:~$ sudo apt install ppa-purge
[sudo] password for k:  
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Probieren Sie »apt-get -f install«, um dies zu korrigieren:
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 libreoffice-core : Hängt ab von: libreoffice-common (> 1:4.3.2~rc2) soll aber nicht installiert werden
 libreoffice-help-en-us : Hängt ab von: libreoffice-l10n-en-us
 libreoffice-l10n-de : Hängt ab von: libreoffice-common soll aber nicht installiert werden
 libreoffice-l10n-en-gb : Hängt ab von: libreoffice-common soll aber nicht installiert werden
 libreoffice-l10n-en-za : Hängt ab von: libreoffice-common soll aber nicht installiert werden
 ppa-purge : Hängt ab von: aptitude (>= 0.6.6-1ubuntu1.2) soll aber nicht installiert werden
 skype : Hängt ab von: skype-bin ist aber nicht installierbar
E: Unerfüllte Abhängigkeiten. Versuchen Sie »apt-get -f install« ohne Angabe eines Pakets (oder geben Sie eine Lösung an).
k@Anna-PC:~$ sudo ppa-purge ppa:launchpad.net/libreoffice
sudo: ppa-purge: command not found

```

---

### Post by blm-ubunet on 2016-02-25
@bashing-om

That ppa:launchpad.net/libreoffice only has Libre Office 5 for trusty.. that's why LO is not installed from there.. She has not updated & never selected LO5 for install.

That ppa & LibreOffice5 (& python3) works well here on trusty.

Perhaps synaptic package manager is (always) the right tool.

---

### Post by Bashing-om on 2016-02-25
anna16; Ouch !!

That says we can not install any new software ( ppa-purge included) until we resolve libreofice.
YUK !
So we have 2 courses of action:
1) Fix the libreoffice install 
---------with a broken package manager ... good luck !, but we can try .
2) Purge libreoffice and deal with the consequences of having to replace dependencies for other applications.

Let's see what we can do about fixing the install .
Show me the English version of the package manager status:
```

LANG=C;sudo apt-get -f install

```

Then possible that " "python:any" line 90 may have a bearing on this ... as 'python' is a core component of the operating system ...
Open up the file /var/lib/dpkg/status in your favorite text editor 
Copy and paste the entire paragraph containing the line 90 back here to the thread and we consider editing out/changing  that offending character.

[INDENT][INDENT]between a big rock and a hard place
[INDENT][INDENT][INDENT]push real hard
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-02-26
Dear bashing-om,

this is the output in English:

```

k@Anna-PC:~$ LANG=C;sudo apt-get -f install
[sudo] password for k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  hyphen-de hyphen-en-us libboost-date-time1.54.0 libclucene-contribs1
  libclucene-core1 libcmis-0.4-4 libexttextcat-2.0-0 libexttextcat-data
  libglew1.10 libhyphen0 liblangtag-common liblangtag1 libmythes-1.2-0
  libneon27-gnutls libqt4-xml libqtcore4 libqtdbus4 libreoffice-style-galaxy
  mysql-common mythes-en-au openoffice.org-hyphenation qdbus qtchooser
  qtcore4-l10n uno-libs3 ure xfonts-mathml
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libreoffice-base-core libreoffice-core libreoffice-help-de
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-l10n-de
  libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-math
  libreoffice-writer mythes-de mythes-de-ch mythes-en-us python3-uno skype
0 upgraded, 0 newly installed, 15 to remove and 511 not upgraded.
14 not fully installed or removed.
After this operation, 309 MB disk space will be freed.
Do you want to continue? [Y/n] Y
dpkg: parse error, in file '/var/lib/dpkg/status' near line 90 package 'python-pkg-resources':
 `Depends' field, invalid package name `python:any': character `:' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by Bashing-om on 2016-02-26
anna16; Hey, hey ...

Now we are making progress .

And I have a better thought this AM .
As we have:
> 
0 upgraded, 0 newly installed, 15 to remove and [color=red]511 not upgraded[/color].

let's try and gt this system updated and the cruft removed !

Let's try this.
In software sources temporarily disable the libreoffice PPA, now in terminal, what results:
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```

we focus on getting this system updated, whatever that might take.

[INDENT][INDENT]if the package manager is not happy
[INDENT][INDENT][INDENT]nobody is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-02-26
Here we go:

```

k@Anna-PC:~$ LANG=C;sudo apt update
Ign http://extras.ubuntu.com trusty InRelease
Ign http://de.archive.ubuntu.com trusty InRelease
Ign http://archive.canonical.com trusty InRelease
Hit http://extras.ubuntu.com trusty Release.gpg
Hit http://de.archive.ubuntu.com trusty-updates InRelease
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://de.archive.ubuntu.com trusty-security InRelease                     
Hit http://extras.ubuntu.com trusty Release                          
Hit http://de.archive.ubuntu.com trusty Release.gpg                     
Hit http://archive.canonical.com trusty Release                       
Hit http://de.archive.ubuntu.com trusty-updates/multiverse Sources   
Hit http://extras.ubuntu.com trusty/main Sources
Hit http://archive.canonical.com trusty/partner Sources
Hit http://de.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://extras.ubuntu.com trusty/main amd64 Packages
Hit http://archive.canonical.com trusty/partner amd64 Packages       
Hit http://de.archive.ubuntu.com trusty-updates/main Sources         
Hit http://de.archive.ubuntu.com trusty-updates/universe Sources
Hit http://archive.canonical.com trusty/partner Translation-en
Hit http://de.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://de.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://de.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://de.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://de.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://de.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://de.archive.ubuntu.com trusty-updates/restricted Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en
Hit http://de.archive.ubuntu.com trusty-updates/universe Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-de
Hit http://de.archive.ubuntu.com trusty-security/multiverse Sources
Hit http://de.archive.ubuntu.com trusty-security/restricted Sources
Hit http://de.archive.ubuntu.com trusty-security/main Sources
Hit http://de.archive.ubuntu.com trusty-security/universe Sources
Hit http://de.archive.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://de.archive.ubuntu.com trusty-security/main amd64 Packages
Hit http://de.archive.ubuntu.com trusty-security/universe amd64 Packages
Hit http://de.archive.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://de.archive.ubuntu.com trusty-security/main Translation-en
Hit http://de.archive.ubuntu.com trusty-security/multiverse Translation-en
Hit http://de.archive.ubuntu.com trusty-security/restricted Translation-en
Hit http://de.archive.ubuntu.com trusty-security/universe Translation-en
Hit http://de.archive.ubuntu.com trusty Release
Hit http://de.archive.ubuntu.com trusty/multiverse Sources
Hit http://de.archive.ubuntu.com trusty/restricted Sources
Hit http://de.archive.ubuntu.com trusty/main Sources
Hit http://de.archive.ubuntu.com trusty/universe Sources
Hit http://de.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://de.archive.ubuntu.com trusty/main amd64 Packages
Hit http://de.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://de.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://de.archive.ubuntu.com trusty/main Translation-en
Hit http://de.archive.ubuntu.com trusty/main Translation-de
Hit http://de.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://de.archive.ubuntu.com trusty/multiverse Translation-de
Hit http://de.archive.ubuntu.com trusty/restricted Translation-en
Hit http://de.archive.ubuntu.com trusty/restricted Translation-de
Hit http://de.archive.ubuntu.com trusty/universe Translation-en
Hit http://de.archive.ubuntu.com trusty/universe Translation-de
Reading package lists... Done
k@Anna-PC:~$ LANG=C;sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try using -f.
k@Anna-PC:~$ LANG=C;sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try using -f.

```

---

### Post by Bashing-om on 2016-02-26
anna16; Well ..

That last looks promising ..

What now results :
```

sudo apt install ppa-purge

```
as we try and get libreoffice reverted to that of our software repository.

my little mind
[INDENT][INDENT][INDENT]one thing at a time
[/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-02-27
That's the answer of my terminal, my dear bashing-om:

```

k@Anna-PC:~$ LANG=C;sudo apt install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 ppa-purge : Depends: aptitude (>= 0.6.6-1ubuntu1.2) but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2016-02-27
anna16; Yuk !

What a sloppyation, stuck in a catch 22 situation ( American slang) . We need to fix libreoffice, but libreoffice has broken the package management system; I for sure do not want to remove libreoffice from the system to resolve this .. the cure most likely will be worse than the ailment.

Let's do this ... 
take a look at what is:
Post back:
```

apt-cache policy libreoffice-common
apt-cache policy libreoffice-core
apt-cache policy skype-bin
apt-cache policy skype

```
look'n that python is a common element ... and in that case we fix that status file ; and see if we can move forward.

[INDENT][INDENT]of at 1st you do not succeed
[INDENT][INDENT][INDENT]do something else, right wrong or otherwise
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-02-27
Here we go:

```

k@Anna-PC:~$ apt-cache policy libreoffice-common
libreoffice-common:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
k@Anna-PC:~$ apt-cache policy libreoffice-core
libreoffice-core:
  Installed: 1:4.3.2~rc2-0ubuntu1~trusty2
  Candidate: 1:4.3.2~rc2-0ubuntu1~trusty2
  Version table:
 *** 1:4.3.2~rc2-0ubuntu1~trusty2 0
        100 /var/lib/dpkg/status
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
k@Anna-PC:~$ apt-cache policy skype-bin
skype-bin:
  Installed: (none)
  Candidate: (none)
  Version table:
k@Anna-PC:~$ apt-cache policy skype
skype:
  Installed: 4.3.0.37-0ubuntu0.12.04.1
  Candidate: 4.3.0.37-0ubuntu0.12.04.1
  Version table:
 *** 4.3.0.37-0ubuntu0.12.04.1 0
        500 http://archive.canonical.com/ubuntu/ trusty/partner amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Bashing-om on 2016-02-27
anna16; Well !

Pleasantly surprised; the required packages are from our repo .
Let's try:
```

sudo apt update
sudo apt install libreoffice-l10n-en-us libreoffice-common

sudo apt install skype-bin

sudo apt-get -f install

```
where I do not know what to expect as results. see what happens .. I do anticipate that attempting to install "skype-bin" the system  will scream and holler. We want to know what the screaming is and take action .

Still pending is looking at the status file line 90 .

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-02-29
Hi bashing-om,

sorry it took a while. But here's the answer of my terminal:

```

k@Anna-PC:~$ LANG=C;sudo apt update
[sudo] password for k: 
Ign http://de.archive.ubuntu.com trusty InRelease                   
Ign http://archive.canonical.com trusty InRelease                   
Ign http://extras.ubuntu.com trusty InRelease                       
Get:1 http://de.archive.ubuntu.com trusty-updates InRelease [65.9 kB]
Hit http://archive.canonical.com trusty Release.gpg                           
Get:2 http://extras.ubuntu.com trusty Release.gpg [72 B]                      
Hit http://archive.canonical.com trusty Release                               
Hit http://extras.ubuntu.com trusty Release                
Get:3 http://de.archive.ubuntu.com trusty-security InRelease [65.9 kB]     
Hit http://archive.canonical.com trusty/partner Sources               
Hit http://extras.ubuntu.com trusty/main Sources                      
Hit http://archive.canonical.com trusty/partner amd64 Packages
Hit http://extras.ubuntu.com trusty/main amd64 Packages    
Hit http://archive.canonical.com trusty/partner Translation-en
Hit http://de.archive.ubuntu.com trusty Release.gpg                        
Get:4 http://de.archive.ubuntu.com trusty-updates/multiverse Sources [5547 B]
Get:5 http://de.archive.ubuntu.com trusty-updates/restricted Sources [5352 B]
Get:6 http://de.archive.ubuntu.com trusty-updates/main Sources [260 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-de
Get:7 http://de.archive.ubuntu.com trusty-updates/universe Sources [150 kB]
Get:8 http://de.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:9 http://de.archive.ubuntu.com trusty-updates/main amd64 Packages [710 kB]
Get:10 http://de.archive.ubuntu.com trusty-updates/universe amd64 Packages [338 kB]
Get:11 http://de.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:12 http://de.archive.ubuntu.com trusty-updates/main Translation-en [359 kB]
Get:13 http://de.archive.ubuntu.com trusty-updates/multiverse Translation-en [6947 B]
Get:14 http://de.archive.ubuntu.com trusty-updates/restricted Translation-en [3699 B]
Get:15 http://de.archive.ubuntu.com trusty-updates/universe Translation-en [180 kB]
Get:16 http://de.archive.ubuntu.com trusty-security/multiverse Sources [2767 B]
Get:17 http://de.archive.ubuntu.com trusty-security/restricted Sources [4035 B]
Get:18 http://de.archive.ubuntu.com trusty-security/main Sources [105 kB]
Get:19 http://de.archive.ubuntu.com trusty-security/universe Sources [33.0 kB]
Get:20 http://de.archive.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:21 http://de.archive.ubuntu.com trusty-security/main amd64 Packages [428 kB]
Get:22 http://de.archive.ubuntu.com trusty-security/universe amd64 Packages [124 kB]
Get:23 http://de.archive.ubuntu.com trusty-security/multiverse amd64 Packages [4990 B]
Get:24 http://de.archive.ubuntu.com trusty-security/main Translation-en [234 kB]
Get:25 http://de.archive.ubuntu.com trusty-security/multiverse Translation-en [2570 B]
Get:26 http://de.archive.ubuntu.com trusty-security/restricted Translation-en [3206 B]
Get:27 http://de.archive.ubuntu.com trusty-security/universe Translation-en [72.6 kB]
Hit http://de.archive.ubuntu.com trusty Release                        
Hit http://de.archive.ubuntu.com trusty/multiverse Sources
Hit http://de.archive.ubuntu.com trusty/restricted Sources                     
Hit http://de.archive.ubuntu.com trusty/main Sources                           
Hit http://de.archive.ubuntu.com trusty/universe Sources                       
Hit http://de.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://de.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://de.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://de.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://de.archive.ubuntu.com trusty/main Translation-en                    
Hit http://de.archive.ubuntu.com trusty/main Translation-de                    
Hit http://de.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://de.archive.ubuntu.com trusty/multiverse Translation-de              
Hit http://de.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://de.archive.ubuntu.com trusty/restricted Translation-de              
Hit http://de.archive.ubuntu.com trusty/universe Translation-en                
Hit http://de.archive.ubuntu.com trusty/universe Translation-de                
Fetched 3206 kB in 6s (484 kB/s)                                               
Reading package lists... Done
k@Anna-PC:~$ sudo apt install libreoffice-l10n-en-us libreoffice-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libreoffice-common' instead of 'libreoffice-l10n-en-us'
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-common : Breaks: libreoffice-core (>= 1:4.3~) but 1:4.3.2~rc2-0ubuntu1~trusty2 is to be installed
                      Breaks: libreoffice-style-galaxy (>= 1:4.3~) but 1:4.3.2~rc2-0ubuntu1~trusty2 is to be installed
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but 1:4.2.8-0ubuntu4 is to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
k@Anna-PC:~$ sudo apt install skype-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'skype-bin' has no installation candidate
k@Anna-PC:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  hyphen-de hyphen-en-us libboost-date-time1.54.0 libclucene-contribs1
  libclucene-core1 libcmis-0.4-4 libexttextcat-2.0-0 libexttextcat-data
  libglew1.10 libhyphen0 liblangtag-common liblangtag1 libmythes-1.2-0
  libneon27-gnutls libqt4-xml libqtcore4 libqtdbus4 libreoffice-style-galaxy
  mysql-common mythes-en-au openoffice.org-hyphenation qdbus qtchooser
  qtcore4-l10n uno-libs3 ure xfonts-mathml
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libreoffice-base-core libreoffice-core libreoffice-help-de
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-l10n-de
  libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-math
  libreoffice-writer mythes-de mythes-de-ch mythes-en-us python3-uno skype
0 upgraded, 0 newly installed, 15 to remove and 512 not upgraded.
14 not fully installed or removed.
After this operation, 309 MB disk space will be freed.
Do you want to continue? [Y/n] Y
dpkg: parse error, in file '/var/lib/dpkg/status' near line 90 package 'python-pkg-resources':
 `Depends' field, invalid package name `python:any': character `:' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)

```·

---

### Post by Bashing-om on 2016-02-29
anna16; Hey ...

A bit better looking ...Maybe making a bit of headway ... what we did is encouraging .

OK .. the package manager says :
> 
libreoffice-common : Breaks: libreoffice-core (>= 1:4.3~) but 1:4.3.2~rc2-0ubuntu1~trusty2 is to be installed
                      Breaks: libreoffice-style-galaxy (>= 1:4.3~) but 1:4.3.2~rc2-0ubuntu1~trusty2 is to be installed
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but 1:4.2.8-0ubuntu4 is to be installed
 
It wants packages from that PPA; 
as in our repository is:
> 
sysop@1404mini:~$ apt list libreoffice-core
Listing... Done
libreoffice-core/trusty-updates,trusty-security 1:4.2.8-0ubuntu4 amd64
sysop@1404mini:~$ 

sysop@1404mini:~$ apt list libreoffice-style-galaxy
Listing... Done
libreoffice-style-galaxy/trusty-updates,trusty-security 1:4.2.8-0ubuntu4 all
sysop@1404mini:~$ 

sysop@1404mini:~$ apt list libreoffice-common 
Listing... Done
libreoffice-common/trusty-updates,trusty-security 1:4.2.8-0ubuntu4 all
sysop@1404mini:~$
##which is the one we want installed .


Let's try this again .. in software sources disable all the 3rd party sources for libreoffice, so when we try and install we are sure to be pulling from our repository.

Now run:
```

sudo apt update
sudo apt install libreoffice-core libreoffice-style-galaxy libreoffice-common

```
See if the package manager will do that for us ... before we get radical.

Still pending is the status file line 90, and skype.

[INDENT][INDENT]poke at it long enough
[INDENT][INDENT][INDENT]got to be a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-02
It's all Chinese to me. ;-) I'm so happy that you help me!

I disabled everything in software sources except for the canonical-partner. Is that right?

Here we go with the rest:
```

k@Anna-PC:~$ LANG=C;sudo apt update
[sudo] password for k: 
Ign http://archive.canonical.com trusty InRelease
Ign http://de.archive.ubuntu.com trusty InRelease
Hit http://archive.canonical.com trusty Release.gpg
Hit http://de.archive.ubuntu.com trusty-updates InRelease
Hit http://archive.canonical.com trusty Release
Hit http://de.archive.ubuntu.com trusty-security InRelease
Hit http://archive.canonical.com trusty/partner Sources                 
Hit http://de.archive.ubuntu.com trusty Release.gpg
Hit http://archive.canonical.com trusty/partner amd64 Packages
Hit http://de.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://archive.canonical.com trusty/partner Translation-en
Hit http://de.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://de.archive.ubuntu.com trusty-updates/main Sources
Hit http://de.archive.ubuntu.com trusty-updates/universe Sources
Hit http://de.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://de.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://de.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://de.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://de.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://de.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://de.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://de.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://de.archive.ubuntu.com trusty-security/multiverse Sources
Hit http://de.archive.ubuntu.com trusty-security/restricted Sources
Hit http://de.archive.ubuntu.com trusty-security/main Sources
Hit http://de.archive.ubuntu.com trusty-security/universe Sources
Hit http://de.archive.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://de.archive.ubuntu.com trusty-security/main amd64 Packages
Hit http://de.archive.ubuntu.com trusty-security/universe amd64 Packages
Hit http://de.archive.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://de.archive.ubuntu.com trusty-security/main Translation-en
Hit http://de.archive.ubuntu.com trusty-security/multiverse Translation-en
Hit http://de.archive.ubuntu.com trusty-security/restricted Translation-en
Hit http://de.archive.ubuntu.com trusty-security/universe Translation-en
Hit http://de.archive.ubuntu.com trusty Release
Hit http://de.archive.ubuntu.com trusty/multiverse Sources
Hit http://de.archive.ubuntu.com trusty/restricted Sources
Hit http://de.archive.ubuntu.com trusty/main Sources
Hit http://de.archive.ubuntu.com trusty/universe Sources
Hit http://de.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://de.archive.ubuntu.com trusty/main amd64 Packages
Hit http://de.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://de.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://de.archive.ubuntu.com trusty/main Translation-en
Hit http://de.archive.ubuntu.com trusty/main Translation-de
Hit http://de.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://de.archive.ubuntu.com trusty/multiverse Translation-de
Hit http://de.archive.ubuntu.com trusty/restricted Translation-en
Hit http://de.archive.ubuntu.com trusty/restricted Translation-de
Hit http://de.archive.ubuntu.com trusty/universe Translation-en
Hit http://de.archive.ubuntu.com trusty/universe Translation-de
Reading package lists... Done
k@Anna-PC:~$ sudo apt install libreoffice-core libreoffice-style-galaxy libreoffice-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libreoffice-style-galaxy is already the newest version.
libreoffice-style-galaxy set to manually installed.
libreoffice-core is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-common : Breaks: libreoffice-core (>= 1:4.3~) but 1:4.3.2~rc2-0ubuntu1~trusty2 is to be installed
                      Breaks: libreoffice-style-galaxy (>= 1:4.3~) but 1:4.3.2~rc2-0ubuntu1~trusty2 is to be installed
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but 1:4.2.8-0ubuntu4 is to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2016-03-02
anna16; Well ..

Looks hopeful ..

OK .. let's try:
```

sudo apt remove libreoffice-style-galaxy libreoffice-core libreoffice-common
sudo apt install libreoffice-style-galaxy libreoffice-core libreoffice-common

```
As we try and get version 1:4.2.8-0ubuntu4 of all the libraries to install .
As advised, I am reticent to do a wholesale removal of libreoffice. I do prefer to work on this a piece at the time and try and get all the pieces ironed out.

It might be that I do not have the correct order ... the package manager will tell us what we need to do in this case.

[INDENT][INDENT]keep pecking away at the problem
[INDENT][INDENT][INDENT]something is going to give
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-04
You're invalueable. Thank's for helping!

Here's our latest results:

```

k@Anna-PC:~$ LANG=C;sudo apt remove libreoffice-style-galaxy libreoffice-core libreoffice-common
[sudo] password for k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libreoffice-common' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-base-core : Depends: libreoffice-core (= 1:4.3.2~rc2-0ubuntu1~trusty2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
                          Recommends: libreoffice-core (> 1:4.2.6.3) but it is not going to be installed or
                                      language-support-translations-en but it is not installable
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
                       Recommends: libreoffice-core (> 1:4.2.6.3) but it is not going to be installed or
                                   language-support-translations-de but it is not installable
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
                          Recommends: libreoffice-core (> 1:4.2.6.3) but it is not going to be installed or
                                      language-support-translations-en but it is not installable
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
                          Recommends: libreoffice-core (> 1:4.2.6.3) but it is not going to be installed or
                                      language-support-translations-en but it is not installable
 libreoffice-math : Depends: libreoffice-core (= 1:4.3.2~rc2-0ubuntu1~trusty2) but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-core (= 1:4.3.2~rc2-0ubuntu1~trusty2) but it is not going to be installed
 mythes-de : Depends: libreoffice-core but it is not going to be installed or
                      openoffice.org-core (>= 3.0~) but it is not installable
 mythes-de-ch : Depends: libreoffice-core but it is not going to be installed or
                         openoffice.org-core (>= 3.0~) but it is not installable
 mythes-en-us : Depends: libreoffice-core but it is not going to be installed or
                         openoffice.org-core (>= 1.9) but it is not installable or
                         language-support-writing-en but it is not installable
 python3-uno : Depends: libreoffice-core (= 1:4.3.2~rc2-0ubuntu1~trusty2) but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
k@Anna-PC:~$ sudo apt install libreoffice-style-galaxy libreoffice-core libreoffice-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libreoffice-style-galaxy is already the newest version.
libreoffice-style-galaxy set to manually installed.
libreoffice-core is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-common : Breaks: libreoffice-core (>= 1:4.3~) but 1:4.3.2~rc2-0ubuntu1~trusty2 is to be installed
                      Breaks: libreoffice-style-galaxy (>= 1:4.3~) but 1:4.3.2~rc2-0ubuntu1~trusty2 is to be installed
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but 1:4.2.8-0ubuntu4 is to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2016-03-04
anna16; Morning ...

Well, we have another piece of the puzzle:
> 
libreoffice-base-core : Depends: libreoffice-core (= 1:4.3.2~rc2-0ubuntu1~trusty2)

From the PPA .., where we want to install from our repo:
```

sysop@1404mini:~$ apt list libreoffice-core
Listing... Done
libreoffice-core/trusty-updates,trusty-security 1:4.2.8-0ubuntu4 amd64
sysop@1404mini:~$

```

However, now that status line 90 appears to be rearing it's head:
> 
python3-uno : Depends: libreoffice-core (= 1:4.3.2~rc2-0ubuntu1~trusty2)


Let's fix this control file and then go back to working the libreoffice puzzle .

Open up the file " /var/lib/dpkg/status" in your favorite text editor ( gedit ) :
```

gedit /var/lib/dpkg/status

```
Copy and paste that entire paragraph containing line 90 back here for our inspection. We see what it is that the package manager is unhappy about.

[INDENT][INDENT]it is what it is
[INDENT][INDENT][INDENT]we best deal with it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-07
Well, we do have a problem here, I guess... Because I can't find gedit on my computer and I can't install it either :confused:

The terminal said this after my try to install it anyways:
```

sudo apt-get install gedit
k@Anna-PC:~$ sudo apt-get install gedit
[sudo] password for k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gedit : Depends: libgtksourceview-3.0-1 (>= 3.10.0) but it is not going to be installed
         Depends: libpeas-1.0-0 (>= 1.1.0) but it is not going to be installed
         Depends: libzeitgeist-2.0-0 (>= 0.9.9) but it is not going to be installed
         Depends: gedit-common (>= 3.10) but it is not going to be installed
         Depends: gedit-common (< 3.11) but it is not going to be installed
         Depends: gir1.2-peas-1.0 but it is not going to be installed
         Recommends: gir1.2-gtksource-3.0 but it is not going to be installed
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by anna16 on 2016-03-07
Ah! Now I got it! I had mousepad on my computer and I think I was able to get your information now! :D

Look:
```

Package: xserver-xorg-input-vmmouse
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 114
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1:13.0.0-1build1
Provides: xorg-driver-input
Depends: libc6 (>= 2.7), xorg-input-abi-20, xserver-xorg-core (>= 2:1.14.99.902), xserver-xorg-input-mouse, udev
Description: X.Org X server -- VMMouse input driver to use with VMWare
 This package provides the driver for the X11 vmmouse input device.
 .
 The VMMouse driver enables support for the special VMMouse protocol
 that is provided by VMware virtual machines to give absolute pointer
 positioning.
 .
 The vmmouse driver is capable of falling back to the standard "mouse"
 driver if a VMware virtual machine is not detected. This allows for
 dual-booting of an operating system from a virtual machine to real hardware
 without having to edit xorg.conf every time.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xf86-input-vmmouse driver module.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

Package: libmono-system-data4.0-cil
Status: install ok installed
Priority: optional
Section: cli-mono
Installed-Size: 1767
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: mono
Version: 3.2.8+dfsg-4ubuntu1
Depends: libmono-corlib4.5-cil (>= 3.2.8), libmono-data-tds4.0-cil (>= 3.0.6), libmono-system-configuration4.0-cil (>= 1.0), libmono-system-enterpriseservices4.0-cil (>= 1.0), libmono-system-transactions4.0-cil (>= 1.0), libmono-system-xml4.0-cil (>= 3.2.1), libmono-system4.0-cil (>= 3.2.8)
Suggests: libglib2.0-0 (>= 2.39.90)
Description: Mono System.Data library (for CLI 4.0)
 Mono is a platform for running and developing applications based on the
 ECMA/ISO Standards. Mono is an open source effort led by Xamarin.
 Mono provides a complete CLR (Common Language Runtime) including compiler and
 runtime, which can produce and execute CIL (Common Intermediate Language)
 bytecode (aka assemblies), and a class library.
 .
 This package contains the Mono System.Data library for CLI 4.0.
Original-Maintainer: Debian Mono Group <pkg-mono-group@lists.alioth.debian.org>
Homepage: http://www.mono-project.com/

Package: ubuntu-release-upgrader-gtk
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 218
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: ubuntu-release-upgrader
Version: 1:0.220.4
Depends: ubuntu-release-upgrader-core (= 1:0.220.4), update-manager, python3-distupgrade (= 1:0.220.4), python3-dbus, python3-gi (>= 3.8), gir1.2-vte-2.90, gir1.2-gtk-3.0, gir1.2-webkit-3.0
Description: manage release upgrades
 This is the GTK+ frontend of the Ubuntu Release Upgrader

Package: libgtkspell0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 96
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: gtkspell
Version: 2.0.16-1ubuntu7
Depends: libc6 (>= 2.2.5), libenchant1c2a (>= 1.6.0), libglib2.0-0 (>= 2.24.0), libgtk2.0-0 (>= 2.8.0)
Description: a spell-checking addon for GTK's TextView widget
 GtkSpell provides MSWord/MacOSX-style highlighting of misspelled words in a
 GtkTextView widget.  Right-clicking a misspelled word pops up a menu of
 suggested replacements.
Original-Maintainer: Ari Pollak <ari@debian.org>

Package: python-pkg-resources
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 182
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: python-setuptools
Version: 3.3-1ubuntu1
Provides: python2.7-setuptools
**Depends: python:any (>= 2.7), python:any (<< 2.8)**
Suggests: python-distribute, python-distribute-doc
Conflicts: python-setuptools (<< 0.6c8-3)
Description: Package Discovery and Resource Access using pkg_resources
 The pkg_resources module provides an API for Python libraries to
 access their resource files, and for extensible applications and
 frameworks to automatically discover plugins.  It also provides
 runtime support for using C extensions that are inside zipfile-format
 eggs, support for merging packages that have separately-distributed
 modules or subpackages, and APIs for managing Python's current
 "working set" of active packages.
Original-Maintainer: Matthias Klose <doko@debian.org>
Homepage: https://pypi.python.org/pypi/setuptools
Python-Version: 2.7

```

---

### Post by anna16 on 2016-03-07
Line 90 says:

Depends: python:any (>= 2.7), python:any (<< 2.8)

---

### Post by Bashing-om on 2016-03-07
anna16; Ouch !

My apologies for my direction to use the text editor 'gedit', I failed to take into account that perhaps your install was different than 'ubuntu proper' . . I often am a victim of my own tunnel vision and do not see these small things within the big picture.


What have we got going on here ?

The syntax is correct and it reads - the package python to support " python-pkg-resources " must be a version greater than 2.7.XXX and must be less than version 2.8.XXXX.
My installed version of 'python' is " ii  python         2.7.5-5ubunt amd64" .

Now the crunch:
> 
sysop@1404mini:~$ apt list Package: python-pkg-resources
Listing... Done
python-pkg-resources/trusty-updates 3.3-1ubuntu2 all
sysop@1404mini:~$


I do not have that package installed on my system .. so not able to directly verify what should be ... but we can accurately surmise what should be:
post back:
```

dpkg -l python-pkg-resources
apt-cache policy python-pkg-resources

```
to identify the version installed and where it came from.

then we want to know about 'python' .. does the installed version match what is required " python:any (>= 2.7), python:any (<< 2.8)" ? :
```

dpkg -l python

```
and did 'python' come from our repo ?:
```

apt-cache policy python

```

Yuk !! And now there is in addition the dependency issues of attempting to install 'gedit' .. What in the world is holding these libraries to an old version ?
for reference what "should be" :
> 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libgtksourcevi 3.10.2-0ubun amd64        shared libraries for the GTK+ syn
sysop@1404mini:~$
 as you can see meets 'gedit's' support requirement on my system.
And last but not least is " python3-uno" from the error condition noted earlier, is this the correct version installed ?
```

dpkg -l python3-uno
apt list python3-uno
apt-cache policy python3-uno

```

All this so we can figure out what is going on that libreoffice is in such a mess and what we must do to straighten libreoffice out. Find out why the libraries are old versions .

[INDENT][INDENT]putting this puzzle together
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-03-08
anna16; OK;

Now that I have a chance to further consider - knowing my tunnel vision condition - and looking further .. that line 90 situation:
see line 92 ! :
> 
Conflicts: python-setuptools [color=red](<< 0.6c8-3)[/color]

I can not see that as a valid version number .. but the package is not installed on my system and I presently do not know how to verify what the version description should be.
Let's see if your system can provide a better description. What returns from terminal command:
```

cat /var/lib/dpkg/status | grep python-setuptools

```


Looking to find that common denominator for all the dependency issues. I have a thought of where this might lead .. we will see what we will see.

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-08
Alright. My terminal's answer is this:

```

k@Anna-PC:~$ LANG=C;cat /var/lib/dpkg/status | grep python-setuptools
Source: python-setuptools
Conflicts: python-setuptools (<< 0.6c8-3)
Source: python-setuptools

```

---

### Post by anna16 on 2016-03-08
And now the answers to your first questions... Just saw that I only answered your last post...

1, about the version and python-pkg-resources:
```

k@Anna-PC:~$ dpkg -l python-pkg-resources
dpkg-query: error: file triggers record mentions illegal package name `mime-support/noawait:' (for interest in file `/usr/lib/mime/packages'): illegal package name in specifier 'mime-support/noawait:': character `/' not allowed (only letters, digits and characters `-+._')
k@Anna-PC:~$ apt-cache policy python-pkg-resources
python-pkg-resources:
  Installed: 3.3-1ubuntu1
  Candidate: 3.3-1ubuntu2
  Version table:
     3.3-1ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 3.3-1ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

2, about 'python' and if the installed version matches what is required " python:any (>= 2.7), python:any (<< 2.8)":
```

k@Anna-PC:~$ dpkg -l python
dpkg-query: error: file triggers record mentions illegal package name `mime-support/noawait:' (for interest in file `/usr/lib/mime/packages'): illegal package name in specifier 'mime-support/noawait:': character `/' not allowed (only letters, digits and characters `-+._')

```

3, if 'python' came from our repo:
```

k@Anna-PC:~$ apt-cache policy python
python:
  Installed: 2.7.5-5ubuntu3
  Candidate: 2.7.5-5ubuntu3
  Version table:
 *** 2.7.5-5ubuntu3 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

4, about " python3-uno":
```

k@Anna-PC:~$ dpkg -l python3-uno
dpkg-query: error: file triggers record mentions illegal package name `mime-support/noawait:' (for interest in file `/usr/lib/mime/packages'): illegal package name in specifier 'mime-support/noawait:': character `/' not allowed (only letters, digits and characters `-+._')
k@Anna-PC:~$ apt list python3-uno
Listing... Done
python3-uno/now 1:4.3.2~rc2-0ubuntu1~trusty2 amd64 [installed,local]
k@Anna-PC:~$ apt-cache policy python3-uno
python3-uno:
  Installed: 1:4.3.2~rc2-0ubuntu1~trusty2
  Candidate: 1:4.3.2~rc2-0ubuntu1~trusty2
  Version table:
 *** 1:4.3.2~rc2-0ubuntu1~trusty2 0
        100 /var/lib/dpkg/status
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

---

### Post by Bashing-om on 2016-03-08
anna16; Well. well, well ....

curious and curiouser ...

The package python-uno is an elevated version, still do not know the why as the package manager can not now tell us.
I will think on that and see what I can come up with.

of greater import presently is:
> 
dpkg-query: error: file triggers record mentions illegal package name `mime-support/noawait:' (for interest in file `/usr/lib/mime/packages'): illegal package name in specifier 'mime-support/noawait:': character `/' not allowed (only letters, digits and characters `-+._')
k@Anna-PC:~$


Let's see what is in that file:
```

cat /usr/lib/mime/packages/mime-support

```
that the package manager is so unhappy about.

And back to " python-setuptools (<< 0.6c8-3) " also no help yet to identify what the listed correct version should be.
How about any better return:
```

LANG=C;cat /var/lib/dpkg/status-old | grep python-setuptools

```
where we look in the backup status file, see if it too is the same .
---------------------------

We do know that at some point we are going to remove 
> 
python3-uno:
Installed: 1:4.3.2~rc2-0ubuntu1~trusty2
*** 1:4.3.2~rc2-0ubuntu1~trusty2 0
        100 /var/lib/dpkg/status
##where what we want:
1:4.2.8-0ubuntu4 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages

when we get all of our ducks in one row ( duck hunting, easy shooting).

[INDENT][INDENT]as around and around we go
[INDENT][INDENT][INDENT]where will we stop ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-11
The file cat /usr/lib/mime/packages/mime-support says:

```

k@Anna-PC:~$ cat /usr/lib/mime/packages/mime-support
application/x-debian-package; /usr/lib/mime/debian-view %s; needsterminal; description=Debian GNU/Linux Package; nametemplate=%s.deb; priority=0
#audio/basic; /usr/lib/mime/playaudio %s; description=Basic uLaw Audio; nametemplate=%s.au; priority=0

```

cat /var/lib/dpkg/status-old | grep python-setuptools answer is:
```

k@Anna-PC:~$ LANG=C;cat /var/lib/dpkg/status-old | grep python-setuptools
Source: python-setuptools
Conflicts: python-setuptools (<< 0.6c8-3)
Source: python-setuptools

```

---

### Post by Bashing-om on 2016-03-11
anna16; sorry;


My ignorance is really showing through .

I can find now way to verify that " 0.6c8-3" is valid ! There must be some way but I just do not know.
```

python-setuptools (<< 0.6c8-3)

```

Nor :
```

dpkg-query: error: file triggers record mentions illegal package name `mime-support/noawait:' 

```
are my bash skills adequate to read what is required in the referenced file.

We will await others here to alleviate my condition of ignorance.

Though inconvenient,
[INDENT][INDENT][INDENT]there is good when things like this happen to me
[/INDENT][/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-03-11
I know how you feel Bashing-om but you are far from ignorant..
Not sure if this will help or not but worth a look 
```
[SIZE=3]python-setuptools 0.6c8-3 source package in Ubuntu
[/SIZE][SIZE=3]                               [/SIZE][SIZE=3]                                [/SIZE]
[SIZE=3]             [/SIZE]
[SIZE=3]                           [/SIZE][SIZE=3]                            [/SIZE]
[SIZE=3]                                      [/SIZE][h=2][SIZE=3]Changelog[/SIZE][/h]         python-setuptools (0.6c8-3) unstable; urgency=low

  * Move site.py into the python-pkg-resources package.

python-setuptools (0.6c8-2) unstable; urgency=low

  * python-pkg-resources: Conflict with python-setuptools. Closes: #468944.

python-setuptools (0.6c8-1) unstable; urgency=low
```
Source [https://launchpad.net/ubuntu/+source/python-setuptools/0.6c8-3](https://launchpad.net/ubuntu/+source/python-setuptools/0.6c8-3)
Witch was dated way back Tue,  24 Jun 2008 00:57:37 +0100
It may help, if they post the section of /var/lib/dpkg/status around line 114
Did they upgrade from 12.04?
Maybe this might also help
```
apt-cache show python-pip | grep -E '^(Package|Version|Depends|Conflicts)'
```

---

### Post by Bashing-om on 2016-03-11
@runrickus :)

You sure do good work, cause I was getting frustrated .

That do deepen the puzzle ! I will go back and re-examine this sloppyation in respect to the info you have provided and await the OP to provide the new info .

I say again
[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-11
Thank you rinrickus and bashing-om!

Here's my terminals answer to your last command:

```

k@Anna-PC:~$ apt-cache show python-pip | grep -E '^(Package|Version|Depends|Conflicts)'
Package: python-pip
Version: 1.5.4-1ubuntu3
Depends: ca-certificates, python-colorama, python-distlib, python-html5lib, python-pip-whl (= 1.5.4-1ubuntu3), python-pkg-resources, python-requests, python-setuptools (>= 0.6c1), python-six, python, python:any (<< 2.8), python:any (>= 2.7.5-5~)
Package: python-pip
Version: 1.5.4-1
Depends: python (>= 2.7), python (<< 2.8), python:any (>= 2.7.1-0ubuntu2), ca-certificates, python-colorama, python-distlib, python-html5lib, python-pkg-resources, python-setuptools (>= 0.6c1), python-six, python-requests

```

---

### Post by Bashing-om on 2016-03-11
anna16; Yuk;

Confused as to what we are looking at on that last output:
> 
Package: python-pip
Version: 1.5.4-1ubuntu3
-bk-
Package: python-pip
Version: 1.5.4-1

where the repo has version:
```

sysop@1404mini:~$ apt list python-pip
Listing... Done
python-pip/trusty-updates 1.5.4-1ubuntu3 all

```

Let us at this time clarify what you have installed and what the options are:
post back:
```

apt-cache policy python-pip

```

and as well, provide the paragraph around line 114 in the file " /var/lib/dpkg/status " .

[INDENT]as around and round we go
[/INDENT]

---

### Post by anna16 on 2016-03-12
And here we go: 
```

k@Anna-PC:~$ LANG=C;apt-cache policy python-pip
python-pip:
  Installed: (none)
  Candidate: 1.5.4-1ubuntu3
  Version table:
     1.5.4-1ubuntu3 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
     1.5.4-1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```

---

### Post by Bashing-om on 2016-03-12
@runrickus; Hey ..

In our efforts to move this forward, take a look at post #38. can you understand where 'python' and ' python-pkg-resources " are having the problem ?

[INDENT][INDENT]stuck big time
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-03-12
Well Yuck is the word for sure!:o
Just for information my output from post #38
```
$ dpkg -l python-pkg-resources
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  python-pkg-res 3.3-1ubuntu2 all          Package Discovery and Resource Ac
```
```
dpkg -l python
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  python         2.7.5-5ubunt amd64        interactive high-level object-ori
```

```
 dpkg -l python3-uno
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  python3-uno    <none>       <none>       (no description available)


```
If I could just recreate... this would make some sense but i can not recreate???
Need time to think through this to move forward and not do anything that will make us go backward...:(

---

### Post by Bashing-om on 2016-03-12
runrickus; Uh Huh ..

'python' appears to be a mess. Let's see if/how libreoffice relates to this.

@anna16 ... what returns:
```

apt-cache depends libreoffice
apt-cache rdepends libreoffice

```

Let's see if we can establish a common denominator between 'python, python-pkg-resources, libreoffice and skype' . What do we need to remove to (RE-)install to the correct versions for a standard 14.04 install ? The difficulty here once these are known is the proper order in which to remove and the order the package manager will dictate in the (RE-)install. Right now, we can not move forward can not move back .. stuck ! We are presently stuck on what python and it's related packages requires.

[INDENT][INDENT]for a simple beginning process
[INDENT][INDENT][INDENT]this sure got deep
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-03-12
@Bashing-om
The second command for query should be this 
```
apt-cache rdepends libreoffice
```
But so far this is bugging the most "**python3-uno**" EDIT: Also this "**python-html5lib**"
I have Libre Office but I show
```
apt-cache policy python3-uno
python3-uno:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```
So very curious..
EDIT: for skype I still show no "python3-uno"
```
me@TheGhost:~$ apt-cache rdepends skype
skype
Reverse Depends:
  skype-bin:i386
  skype-bin:i386
  skype:i386
me@TheGhost:~$ apt-cache depends skype
skype
  Depends: <skype-bin>
    skype-bin:i386
  Conflicts: skype:i386


```
EDIT#3 and when adding the PPA for Libre Office
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libcdr-0.0-0 libcmis-0.4-4 libmspub-0.0-0 liborcus-0.6-0 libvisio-0.0-0
  libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  fonts-opensymbol liblcms2-2 libreoffice-avmedia-backend-gstreamer
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-help-en-us
  libreoffice-impress libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-presentation-minimizer
  libreoffice-style-galaxy libreoffice-style-human libreoffice-writer
  uno-libs3 ure
21 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 84.3 MB of archives.
After this operation, 27.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```
So still very much a mystery...
But with Two heads we should be able to get through this..

---

### Post by Bashing-om on 2016-03-12
@runrickus;

Fixed my error that you pointed out :)

Do not know how all this python plays ... or why python3-uno would be installed;
But:
```

apt-cache show python3-uno

```
may shed a lot of light on our situation ?? - for 1, libreoffice-core is a dependency .

@anna16; Hey.

Let's look at 'dpkg's' control file, see if that is the source of the dpkg error reports.
Post back:
```

cat /var/lib/dpkg/triggers/File

```

As we must get past the dpkg error reports before we can address install/removal processes.

[INDENT][INDENT]one thing is built, upon another, on another
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-03-12
Well I did not show that till after I added the PPA in question(Libre Office)
Now I show from "**cat /var/lib/dpkg/triggers/File**"
```
Source: libreoffice
Version: 1:4.2.3~rc3-0ubuntu2
Replaces: python3-uno (<< 1:4.0.2~rc2), python3.3-uno
Depends: libreoffice-core (= 1:4.2.3~rc3-0ubuntu2), python3:any (>= 3.3.2-2~), libc6 (>= 2.14), libgcc1 (>= 1:4.1.1), libpython3.4 (>= 3.4~b1), libstdc++6 (>= 4.1.1), uno-libs3 (>= 4.1.0~alpha), ure
Conflicts: libreoffice-common (<< 1:3.5.0), python-uno, python3-uno (<< 1:4.0.2~rc2), python3.3-uno
Filename: pool/main/libr/libreoffice/python3-uno_4.2.3~rc3-0ubuntu2_amd64.deb
Size: 120014
MD5sum: 8235aa9a776622e35b5806c8793cfc27
SHA1: 7059f5189ce80f73c9bf30125d68744e25c38351
SHA256: 4e0051680249899126256d4aa22e4969df7207f23a65e806119b7111aebd2382
Description-en: Python-UNO bridge
 The Python-UNO bridge allows use of the standard LibreOffice API
 with the Python scripting language. It additionally allows
 others to develop UNO components in Python, thus Python UNO components
 may be run within the LibreOffice process and can be called from C++
 or the built in StarBasic scripting language.
Description-md5: f4a55d75b607baa049506ff436442fb6
Enhances: libreoffice

```
So slowly we sneak up on this little puzzle..

---

### Post by Bashing-om on 2016-03-12
runrickus; Yeah !

A bit more light on this and another piece in the puzzle . Good job .

Let's wait for Anna to catch up with us . Get updated and away we go again.

[INDENT][INDENT]let there be light
[/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-13
Ok you two. Here we go:

```

k@Anna-PC:~$ LANG=C;apt-cache depends libreoffice
libreoffice
  Depends: fonts-sil-gentium-basic
  Depends: libreoffice-base
  Depends: libreoffice-calc
  Depends: libreoffice-core
  Depends: libreoffice-draw
  Depends: libreoffice-impress
  Depends: libreoffice-math
  Depends: libreoffice-report-builder-bin
  Depends: libreoffice-writer
  Depends: libreoffice-avmedia-backend-gstreamer
  Depends: fonts-dejavu
  Depends: libreoffice-java-common
  Depends: python3-uno
  Suggests: cups-bsd
  Suggests: <hunspell-dictionary>
    hunspell-an
    hunspell-ar
    hunspell-be
    hunspell-br
    hunspell-da
    hunspell-de-at
    hunspell-de-at-frami
    hunspell-de-ch
    hunspell-de-ch-frami
    hunspell-de-de
    hunspell-de-de-frami
    hunspell-en-ca
    hunspell-en-us
    hunspell-eu-es
    hunspell-fr-classical
    hunspell-fr-comprehensive
    hunspell-fr-modern
    hunspell-fr-revised
    hunspell-gl-es
    hunspell-hu
    hunspell-kk
    hunspell-ko
    hunspell-ne
    hunspell-ro
    hunspell-ru
    hunspell-se
    hunspell-sh
    hunspell-sr
    hunspell-sv-se
    hunspell-uz
    hunspell-vi
    myspell-et
    myspell-fr
    myspell-lv
    myspell-pl
    myspell-ru
  Suggests: <hyphen-hyphenation-patterns>
    hyphen-af
    hyphen-ca
    hyphen-de
    hyphen-fr
    hyphen-hu
    hyphen-it
    hyphen-pl
    hyphen-ro
    hyphen-ru
    hyphen-sh
    hyphen-sl
    hyphen-sr
    hyphen-sv
    hyphen-zu
    myspell-et
    myspell-lv
    openoffice.org-hyphenation-lt
 |Suggests: <iceweasel>
    firefox
 |Suggests: firefox
 |Suggests: <icedove>
 |Suggests: thunderbird
 |Suggests: <iceape-browser>
  Suggests: <mozilla-browser>
 |Suggests: imagemagick
    graphicsmagick-imagemagick-compat
  Suggests: graphicsmagick-imagemagick-compat
  Suggests: <libgl1>
    libgl1-mesa-glx
    libgl1-mesa-glx-lts-utopic
    libgl1-mesa-glx-lts-vivid
    libgl1-mesa-glx-lts-wily
  Suggests: <libreoffice-grammarcheck>
    libreoffice-lightproof-en
    libreoffice-lightproof-hu
    libreoffice-lightproof-ru-ru
  Suggests: <libreoffice-help-4.2>
  Suggests: <libreoffice-l10n-4.2>
  Suggests: libsane
  Suggests: libxrender1
  Suggests: <myspell-dictionary>
    myspell-ca
    myspell-de-de-oldspell
    myspell-fr-gut
    myspell-he
    hunspell-kk
    myspell-af
    myspell-bg
    myspell-cs
    myspell-da
    myspell-de-at
    myspell-de-ch
    myspell-de-de
    myspell-en-au
    myspell-en-gb
    myspell-en-us
    myspell-en-za
    myspell-eo
    myspell-es
    myspell-et
    myspell-fa
    myspell-fo
    myspell-fr
    myspell-ga
    myspell-gd
    myspell-gv
    myspell-hr
    myspell-hu
    myspell-hy
    myspell-it
    myspell-ku
    myspell-lt
    myspell-lv
    myspell-nb
    myspell-nl
    myspell-nn
    myspell-pl
    myspell-pt-br
    myspell-pt-pt
    myspell-ru
    myspell-sk
    myspell-sl
    myspell-sw
    myspell-th
    myspell-tl
    myspell-uk
  Suggests: <mythes-thesaurus>
    mythes-ca
    mythes-cs
    mythes-de
    mythes-de-ch
    mythes-en-us
    mythes-fr
    mythes-hu
    mythes-it
    mythes-ne
    mythes-pl
    mythes-ro
    mythes-ru
    mythes-sk
  Suggests: openclipart-libreoffice
  Suggests: pstoedit
  Suggests: unixodbc
  Suggests: gstreamer1.0-plugins-base
  Suggests: gstreamer1.0-plugins-good
  Suggests: gstreamer1.0-plugins-ugly
  Suggests: gstreamer1.0-plugins-bad
  Suggests: <gstreamer1.0-ffmpeg>
 |Suggests: default-jre
 |Suggests: gcj-jre
 |Suggests: openjdk-7-jre
 |Suggests: openjdk-6-jre
 |Suggests: <sun-java5-jre>
 |Suggests: <sun-java6-jre>
 |Suggests: <java5-runtime>
    openjdk-6-jre
    default-jre
    gcj-4.8-jre
    gcj-jre
    openjdk-7-jre
  Suggests: <jre>
  Suggests: libreoffice-officebean
 |Recommends: fonts-liberation
  Recommends: ttf-mscorefonts-installer
  Recommends: libpaper-utils
 |Recommends: libreoffice-gnome
  Recommends: libreoffice-kde

```

and...
```

k@Anna-PC:~$ apt-cache rdepends libreoffice
libreoffice
Reverse Depends:
  python3-uno
  libreoffice-subsequentcheckbase
  libreoffice-kde
  libreoffice-gtk3
  browser-plugin-libreoffice
  python3-uno
  libreoffice-gtk
  libreoffice-gnome
 |ooohg
  owncloud
  openclipart2-libreoffice
  openclipart-libreoffice
 |loook
  libreoffice-zemberek
 |libreoffice-zemberek
  libreoffice-subsequentcheckbase
  libreoffice-kde
  libreoffice-gtk3
  libjodconverter-java
  grcompiler
  browser-plugin-libreoffice
  python3-uno
  myspell-uk
  myspell-pl
  libreoffice-voikko
 |libreoffice-voikko
  libreoffice-gtk
  libreoffice-gnome
  hunspell-sv-se
  hunspell-ru
  hunspell-br
  hunspell-be
k@Anna-PC:~$ cat /var/lib/dpkg/triggers/File
/usr/lib/mime/packages mime-support/noawait:
/usr/share/applications mime-support/noawait:
/etc/init ureadahead:
/etc/init.d ureadahead:
/usr/share/info install-info/noawait:
/usr/lib/x86_64-linux-gnu/gio/modules libglib2.0-0:amd64:
/usr/lib/gio/modules libglib2.0-0:amd64:
/usr/share/glib-2.0/schemas libglib2.0-0:amd64:
/usr/man man-db/noawait:
/usr/share/man man-db/noawait:
/usr/local/man man-db/noawait:
/usr/local/share/man man-db/noawait:
/usr/X11R6/man man-db/noawait:
/opt/man man-db/noawait:
/etc/sgml sgml-base:
/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders libgdk-pixbuf2.0-0:amd64:
/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders libgdk-pixbuf2.0-0:amd64:
/usr/share/fonts fontconfig:
/usr/share/ghostscript/fonts fontconfig:
/usr/share/texmf/fonts fontconfig:
/usr/share/mime/packages shared-mime-info:
/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules libgtk2.0-0:amd64/noawait:
/usr/lib/gtk-2.0/2.10.0/immodules libgtk2.0-0:amd64/noawait:
/usr/share/package-data-downloads update-notifier-common:
/etc/lsb-release plymouth-theme-ubuntu-text:
/etc/ufw/applications.d ufw:
/usr/share/icons/hicolor hicolor-icon-theme:
/usr/share/icons/gnome gnome-icon-theme:
/usr/share/cups/ppd-updaters cups:
/usr/share/applications desktop-file-utils:
/usr/share/doc-base doc-base/noawait:
/usr/share/doc/rarian-compat doc-base/noawait:
/usr/share/gconf/defaults gconf2:
/usr/share/gconf/mandatory gconf2:
/usr/share/gconf/schemas gconf2:
/usr/share/GConf/gsettings gconf2:
/usr/share/applications gnome-menus/noawait:
/usr/share/app-install/desktop software-center:
/usr/share/locale-langpack software-center:
/usr/lib/x86_64-linux-gnu/gtk-3.0/3.0.0/immodules libgtk-3-0:amd64/noawait:
/usr/lib/gtk-3.0/3.0.0/immodules libgtk-3-0:amd64/noawait:
/usr/lib/i386-linux-gnu/gio/modules libglib2.0-0:i386:
/usr/lib/gio/modules libglib2.0-0:i386:
/usr/share/glib-2.0/schemas libglib2.0-0:i386:
/lib/udev/hwdb.d udev/noawait:

```

---

### Post by Bashing-om on 2016-03-13
anna16; Shucks ..

Nother red herring, as I find no faults here either.

Back to the drawing board, see what I can learn and find out.

> 
dpkg: parse error, in file '/var/lib/dpkg/status' near line 90 package 'python-pkg-resources':
 `Depends' field, invalid package name `python:any': character `:' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)

-bk-

Line 90 says:
Depends: python:any (>= 2.7), python:any (<< 2.8)
>> Conflicts: python-setuptools (<< 0.6c8-3)

-bk-

dpkg -l python
dpkg-query: error: file triggers record mentions illegal package name `mime-support/noawait:' (for interest in file `/usr/lib/mime/packages'): illegal package name in specifier 'mime-support/noawait:': character `/' not allowed (only letters, digits and characters `-+._')


Need to find out the cause of these error conditions, and my bash skills just not up to this task .  But that does not stop me from trying to comprehend.

[INDENT][INDENT]as I sharpen my talents
[/INDENT][/INDENT]
---------------------

Maybe another wild goose chase but what is is these files:
```

cat /usr/lib/mime/packages/mime-support
cat /usr/share/applications/mime-support

``` as the "bread crumbs" seem to lead there.
Be aware " /usr/share/applications/mime-support" is not on my system ( no libreoffice installed !)

[INDENT][INDENT]maybe
[/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-16
Here we go:

```

k@Anna-PC:~$ LANG=C;cat /usr/lib/mime/packages/mime-support
application/x-debian-package; /usr/lib/mime/debian-view %s; needsterminal; description=Debian GNU/Linux Package; nametemplate=%s.deb; priority=0
#audio/basic; /usr/lib/mime/playaudio %s; description=Basic uLaw Audio; nametemplate=%s.au; priority=0
k@Anna-PC:~$ cat /usr/share/applications/mime-support
cat: /usr/share/applications/mime-support: No such file or directory

```

---

### Post by Bashing-om on 2016-03-16
anna16; Welp ...

Nope, sorry again to put you through the bother, I see no problem here either.

I just do not have the bash skill to find what it is that bash is looking for and complaining about.
It is back to the drawing board, see what I can learn.

Keep in mind, if and when you loose patience and the frustration level is excessive, only takes 30 minutes to do a clean fresh install - IF you have kept backups of your personal data . However, taking this expedient one learns little from the experience.

[INDENT][INDENT]but,
[INDENT][INDENT][INDENT]there is no quit in my nature
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-16
Hm... Ok... Well, if you want to try further that would be wonderful. :-) But if you say it's to much of an ordeal, I'll see to find someone to set my system up again... ;-) In any case, I'm really greatful for your help!!

---

### Post by Bashing-om on 2016-03-16
anna16; Oh Noo !

I would much prefer to solve this . Everything I look at says the problem is in the status file, but I see no error in it unless ,maybe, it is in the acceptable range of python . In respect to "  python-setuptools (<< 0.6c8-3) ??? 
But I honestly do not know; as All that says is "strictly earlier" than version 0.6c8-3" Ouch ! Where did that old version come into play from ? As the current version is :
> 
sysop@1404mini:~$ apt list python-setuptools
Listing... Done
python-setuptools/trusty-updates 3.3-1ubuntu2 all
sysop@1404mini:~$ 

But only as a conflict conditional .

Now I must seriously question if I have been barking up the wrong tree ( American expression of a hunting dog). I will consider making an edit to reflect a later version for python-setuptools, AND how that edit effects other packages. Maybe best though to see if the package manager will fix this for us. Somehow, someway ,


Still stuck, after all this time.

[INDENT][INDENT][INDENT]looking for a way forward
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-03-17
anna16; Morning .....


AND back on this ... update:

I have 14.04.4 installed and updated ... and this from my install:
```

Package: python-pkg-resources
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 182
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: python-setuptools
Version: 3.3-1ubuntu2
Provides: python2.7-setuptools
Depends: python:any (>= 2.7), python:any (<< 2.8)
Suggests: python-distribute, python-distribute-doc
Conflicts: python-setuptools (<< 0.6c8-3)
<snip>
Python-Version: 2.7

```
Blows my theory away . As my install also has " Conflicts: python-setuptools (<< 0.6c8-3) " I see no difference in your paragraph than that of mine. So the question again is why is the package manager complaining about :
> 
Line 90 says:
Depends: python:any (>= 2.7), python:any (<< 2.8)
>> Conflicts: python-setuptools (<< 0.6c8-3)

I just do not "see" it .
Once again, I am back to seeing what I can learn . I will be back here when I know more.

After all this time
[INDENT][INDENT][INDENT][INDENT]still stuck
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2016-03-19
Were it me, I would first check the apt policy on python-setuptools. If the source is unusual, then remove python-setuptools entirely. It's not essential, and can be easily reinstalled from proper Ubuntu repositories.

```
apt-cache policy python-setuptools
```

---

### Post by anna16 on 2016-03-19
Thanks bashing-om for not giving up!!! You're wonderful!

And thanks ian-weisser for your input! I ran your command and that's what came out... 

Can you make something out of it guys?

```

k@Anna-PC:~$ LANG=C;apt-cache policy python-setuptools
python-setuptools:
  Installed: (none)
  Candidate: 3.3-1ubuntu2
  Version table:
     3.3-1ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     3.3-1ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

---

### Post by Bashing-om on 2016-03-19
anna16; Well !

I had requested Ian to have a look and offer advise.
@ian-weisser; Thanks so much !


That is unexpected output for " python-setuptools " .

What does the package manager tell us with:
```

sudo apt-get remove --purge python-setuptools

```

[INDENT][INDENT]looking for that way forward
[/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-19
Here is the answer:

```

k@Anna-PC:~$ sudo apt-get remove --purge python-setuptools
[sudo] password for k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'python-setuptools' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by ian-weisser on 2016-03-19
'--purge' does not mean 'force', and is probably not helping.

Remove all of the LibreOffice packages from the PPA. One hopes you have already disabled or removed that PPA.
Remove Skype.
You can reinstall those from the Ubuntu repositories once your conflicting packages are located and removed.

---

### Post by Bashing-om on 2016-03-19
anna16; Hey !

I do not see " libreoffice-l10n-en-us" as stock; where did it come from ?

show :
```

apt-cache policy libreoffice-l10n-en-us

```
Let's see if that is one of the PPA packages we need to remove .

[INDENT][INDENT]progress being made
[/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-23
That's what's came out:

```

k@Anna-PC:~$ LANG=C;apt-cache policy libreoffice-l10n-en-us
libreoffice-l10n-en-us:
  Installed: (none)
  Candidate: (none)
  Version table:

```

---

### Post by Bashing-om on 2016-03-23
anna16; K;


3 able minds continue to concentrate on this, find what is the hold up here . 
runrickus is about ready to try that nuclear solution. ( we communicate on a different venue) .

Le's see what results - what the package manger advises:
terminal command:
```

sudo apt remove libreoffice-common

```
see if we can tear libreoffice apart piece by piece and put it back together in the version supported by our software repository.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-29
Hi everyone! Happy Easter! :-)

I was away, so couldn't give you an answer on your last command... But here we go now:

```

k@Anna-PC:~$ LANG=C;sudo apt remove libreoffice-common
[sudo] password for k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libreoffice-common' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2016-03-29
anna16; Well, well well ...

Not at all as expected...
Let's try:
```

sudo apt remove skype
sudo apt remove libreoffice-core

```

see if these point us in a reasonable direction of removal to properly get libreoffice to install.


[INDENT][INDENT]poke poke poke
[INDENT][INDENT][INDENT]'til something gives
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-29
Here's the answer:

```

k@Anna-PC:~$ LANG=C;sudo apt remove skype
[sudo] password for k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
k@Anna-PC:~$ sudo apt remove ibreoffice-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ibreoffice-core

```

---

### Post by QDR06VV9 on 2016-03-29
Hi anna 16 that last command should have read
```
sudo apt remove libreoffice-core
```
it was missing the 'l'

---

### Post by anna16 on 2016-03-29
Oops... Right! ;-) Here we go:

```

k@Anna-PC:~$ LANG=C;sudo apt remove libreoffice-core
[sudo] password for k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-base-core : Depends: libreoffice-core (= 1:4.3.2~rc2-0ubuntu1~trusty2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
                          Recommends: libreoffice-core (> 1:4.2.6.3) but it is not going to be installed or
                                      language-support-translations-en but it is not installable
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
                       Recommends: libreoffice-core (> 1:4.2.6.3) but it is not going to be installed or
                                   language-support-translations-de but it is not installable
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
                          Recommends: libreoffice-core (> 1:4.2.6.3) but it is not going to be installed or
                                      language-support-translations-en but it is not installable
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
                          Recommends: libreoffice-core (> 1:4.2.6.3) but it is not going to be installed or
                                      language-support-translations-en but it is not installable
 libreoffice-math : Depends: libreoffice-core (= 1:4.3.2~rc2-0ubuntu1~trusty2) but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-core (= 1:4.3.2~rc2-0ubuntu1~trusty2) but it is not going to be installed
 mythes-de : Depends: libreoffice-core but it is not going to be installed or
                      openoffice.org-core (>= 3.0~) but it is not installable
 mythes-de-ch : Depends: libreoffice-core but it is not going to be installed or
                         openoffice.org-core (>= 3.0~) but it is not installable
 mythes-en-us : Depends: libreoffice-core but it is not going to be installed or
                         openoffice.org-core (>= 1.9) but it is not installable or
                         language-support-writing-en but it is not installable
 python3-uno : Depends: libreoffice-core (= 1:4.3.2~rc2-0ubuntu1~trusty2) but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

---

### Post by Bashing-om on 2016-03-29
anna16; K,

As we take another step down:
```

sudo apt remove libreoffice-base-core 

```
(( python3-uno : Depends: libreoffice-core  )) raising it ugly head again.

As it is optional to install and is " standard LibreOffice API " let's also try and remove it.
```

sudo apt remove python3-uno

```

[INDENT][INDENT]as around and round we go
[/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-30
Hey bashing-om,
here's the next step:

```

k@Anna-PC:~$ LANG=C;sudo apt remove libreoffice-base-core
[sudo] password for k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-base-core (= 1:4.3.2~rc2-0ubuntu1~trusty2) but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
k@Anna-PC:~$ sudo apt remove python3-uno
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2016-03-30
anna16; Yuk.

Still have not found the right button to push.
Let's see if this gives us any hunts:
```

apt-cache policy "libre-*"

```
To show what is installed, and what might be removable. Maybe we have reached the point of "forcing" the issue !

[INDENT][INDENT]looking for that way forward
[/INDENT][/INDENT]

---

### Post by anna16 on 2016-03-31
Here's the outcome:

```

ages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-gu:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-sdbc-postgresql:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libresiprocate-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
librelp-dev:
  Installed: (none)
  Candidate: 1.2.2-2ubuntu1
  Version table:
     1.2.2-2ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-ga:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libregistry0:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-gd:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-he:
  Installed: (none)
  Candidate: (none)
  Version table:
librest-dev:
  Installed: (none)
  Candidate: 0.7.90-0ubuntu1
  Version table:
     0.7.90-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-hi:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-gl:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreadline-gplv2-dev:
  Installed: (none)
  Candidate: 5.2+dfsg-2
  Version table:
     5.2+dfsg-2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-hr:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-gu:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-hu:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-en-us:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-he:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-id:
  Installed: (none)
  Candidate: (none)
  Version table:
librelaxng-datatype-java:
  Installed: (none)
  Candidate: 1.0+ds1-3
  Version table:
     1.0+ds1-3 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-l10n-hi:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-hr:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-hu:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-is:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-it:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-style-tango:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreact-ocaml:
  Installed: (none)
  Candidate: 0.9.4-3
  Version table:
     0.9.4-3 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
librepository-java-doc:
  Installed: (none)
  Candidate: 1.1.6-2
  Version table:
     1.1.6-2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-help-zh-tw:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-ja:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-id:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-pt-br:
  Installed: (none)
  Candidate: (none)
  Version table:
mozilla-libreoffice:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-in:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-is:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-it:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-wiki-publisher:
  Installed: (none)
  Candidate: 1.1.2+LibO4.2.8-0ubuntu4
  Version table:
     1.1.2+LibO4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     1.1.2+LibO4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-help-kmr-latn:
  Installed: (none)
  Candidate: (none)
  Version table:
libres-ocaml-dev:
  Installed: (none)
  Candidate: 4.0.3-3
  Version table:
     4.0.3-3 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-l10n-ja:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-ka:
  Installed: (none)
  Candidate: (none)
  Version table:
libregina3:
  Installed: (none)
  Candidate: 3.6-2
  Version table:
     3.6-2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libdjvulibre-dev:
  Installed: (none)
  Candidate: 3.5.25.4-3
  Version table:
     3.5.25.4-3 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-kk:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-km:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-ko:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-style-galaxy:
  Installed: 1:4.3.2~rc2-0ubuntu1~trusty2
  Candidate: 1:4.3.2~rc2-0ubuntu1~trusty2
  Version table:
 *** 1:4.3.2~rc2-0ubuntu1~trusty2 0
        100 /var/lib/dpkg/status
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libregina3-dev:
  Installed: (none)
  Candidate: 3.6-2
  Version table:
     3.6-2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libregistry-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-ka:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-kk:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-km:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-ko:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-dtd-officedocument1.0:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-ku:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-lt:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-lv:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-librelogo:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-style-oxygen:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-hyphenation-tr:
  Installed: (none)
  Candidate: (none)
  Version table:
libreturn-value-perl:
  Installed: (none)
  Candidate: 1.666003-1
  Version table:
     1.666003-1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-grammarcheck-mk:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-ml:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-mn:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-lt:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-mr:
  Installed: (none)
  Candidate: (none)
  Version table:
librefdb-sru-perl:
  Installed: (none)
  Candidate: 0.7-2
  Version table:
     0.7-2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-l10n-lv:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-en-za:
  Installed: 1:4.2.6.3-0ubuntu1
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
 *** 1:4.2.6.3-0ubuntu1 0
        100 /var/lib/dpkg/status
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
librenaissance0:
  Installed: (none)
  Candidate: 0.9.0-4build3
  Version table:
     0.9.0-4build3 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
librest-extras-0.7-0:
  Installed: (none)
  Candidate: 0.7.90-0ubuntu1
  Version table:
     0.7.90-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-nb:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-ne:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-mk:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-ml:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-mn:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-nl:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-nn:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-mr:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-nr:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck:
  Installed: (none)
  Candidate: (none)
  Version table:
djvulibre-plugin:
  Installed: (none)
  Candidate: 4.9-4ubuntu3
  Version table:
     4.9-4ubuntu3 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libdjvulibre15:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-writer2latex:
  Installed: (none)
  Candidate: 1.0.2-10ubuntu1
  Version table:
     1.0.2-10ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-l10n-nb:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-ne:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-oc:
  Installed: (none)
  Candidate: (none)
  Version table:
libreflectasm-java-doc:
  Installed: (none)
  Candidate: 1.05-2
  Version table:
     1.05-2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-l10n-nl:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-nn:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-om:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-nr:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-or:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice.org-writer:
  Installed: (none)
  Candidate: (none)
  Version table:
librep9:
  Installed: (none)
  Candidate: 0.90.2-1.4ubuntu3
  Version table:
     0.90.2-1.4ubuntu3 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-spellcheck-tr:
  Installed: (none)
  Candidate: (none)
  Version table:
libdjvulibre21:
  Installed: 3.5.25.4-3
  Candidate: 3.5.25.4-3
  Version table:
 *** 3.5.25.4-3 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
libreoffice-grammarcheck-zh-cn:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-oc:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-nso:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-presenter-console:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-l10n-om:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-pl:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-or:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-pa-in:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-pt:
  Installed: (none)
  Candidate: (none)
  Version table:
librecad:
  Installed: (none)
  Candidate: 2.0.2+nolibs-1
  Version table:
     2.0.2+nolibs-1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-base-drivers:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
librestlet-java:
  Installed: (none)
  Candidate: 2.0.14+repack-0ubuntu1
  Version table:
     2.0.14+repack-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-l10n-pl:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-l10n-pt:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-math:
  Installed: 1:4.3.2~rc2-0ubuntu1~trusty2
  Candidate: 1:4.3.2~rc2-0ubuntu1~trusty2
  Version table:
 *** 1:4.3.2~rc2-0ubuntu1~trusty2 0
        100 /var/lib/dpkg/status
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-style-sifr:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libreoffice-script-provider-bsh:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
librest-doc:
  Installed: (none)
  Candidate: 0.7.90-0ubuntu1
  Version table:
     0.7.90-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-dbg:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-ro:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-ru:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-calc:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu4
  Version table:
     1:4.2.8-0ubuntu4 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-rw:
  Installed: (none)
  Candidate: (none)
  Version table:
unity-scope-asklibreoffice:
  Installed: (none)
  Candidate: (none)
  Version table:
librepository-java-gcj:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-evolution:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-si:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-sk:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-sl:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-ro:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-sr:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-ru:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-ss:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-grammarcheck-st:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-l10n-rw:
  Installed: (none)
  Candidate: 1:4.2.8-0ubuntu1
  Version table:
     1:4.2.8-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libreoffice-grammarcheck-sv:
  Installed: (none)
  Candidate: (none)
  Version table:

```

---

### Post by Bashing-om on 2016-03-31
anna16; Wow !

Curious and curiouser ...Nothing of any significance is installed yet we can not move !
let's see what results now:
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt remove libreoffice-style-galaxy ##should be 1:4.2.8-0ubuntu4##
sudo apt remove libreoffice-l10n-en-za ##should be 1:4.2.8-0ubuntu1##
sudo apt remove libreoffice-math ##should be 1:4.2.8-0ubuntu4##
sudo apt remove libreoffice-help-en-us
sudo apt remove libreoffice-l10n-de 
sudo apt remove libreoffice-l10n-en-gb
sudo apt remove libreoffice-l10n-en-za
sudo apt remove libreoffice-writer
sudo apt update
sudo apt upgrade

```
Note that some of the installed versions are higher, some lower than that of what is in the 14.04 repository. We are working to get the repository version of libreoffice installed. The '##" are for comments and need not be also entered into the command.

Show us the outputs, maybe we can see a way forward.

[INDENT][INDENT]poke poke poke
[INDENT][INDENT][INDENT]'til something gives
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anna16 on 2016-04-02
Aaaaand here we go again:

```

k@Anna-PC:~$ LANG=C;sudo apt-get autoclean
[sudo] password for k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del ubuntu-release-upgrader-gtk 1:0.220.5 [9284 B]
Del libgnutls-openssl27 2.12.23-12ubuntu2.4 [18.3 kB]
Del libreoffice-help-en-us 1:5.0.5~rc2-0ubuntu1~trusty1 [2410 kB]
Del chromium-codecs-ffmpeg-extra 48.0.2564.82-0ubuntu0.14.04.1.1108 [880 kB]
Del libcupscgi1 1.7.2-0ubuntu1.2 [26.2 kB]
Del cups-client 1.7.2-0ubuntu1.2 [195 kB]
Del libreoffice-math 1:4.3.6~rc2-0ubuntu1~trusty1 [406 kB]
Del ubuntu-drivers-common 1:0.2.91.7 [45.4 kB]
Del libsystemd-daemon0 204-5ubuntu20.7 [9738 B]
Del libcurl3-gnutls 7.35.0-1ubuntu2.1 [165 kB]
Del python-aptdaemon 1.1.1-1ubuntu5.1 [66.1 kB]
Del libreoffice-l10n-en-gb 1:5.0.2-0ubuntu1~trusty1 [484 kB]
Del libdbus-1-3 1.6.18-0ubuntu4.2 [132 kB]
Del libcupsmime1 1.7.2-0ubuntu1.2 [12.1 kB]
Del aptdaemon 1.1.1-1ubuntu5.1 [13.5 kB]
Del libreoffice-core 1:4.3.2~rc2-0ubuntu1~trusty2 [31.9 MB]
Del cups-ppdc 1.7.2-0ubuntu1.2 [25.4 kB]
Del libreoffice-common 1:4.3.3~rc2-0ubuntu1~trusty1 [20.1 MB]
Del libreoffice-help-de 1:5.0.5~rc2-0ubuntu1~trusty1 [3063 kB]
Del libreoffice-help-en-gb 1:5.0.5~rc2-0ubuntu1~trusty1 [2390 kB]
Del ca-certificates 20141019ubuntu0.14.04.1 [189 kB]
Del libreoffice-common 1:4.3.2~rc2-0ubuntu1~trusty2 [20.0 MB]
Del libreoffice-math 1:5.1.0~rc3-0ubuntu1~trusty0 [361 kB]
Del fonts-opensymbol 2:102.7+LibO5.0.5~rc2-0ubuntu1~trusty1 [279 kB]
Del systemd-services 204-5ubuntu20.7 [197 kB]
Del libnss3 2:3.17.1-0ubuntu0.14.04.1 [1094 kB]
Del uno-libs3 5.0.5~rc2-0ubuntu1~trusty1 [878 kB]
Del libreoffice-common 1:5.1.0~rc3-0ubuntu1~trusty0 [22.6 MB]
Del python3-uno 1:4.3.3~rc2-0ubuntu1~trusty1 [174 kB]
Del python3-apport 2.14.1-0ubuntu3.5 [74.9 kB]
Del libreoffice-base-core 1:4.3.6~rc2-0ubuntu1~trusty1 [786 kB]
Del libgnutls26 2.12.23-12ubuntu2.4 [393 kB]
Del cups-core-drivers 1.7.2-0ubuntu1.2 [25.7 kB]
Del libreoffice-core 1:4.3.3~rc2-0ubuntu1~trusty1 [31.9 MB]
Del libreoffice-writer 1:5.0.2-0ubuntu1~trusty1 [7637 kB]
Del libcupsppdc1 1.7.2-0ubuntu1.2 [44.0 kB]
Del ure 5.0.2-0ubuntu1~trusty1 [1709 kB]
Del aptdaemon-data 1.1.1-1ubuntu5.1 [162 kB]
Del linux-image-generic 3.13.0.77.83 [2234 B]
Del libreoffice-base-core 1:5.0.2-0ubuntu1~trusty1 [794 kB]
Del cups-bsd 1.7.2-0ubuntu1.2 [26.6 kB]
Del udev 204-5ubuntu20.7 [735 kB]
Del libnspr4 2:4.10.7-0ubuntu0.14.04.1 [111 kB]
Del libreoffice-writer 1:4.3.2~rc2-0ubuntu1~trusty2 [7937 kB]
Del libreoffice-core 1:4.3.6~rc2-0ubuntu1~trusty1 [31.9 MB]
Del python3-uno 1:4.3.2~rc2-0ubuntu1~trusty2 [174 kB]
Del ure 4.3.2~rc2-0ubuntu1~trusty2 [1814 kB]
Del libpam-systemd 204-5ubuntu20.7 [25.5 kB]
Del libreoffice-math 1:5.0.2-0ubuntu1~trusty1 [437 kB]
Del libuuid1 2.20.1-5.1ubuntu20.2 [10.9 kB]
Del python-aptdaemon.gtk3widgets 1.1.1-1ubuntu5.1 [13.7 kB]
Del openssl 1.0.1f-1ubuntu2.16 [488 kB]
Del libreoffice-l10n-de 1:5.1.0~rc3-0ubuntu1~trusty0 [504 kB]
Del libnss3-nssdb 2:3.17.1-0ubuntu0.14.04.1 [10.6 kB]
Del gir1.2-webkit-3.0 2.4.4-1~ubuntu1 [60.1 kB]
Del libreoffice-l10n-en-za 1:5.0.5~rc2-0ubuntu1~trusty1 [406 kB]
Del libexo-1-0 0.10.2-3ubuntu1.14.04.1 [308 kB]
Del libwebkitgtk-3.0-0 2.4.4-1~ubuntu1 [6491 kB]
Del python3-uno 1:4.3.4-0ubuntu1~trusty1 [174 kB]
Del python3-uno 1:5.0.5~rc2-0ubuntu1~trusty1 [175 kB]
Del ure 5.1.0~rc3-0ubuntu1~trusty0 [1712 kB]
Del libreoffice-writer 1:4.3.6~rc2-0ubuntu1~trusty1 [7952 kB]
Del ubuntu-release-upgrader-core 1:0.220.5 [23.1 kB]
Del libreoffice-style-galaxy 1:5.1.0~rc3-0ubuntu1~trusty0 [1518 kB]
Del libreoffice-writer 1:4.3.4-0ubuntu1~trusty1 [7917 kB]
Del cups-server-common 1.7.2-0ubuntu1.2 [513 kB]
Del uno-libs3 5.1.0~rc3-0ubuntu1~trusty0 [870 kB]
Del gcc-4.9-base 4.9.1-0ubuntu1 [14.8 kB]
Del libreoffice-core 1:4.3.4-0ubuntu1~trusty1 [31.8 MB]
Del libwebkitgtk-3.0-common 2.4.4-1~ubuntu1 [107 kB]
Del ure 5.0.5~rc2-0ubuntu1~trusty1 [1714 kB]
Del python3-aptdaemon 1.1.1-1ubuntu5.1 [66.7 kB]
Del libnspr4-0d 2:4.10.7-0ubuntu0.14.04.1 [6574 B]
Del libreoffice-base-core 1:4.3.3~rc2-0ubuntu1~trusty1 [785 kB]
Del linux-headers-generic 3.13.0.77.83 [2220 B]
Del chromium-codecs-ffmpeg-extra 37.0.2062.120-0ubuntu0.14.04.1~pkg1049 [831 kB]
Del cups-daemon 1.7.2-0ubuntu1.2 [268 kB]
Del libreoffice-l10n-de 1:5.0.2-0ubuntu1~trusty1 [496 kB]
Del apport-gtk 2.14.1-0ubuntu3.5 [9504 B]
Del python3-uno 1:4.3.6~rc2-0ubuntu1~trusty1 [175 kB]
Del libreoffice-common 1:5.0.2-0ubuntu1~trusty1 [22.5 MB]
Del libwebkitgtk-1.0-0 2.4.4-1~ubuntu1 [6489 kB]
Del libreoffice-math 1:4.3.2~rc2-0ubuntu1~trusty2 [405 kB]
Del python3-uno 1:5.0.2-0ubuntu1~trusty1 [175 kB]
Del util-linux 2.20.1-5.1ubuntu20.2 [458 kB]
Del uuid-runtime 2.20.1-5.1ubuntu20.2 [12.2 kB]
Del libreoffice-style-galaxy 1:5.0.5~rc2-0ubuntu1~trusty1 [1555 kB]
Del libwebkitgtk-1.0-common 2.4.4-1~ubuntu1 [107 kB]
Del libreoffice-writer 1:4.3.3~rc2-0ubuntu1~trusty1 [7939 kB]
Del libcurl3 7.35.0-1ubuntu2.1 [173 kB]
Del libreoffice-style-galaxy 1:5.0.2-0ubuntu1~trusty1 [1557 kB]
Del libreoffice-writer 1:5.0.5~rc2-0ubuntu1~trusty1 [7662 kB]
Del gir1.2-javascriptcoregtk-3.0 2.4.4-1~ubuntu1 [12.1 kB]
Del libblkid1 2.20.1-5.1ubuntu20.2 [62.5 kB]
Del linux-libc-dev 3.13.0-77.121 [776 kB]
Del linux-generic 3.13.0.77.83 [1784 B]
Del uno-libs3 5.0.2-0ubuntu1~trusty1 [877 kB]
Del libreoffice-l10n-en-za 1:5.0.2-0ubuntu1~trusty1 [404 kB]
Del libssl1.0.0 1.0.1f-1ubuntu2.16 [827 kB]
Del libreoffice-math 1:4.3.4-0ubuntu1~trusty1 [406 kB]
Del bsdutils 1:2.20.1-5.1ubuntu20.2 [33.8 kB]
Del irqbalance 1.0.6-2ubuntu0.14.04.1 [30.6 kB]
Del libreoffice-core 1:5.0.2-0ubuntu1~trusty1 [33.0 MB]
Del libreoffice-l10n-en-gb 1:5.0.5~rc2-0ubuntu1~trusty1 [486 kB]
Del libreoffice-core 1:5.1.0~rc3-0ubuntu1~trusty0 [31.7 MB]
Del libreoffice-base-core 1:5.1.0~rc3-0ubuntu1~trusty0 [713 kB]
Del libreoffice-core 1:5.0.5~rc2-0ubuntu1~trusty1 [33.0 MB]
Del dbus 1.6.18-0ubuntu4.2 [230 kB]
Del libreoffice-base-core 1:5.0.5~rc2-0ubuntu1~trusty1 [794 kB]
Del libjavascriptcoregtk-3.0-0 2.4.4-1~ubuntu1 [1820 kB]
Del dbus-x11 1.6.18-0ubuntu4.2 [19.2 kB]
Del libexo-helpers 0.10.2-3ubuntu1.14.04.1 [16.1 kB]
Del libsystemd-login0 204-5ubuntu20.7 [26.8 kB]
Del mount 2.20.1-5.1ubuntu20.2 [115 kB]
Del python3-aptdaemon.gtk3widgets 1.1.1-1ubuntu5.1 [13.8 kB]
Del libnss3-1d 2:3.17.1-0ubuntu0.14.04.1 [9308 B]
Del gir1.2-gudev-1.0 1:204-5ubuntu20.7 [5486 B]
Del libexo-common 0.10.2-3ubuntu1.14.04.1 [15.8 kB]
Del libreoffice-writer 1:5.1.0~rc3-0ubuntu1~trusty0 [7554 kB]
Del libreoffice-l10n-de 1:5.0.5~rc2-0ubuntu1~trusty1 [498 kB]
Del libreoffice-l10n-en-gb 1:5.1.0~rc3-0ubuntu1~trusty0 [492 kB]
Del libreoffice-base-core 1:4.3.2~rc2-0ubuntu1~trusty2 [786 kB]
Del linux-firmware 1.127.7 [20.4 MB]
Del libcupsimage2 1.7.2-0ubuntu1.2 [15.3 kB]
Del libjavascriptcoregtk-1.0-0 2.4.4-1~ubuntu1 [1820 kB]
Del uno-libs3 4.3.2~rc2-0ubuntu1~trusty2 [779 kB]
Del file 1:5.14-2ubuntu3.2 [18.8 kB]
Del libmount1 2.20.1-5.1ubuntu20.2 [60.2 kB]
Del libreoffice-common 1:4.3.4-0ubuntu1~trusty1 [20.2 MB]
Del libcups2 1.7.2-0ubuntu1.2 [179 kB]
Del oxideqt-codecs-extra 1.12.6-0ubuntu0.14.04.1 [885 kB]
Del libreoffice-common 1:4.3.6~rc2-0ubuntu1~trusty1 [20.2 MB]
Del python3-distupgrade 1:0.220.5 [104 kB]
Del libreoffice-common 1:5.0.5~rc2-0ubuntu1~trusty1 [22.4 MB]
Del exo-utils 0.10.2-3ubuntu1.14.04.1 [42.3 kB]
Del libreoffice-l10n-en-za 1:5.1.0~rc3-0ubuntu1~trusty0 [411 kB]
Del libudev1 204-5ubuntu20.7 [33.3 kB]
Del libreoffice-math 1:4.3.3~rc2-0ubuntu1~trusty1 [405 kB]
Del liblcms2-2 2.6-3ubuntu1~trusty1 [134 kB]
Del libreoffice-style-galaxy 1:4.3.2~rc2-0ubuntu1~trusty2 [1443 kB]
Del libmagic1 1:5.14-2ubuntu3.2 [184 kB]
Del libreoffice-math 1:5.0.5~rc2-0ubuntu1~trusty1 [439 kB]
Del xserver-xorg-core 2:1.15.1-0ubuntu2.1 [1228 kB]
Del cups-common 1.7.2-0ubuntu1.2 [160 kB]
Del python3-aptdaemon.pkcompat 1.1.1-1ubuntu5.1 [32.4 kB]
Del fonts-droid 1:4.3-3ubuntu1.1 [3040 kB]
Del libgudev-1.0-0 1:204-5ubuntu20.7 [14.1 kB]
Del cups 1.7.2-0ubuntu1.2 [185 kB]
Del python3-problem-report 2.14.1-0ubuntu3.5 [9098 B]
Del apport 2.14.1-0ubuntu3.5 [179 kB]
Del libreoffice-base-core 1:4.3.4-0ubuntu1~trusty1 [786 kB]
Del xserver-common 2:1.15.1-0ubuntu2.1 [27.5 kB]
Del cpio 2.11+dfsg-1ubuntu1.1 [73.3 kB]
Del libgcc1 1:4.9.1-0ubuntu1 [39.2 kB]

k@Anna-PC:~$ sudo apt-get clean
k@Anna-PC:~$ 

k@Anna-PC:~$ sudo apt remove libreoffice-style-galaxy ##should be 1:4.2.8-0ubuntu4##
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

k@Anna-PC:~$ sudo apt remove libreoffice-l10n-en-za ##should be 1:4.2.8-0ubuntu1##
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

k@Anna-PC:~$ sudo apt remove libreoffice-math ##should be 1:4.2.8-0ubuntu4##
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

k@Anna-PC:~$ sudo apt remove libreoffice-help-en-us
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

k@Anna-PC:~$ sudo apt remove libreoffice-l10n-en-gb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-en-gb : Depends: libreoffice-l10n-en-gb but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

k@Anna-PC:~$ sudo apt remove libreoffice-l10n-en-za
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

k@Anna-PC:~$ sudo apt remove libreoffice-writer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not going to be installed
 libreoffice-help-de : Depends: libreoffice-writer but it is not going to be installed or
                                language-support-translations-de but it is not installable
 libreoffice-help-en-gb : Depends: libreoffice-writer but it is not going to be installed or
                                   language-support-translations-en but it is not installable
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
                          Depends: libreoffice-writer but it is not going to be installed or
                                   language-support-translations-en but it is not installable
 libreoffice-l10n-de : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

k@Anna-PC:~$ sudo apt update
Ign http://de.archive.ubuntu.com trusty InRelease
Get:1 http://de.archive.ubuntu.com trusty-updates InRelease [65.9 kB]
Ign http://archive.canonical.com trusty InRelease                              
Get:2 http://de.archive.ubuntu.com trusty-security InRelease [65.9 kB]     
Get:3 http://archive.canonical.com trusty Release.gpg [933 B]                  
Hit http://de.archive.ubuntu.com trusty Release.gpg                        
Get:4 http://de.archive.ubuntu.com trusty-updates/multiverse Sources [5946 B]
Get:5 http://archive.canonical.com trusty Release [9359 B]            
Get:6 http://de.archive.ubuntu.com trusty-updates/restricted Sources [5352 B]
Get:7 http://de.archive.ubuntu.com trusty-updates/main Sources [271 kB]
Get:8 http://archive.canonical.com trusty/partner Sources [10.1 kB]
Get:9 http://archive.canonical.com trusty/partner amd64 Packages [5620 B]     
Get:10 http://archive.canonical.com trusty/partner Translation-en [4593 B]    
Get:11 http://de.archive.ubuntu.com trusty-updates/universe Sources [151 kB]
Get:12 http://de.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:13 http://de.archive.ubuntu.com trusty-updates/main amd64 Packages [747 kB]
Get:14 http://de.archive.ubuntu.com trusty-updates/universe amd64 Packages [356 kB]
Get:15 http://de.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:16 http://de.archive.ubuntu.com trusty-updates/main Translation-en [373 kB]
Get:17 http://de.archive.ubuntu.com trusty-updates/multiverse Translation-en [7227 B]
Get:18 http://de.archive.ubuntu.com trusty-updates/restricted Translation-en [3699 B]
Get:19 http://de.archive.ubuntu.com trusty-updates/universe Translation-en [186 kB]
Get:20 http://de.archive.ubuntu.com trusty-security/multiverse Sources [2750 B]
Get:21 http://de.archive.ubuntu.com trusty-security/restricted Sources [4035 B]
Get:22 http://de.archive.ubuntu.com trusty-security/main Sources [110 kB]
Get:23 http://de.archive.ubuntu.com trusty-security/universe Sources [34.7 kB]
Get:24 http://de.archive.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:25 http://de.archive.ubuntu.com trusty-security/main amd64 Packages [449 kB]
Get:26 http://de.archive.ubuntu.com trusty-security/universe amd64 Packages [126 kB]
Get:27 http://de.archive.ubuntu.com trusty-security/multiverse amd64 Packages [4991 B]
Get:28 http://de.archive.ubuntu.com trusty-security/main Translation-en [245 kB]
Get:29 http://de.archive.ubuntu.com trusty-security/multiverse Translation-en [2570 B]
Get:30 http://de.archive.ubuntu.com trusty-security/restricted Translation-en [3206 B]
Get:31 http://de.archive.ubuntu.com trusty-security/universe Translation-en [74.3 kB]
Hit http://de.archive.ubuntu.com trusty Release                                
Hit http://de.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://de.archive.ubuntu.com trusty/restricted Sources                     
Hit http://de.archive.ubuntu.com trusty/main Sources                           
Hit http://de.archive.ubuntu.com trusty/universe Sources                       
Hit http://de.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://de.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://de.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://de.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://de.archive.ubuntu.com trusty/main Translation-en                    
Hit http://de.archive.ubuntu.com trusty/main Translation-de                    
Hit http://de.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://de.archive.ubuntu.com trusty/multiverse Translation-de              
Hit http://de.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://de.archive.ubuntu.com trusty/restricted Translation-de              
Hit http://de.archive.ubuntu.com trusty/universe Translation-en                
Hit http://de.archive.ubuntu.com trusty/universe Translation-de                
Fetched 3369 kB in 7s (468 kB/s)                                               
Reading package lists... Done

k@Anna-PC:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try using -f.

```

---

### Post by ian-weisser on 2016-04-02
Try:
```
sudo apt remove libreoffice* skype
sudo apt upgrade
```

---

### Post by anna16 on 2016-04-04
Thanks Ian!

Here's my terminals response:

```

k@Anna-PC:~$ LANG=C;sudo apt remove libreoffice* skype
[sudo] password for k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libreoffice-grammarcheck-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-subsequentcheckbase' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-4.1' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-4.2' for regex 'libreoffice*'
Note, selecting 'libreoffice-pdfimport' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-base-core' for regex 'libreoffice*'
Note, selecting 'libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-emailmerge' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-officebean' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-crystal' for regex 'libreoffice*'
Note, selecting 'openclipart2-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-dmaths' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-binfilter' for regex 'libreoffice*'
Note, selecting 'libreoffice-report-builder' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-as' for regex 'libreoffice*'
Note, selecting 'openclipart-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-be' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-impress' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-avmedia-backend-gstreamer' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-base' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.5' for regex 'libreoffice*'
Note, selecting 'libreoffice-lightproof-ru-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.6' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2xhtml' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gd' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-avmedia-backend' for regex 'libreoffice*'
Note, selecting 'libreoffice-draw' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hi' for regex 'libreoffice*'
Note, selecting 'browser-plugin-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-reportdesigner' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-kmr-latn' for regex 'libreoffice*'
Note, selecting 'libreoffice-accessodf' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-hicontrast' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-bundled' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-kk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-sdbc-firebird' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-default' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-gcj' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-mobiledev' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-presentation-minimizer' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice.org-calc' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-kmr-latn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-rw' for regex 'libreoffice*'
Note, selecting 'zotero-libreoffice-integration' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-report-builder-bin' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nso' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-andromeda' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-kab' for regex 'libreoffice*'
Note, selecting 'libreoffice-script-provider-python' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-lightproof-en' for regex 'libreoffice*'
Note, selecting 'libreoffice-hyphenation-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-ogltrans' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-voikko' for regex 'libreoffice*'
Note, selecting 'libreoffice-kde' for regex 'libreoffice*'
Note, selecting 'libreoffice-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-nlpsolver' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-lightproof-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-unbundled' for regex 'libreoffice*'
Note, selecting 'libreoffice-zemberek' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-4.1' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-4.2' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-be' for regex 'libreoffice*'
Note, selecting 'libreoffice-style' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-be' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-templates' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev-doc' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk3' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-sdbc-hsqldb' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-java-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-mysql-connector' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nso' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-gd' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-script-provider-js' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-sdbc-postgresql' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gd' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-tango' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-pt-br' for regex 'libreoffice*'
Note, selecting 'mozilla-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-wiki-publisher' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-kmr-latn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-kk' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-galaxy' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-kk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-dtd-officedocument1.0' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-librelogo' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-oxygen' for regex 'libreoffice*'
Note, selecting 'libreoffice-hyphenation-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2latex' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-or' for regex 'libreoffice*'
Note, selecting 'libreoffice.org-writer' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nso' for regex 'libreoffice*'
Note, selecting 'libreoffice-presenter-console' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-base-drivers' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-math' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-sifr' for regex 'libreoffice*'
Note, selecting 'libreoffice-script-provider-bsh' for regex 'libreoffice*'
Note, selecting 'libreoffice-dbg' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-calc' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-rw' for regex 'libreoffice*'
Note, selecting 'unity-scope-asklibreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-evolution' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-avmedia-backend-gstreamer' instead of 'libreoffice-avmedia-backend'
Package 'libreoffice-gcj' is not installed, so not removed
Package 'libreoffice-filter-mobiledev' is not installed, so not removed
Package 'libreoffice-l10n-3.5' is not installed, so not removed
Package 'libreoffice-l10n-3.6' is not installed, so not removed
Package 'libreoffice-style-andromeda' is not installed, so not removed
Package 'zotero-libreoffice-integration' is not installed, so not removed
Note, selecting 'libreoffice-common' instead of 'libreoffice-l10n-en-us'
Package 'libreoffice-filter-binfilter' is not installed, so not removed
Package 'libreoffice-unbundled' is not installed, so not removed
Package 'libreoffice-evolution' is not installed, so not removed
Package 'libreoffice-kab' is not installed, so not removed
Note, selecting 'browser-plugin-libreoffice' instead of 'mozilla-libreoffice'
Note, selecting 'libreoffice-core' instead of 'libreoffice-bundled'
Note, selecting 'openoffice.org-dtd-officedocument1.0' instead of 'libreoffice-dtd-officedocument1.0'
Note, selecting 'libreoffice-gnome' instead of 'libreoffice-gtk-gnome'
Package 'libreoffice-grammarcheck-af' is not installed, so not removed
Package 'libreoffice-help-af' is not installed, so not removed
Package 'libreoffice-grammarcheck-ar' is not installed, so not removed
Package 'libreoffice-help-ar' is not installed, so not removed
Package 'libreoffice-grammarcheck-as' is not installed, so not removed
Package 'libreoffice-help-as' is not installed, so not removed
Package 'libreoffice-grammarcheck-ast' is not installed, so not removed
Package 'libreoffice-help-ast' is not installed, so not removed
Package 'libreoffice-grammarcheck-be' is not installed, so not removed
Package 'libreoffice-help-be' is not installed, so not removed
Package 'libreoffice-grammarcheck-bg' is not installed, so not removed
Package 'libreoffice-help-bg' is not installed, so not removed
Package 'libreoffice-grammarcheck-bn' is not installed, so not removed
Package 'libreoffice-help-bn' is not installed, so not removed
Package 'libreoffice-grammarcheck-br' is not installed, so not removed
Package 'libreoffice-help-br' is not installed, so not removed
Package 'libreoffice-grammarcheck-bs' is not installed, so not removed
Package 'libreoffice-help-bs' is not installed, so not removed
Package 'libreoffice-grammarcheck-ca' is not installed, so not removed
Package 'libreoffice-grammarcheck-cs' is not installed, so not removed
Package 'libreoffice-grammarcheck-cy' is not installed, so not removed
Package 'libreoffice-help-cy' is not installed, so not removed
Package 'libreoffice-grammarcheck-da' is not installed, so not removed
Package 'libreoffice-grammarcheck-de' is not installed, so not removed
Package 'libreoffice-grammarcheck-dz' is not installed, so not removed
Package 'libreoffice-grammarcheck-el' is not installed, so not removed
Note, selecting 'libreoffice-lightproof-en' instead of 'libreoffice-grammarcheck-en-gb'
Note, selecting 'libreoffice-lightproof-en' instead of 'libreoffice-grammarcheck-en-za'
Package 'libreoffice-help-en-za' is not installed, so not removed
Package 'libreoffice-grammarcheck-eo' is not installed, so not removed
Package 'libreoffice-help-eo' is not installed, so not removed
Package 'libreoffice-grammarcheck-es' is not installed, so not removed
Package 'libreoffice-grammarcheck-et' is not installed, so not removed
Package 'libreoffice-grammarcheck-eu' is not installed, so not removed
Package 'libreoffice-grammarcheck-fa' is not installed, so not removed
Package 'libreoffice-help-fa' is not installed, so not removed
Package 'libreoffice-grammarcheck-fi' is not installed, so not removed
Package 'libreoffice-grammarcheck-fr' is not installed, so not removed
Package 'libreoffice-grammarcheck-ga' is not installed, so not removed
Package 'libreoffice-help-ga' is not installed, so not removed
Package 'libreoffice-grammarcheck-gd' is not installed, so not removed
Package 'libreoffice-help-gd' is not installed, so not removed
Package 'libreoffice-grammarcheck-gl' is not installed, so not removed
Package 'libreoffice-grammarcheck-gu' is not installed, so not removed
Package 'libreoffice-help-gu' is not installed, so not removed
Package 'libreoffice-grammarcheck-he' is not installed, so not removed
Package 'libreoffice-help-he' is not installed, so not removed
Package 'libreoffice-grammarcheck-hi' is not installed, so not removed
Package 'libreoffice-grammarcheck-hr' is not installed, so not removed
Package 'libreoffice-help-hr' is not installed, so not removed
Note, selecting 'libreoffice-lightproof-hu' instead of 'libreoffice-grammarcheck-hu'
Package 'libreoffice-grammarcheck-id' is not installed, so not removed
Package 'libreoffice-help-id' is not installed, so not removed
Package 'libreoffice-grammarcheck-is' is not installed, so not removed
Package 'libreoffice-help-is' is not installed, so not removed
Package 'libreoffice-grammarcheck-it' is not installed, so not removed
Package 'libreoffice-grammarcheck-ja' is not installed, so not removed
Package 'libreoffice-grammarcheck-ka' is not installed, so not removed
Package 'libreoffice-help-ka' is not installed, so not removed
Package 'libreoffice-grammarcheck-kk' is not installed, so not removed
Package 'libreoffice-help-kk' is not installed, so not removed
Package 'libreoffice-grammarcheck-km' is not installed, so not removed
Package 'libreoffice-grammarcheck-kmr-latn' is not installed, so not removed
Package 'libreoffice-help-kmr-latn' is not installed, so not removed
Package 'libreoffice-grammarcheck-ko' is not installed, so not removed
Package 'libreoffice-grammarcheck-lt' is not installed, so not removed
Package 'libreoffice-help-lt' is not installed, so not removed
Package 'libreoffice-grammarcheck-lv' is not installed, so not removed
Package 'libreoffice-help-lv' is not installed, so not removed
Package 'libreoffice-grammarcheck-mk' is not installed, so not removed
Package 'libreoffice-help-mk' is not installed, so not removed
Package 'libreoffice-grammarcheck-ml' is not installed, so not removed
Package 'libreoffice-help-ml' is not installed, so not removed
Package 'libreoffice-grammarcheck-mn' is not installed, so not removed
Package 'libreoffice-help-mn' is not installed, so not removed
Package 'libreoffice-grammarcheck-mr' is not installed, so not removed
Package 'libreoffice-help-mr' is not installed, so not removed
Package 'libreoffice-grammarcheck-nb' is not installed, so not removed
Package 'libreoffice-help-nb' is not installed, so not removed
Package 'libreoffice-grammarcheck-ne' is not installed, so not removed
Package 'libreoffice-help-ne' is not installed, so not removed
Package 'libreoffice-grammarcheck-nl' is not installed, so not removed
Package 'libreoffice-grammarcheck-nn' is not installed, so not removed
Package 'libreoffice-help-nn' is not installed, so not removed
Package 'libreoffice-grammarcheck-nr' is not installed, so not removed
Package 'libreoffice-help-nr' is not installed, so not removed
Package 'libreoffice-grammarcheck-nso' is not installed, so not removed
Package 'libreoffice-help-nso' is not installed, so not removed
Package 'libreoffice-grammarcheck-oc' is not installed, so not removed
Package 'libreoffice-help-oc' is not installed, so not removed
Package 'libreoffice-grammarcheck-om' is not installed, so not removed
Package 'libreoffice-grammarcheck-or' is not installed, so not removed
Package 'libreoffice-help-or' is not installed, so not removed
Package 'libreoffice-grammarcheck-pa-in' is not installed, so not removed
Package 'libreoffice-help-pa-in' is not installed, so not removed
Package 'libreoffice-grammarcheck-pl' is not installed, so not removed
Package 'libreoffice-grammarcheck-pt' is not installed, so not removed
Package 'libreoffice-grammarcheck-pt-br' is not installed, so not removed
Package 'libreoffice-grammarcheck-ro' is not installed, so not removed
Package 'libreoffice-help-ro' is not installed, so not removed
Note, selecting 'libreoffice-lightproof-ru-ru' instead of 'libreoffice-grammarcheck-ru'
Package 'libreoffice-grammarcheck-rw' is not installed, so not removed
Package 'libreoffice-help-rw' is not installed, so not removed
Package 'libreoffice-grammarcheck-si' is not installed, so not removed
Package 'libreoffice-help-si' is not installed, so not removed
Package 'libreoffice-grammarcheck-sk' is not installed, so not removed
Package 'libreoffice-grammarcheck-sl' is not installed, so not removed
Package 'libreoffice-grammarcheck-sr' is not installed, so not removed
Package 'libreoffice-help-sr' is not installed, so not removed
Package 'libreoffice-grammarcheck-ss' is not installed, so not removed
Package 'libreoffice-help-ss' is not installed, so not removed
Package 'libreoffice-grammarcheck-st' is not installed, so not removed
Package 'libreoffice-help-st' is not installed, so not removed
Package 'libreoffice-grammarcheck-sv' is not installed, so not removed
Package 'libreoffice-grammarcheck-ta' is not installed, so not removed
Package 'libreoffice-help-ta' is not installed, so not removed
Package 'libreoffice-grammarcheck-te' is not installed, so not removed
Package 'libreoffice-help-te' is not installed, so not removed
Package 'libreoffice-grammarcheck-tg' is not installed, so not removed
Package 'libreoffice-help-tg' is not installed, so not removed
Package 'libreoffice-grammarcheck-th' is not installed, so not removed
Package 'libreoffice-help-th' is not installed, so not removed
Package 'libreoffice-grammarcheck-tn' is not installed, so not removed
Package 'libreoffice-help-tn' is not installed, so not removed
Package 'libreoffice-grammarcheck-tr' is not installed, so not removed
Package 'libreoffice-grammarcheck-ts' is not installed, so not removed
Package 'libreoffice-help-ts' is not installed, so not removed
Package 'libreoffice-grammarcheck-ug' is not installed, so not removed
Package 'libreoffice-help-ug' is not installed, so not removed
Package 'libreoffice-grammarcheck-uk' is not installed, so not removed
Package 'libreoffice-help-uk' is not installed, so not removed
Package 'libreoffice-grammarcheck-uz' is not installed, so not removed
Package 'libreoffice-help-uz' is not installed, so not removed
Package 'libreoffice-grammarcheck-ve' is not installed, so not removed
Package 'libreoffice-help-ve' is not installed, so not removed
Package 'libreoffice-grammarcheck-vi' is not installed, so not removed
Package 'libreoffice-grammarcheck-xh' is not installed, so not removed
Package 'libreoffice-help-xh' is not installed, so not removed
Package 'libreoffice-grammarcheck-zh-cn' is not installed, so not removed
Package 'libreoffice-grammarcheck-zh-tw' is not installed, so not removed
Package 'libreoffice-grammarcheck-zu' is not installed, so not removed
Package 'libreoffice-help-zu' is not installed, so not removed
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-hyphenation-fi'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-spellcheck-fi'
Note, selecting 'unity-scope-home' instead of 'unity-scope-asklibreoffice'
Package 'libreoffice.org-calc' is not installed, so not removed
Package 'libreoffice.org-writer' is not installed, so not removed
Note, selecting 'libreoffice-lightproof-en' instead of 'libreoffice-grammarcheck-en-us'
Note, selecting 'libreoffice-report-builder' instead of 'libreoffice-reportdesigner'
Note, selecting 'libreoffice-zemberek' instead of 'libreoffice-hyphenation-tr'
Note, selecting 'libreoffice-zemberek' instead of 'libreoffice-spellcheck-tr'
Package 'libreoffice-help-4.2' is not installed, so not removed
Package 'libreoffice-l10n-4.2' is not installed, so not removed
Package 'libreoffice-nlpsolver' is not installed, so not removed
Package 'libreoffice-voikko' is not installed, so not removed
Package 'libreoffice-accessodf' is not installed, so not removed
Package 'libreoffice-dmaths' is not installed, so not removed
Package 'libreoffice-lightproof-en' is not installed, so not removed
Package 'libreoffice-lightproof-hu' is not installed, so not removed
Package 'libreoffice-lightproof-ru-ru' is not installed, so not removed
Package 'libreoffice-templates' is not installed, so not removed
Package 'libreoffice-writer2latex' is not installed, so not removed
Package 'libreoffice-writer2xhtml' is not installed, so not removed
Package 'libreoffice-zemberek' is not installed, so not removed
Package 'openclipart-libreoffice' is not installed, so not removed
Package 'openclipart2-libreoffice' is not installed, so not removed
Package 'libreoffice-avmedia-backend-gstreamer' is not installed, so not removed
Package 'libreoffice-base' is not installed, so not removed
Package 'libreoffice-base-drivers' is not installed, so not removed
Package 'libreoffice-calc' is not installed, so not removed
Package 'libreoffice-common' is not installed, so not removed
Package 'libreoffice-dbg' is not installed, so not removed
Package 'libreoffice-dev' is not installed, so not removed
Package 'libreoffice-dev-doc' is not installed, so not removed
Package 'libreoffice-draw' is not installed, so not removed
Package 'libreoffice-gnome' is not installed, so not removed
Package 'libreoffice-gtk' is not installed, so not removed
Package 'libreoffice-help-ca' is not installed, so not removed
Package 'libreoffice-help-cs' is not installed, so not removed
Package 'libreoffice-help-da' is not installed, so not removed
Package 'libreoffice-help-dz' is not installed, so not removed
Package 'libreoffice-help-el' is not installed, so not removed
Package 'libreoffice-help-es' is not installed, so not removed
Package 'libreoffice-help-et' is not installed, so not removed
Package 'libreoffice-help-eu' is not installed, so not removed
Package 'libreoffice-help-fi' is not installed, so not removed
Package 'libreoffice-help-fr' is not installed, so not removed
Package 'libreoffice-help-gl' is not installed, so not removed
Package 'libreoffice-help-hi' is not installed, so not removed
Package 'libreoffice-help-hu' is not installed, so not removed
Package 'libreoffice-help-it' is not installed, so not removed
Package 'libreoffice-help-ja' is not installed, so not removed
Package 'libreoffice-help-km' is not installed, so not removed
Package 'libreoffice-help-ko' is not installed, so not removed
Package 'libreoffice-help-nl' is not installed, so not removed
Package 'libreoffice-help-om' is not installed, so not removed
Package 'libreoffice-help-pl' is not installed, so not removed
Package 'libreoffice-help-pt' is not installed, so not removed
Package 'libreoffice-help-pt-br' is not installed, so not removed
Package 'libreoffice-help-ru' is not installed, so not removed
Package 'libreoffice-help-sk' is not installed, so not removed
Package 'libreoffice-help-sl' is not installed, so not removed
Package 'libreoffice-help-sv' is not installed, so not removed
Package 'libreoffice-help-tr' is not installed, so not removed
Package 'libreoffice-help-vi' is not installed, so not removed
Package 'libreoffice-help-zh-cn' is not installed, so not removed
Package 'libreoffice-help-zh-tw' is not installed, so not removed
Package 'libreoffice-impress' is not installed, so not removed
Package 'libreoffice-java-common' is not installed, so not removed
Package 'libreoffice-l10n-af' is not installed, so not removed
Package 'libreoffice-l10n-ar' is not installed, so not removed
Package 'libreoffice-l10n-as' is not installed, so not removed
Package 'libreoffice-l10n-ast' is not installed, so not removed
Package 'libreoffice-l10n-be' is not installed, so not removed
Package 'libreoffice-l10n-bg' is not installed, so not removed
Package 'libreoffice-l10n-bn' is not installed, so not removed
Package 'libreoffice-l10n-br' is not installed, so not removed
Package 'libreoffice-l10n-bs' is not installed, so not removed
Package 'libreoffice-l10n-ca' is not installed, so not removed
Package 'libreoffice-l10n-cs' is not installed, so not removed
Package 'libreoffice-l10n-cy' is not installed, so not removed
Package 'libreoffice-l10n-da' is not installed, so not removed
Package 'libreoffice-l10n-dz' is not installed, so not removed
Package 'libreoffice-l10n-el' is not installed, so not removed
Package 'libreoffice-l10n-eo' is not installed, so not removed
Package 'libreoffice-l10n-es' is not installed, so not removed
Package 'libreoffice-l10n-et' is not installed, so not removed
Package 'libreoffice-l10n-eu' is not installed, so not removed
Package 'libreoffice-l10n-fa' is not installed, so not removed
Package 'libreoffice-l10n-fi' is not installed, so not removed
Package 'libreoffice-l10n-fr' is not installed, so not removed
Package 'libreoffice-l10n-ga' is not installed, so not removed
Package 'libreoffice-l10n-gd' is not installed, so not removed
Package 'libreoffice-l10n-gl' is not installed, so not removed
Package 'libreoffice-l10n-gu' is not installed, so not removed
Package 'libreoffice-l10n-he' is not installed, so not removed
Package 'libreoffice-l10n-hi' is not installed, so not removed
Package 'libreoffice-l10n-hr' is not installed, so not removed
Package 'libreoffice-l10n-hu' is not installed, so not removed
Package 'libreoffice-l10n-id' is not installed, so not removed
Package 'libreoffice-l10n-in' is not installed, so not removed
Package 'libreoffice-l10n-is' is not installed, so not removed
Package 'libreoffice-l10n-it' is not installed, so not removed
Package 'libreoffice-l10n-ja' is not installed, so not removed
Package 'libreoffice-l10n-ka' is not installed, so not removed
Package 'libreoffice-l10n-kk' is not installed, so not removed
Package 'libreoffice-l10n-km' is not installed, so not removed
Package 'libreoffice-l10n-kmr-latn' is not installed, so not removed
Package 'libreoffice-l10n-ko' is not installed, so not removed
Package 'libreoffice-l10n-ku' is not installed, so not removed
Package 'libreoffice-l10n-lt' is not installed, so not removed
Package 'libreoffice-l10n-lv' is not installed, so not removed
Package 'libreoffice-l10n-mk' is not installed, so not removed
Package 'libreoffice-l10n-ml' is not installed, so not removed
Package 'libreoffice-l10n-mn' is not installed, so not removed
Package 'libreoffice-l10n-mr' is not installed, so not removed
Package 'libreoffice-l10n-nb' is not installed, so not removed
Package 'libreoffice-l10n-ne' is not installed, so not removed
Package 'libreoffice-l10n-nl' is not installed, so not removed
Package 'libreoffice-l10n-nn' is not installed, so not removed
Package 'libreoffice-l10n-nr' is not installed, so not removed
Package 'libreoffice-l10n-nso' is not installed, so not removed
Package 'libreoffice-l10n-oc' is not installed, so not removed
Package 'libreoffice-l10n-om' is not installed, so not removed
Package 'libreoffice-l10n-or' is not installed, so not removed
Package 'libreoffice-l10n-pa-in' is not installed, so not removed
Package 'libreoffice-l10n-pl' is not installed, so not removed
Package 'libreoffice-l10n-pt' is not installed, so not removed
Package 'libreoffice-l10n-pt-br' is not installed, so not removed
Package 'libreoffice-l10n-ro' is not installed, so not removed
Package 'libreoffice-l10n-ru' is not installed, so not removed
Package 'libreoffice-l10n-rw' is not installed, so not removed
Package 'libreoffice-l10n-si' is not installed, so not removed
Package 'libreoffice-l10n-sk' is not installed, so not removed
Package 'libreoffice-l10n-sl' is not installed, so not removed
Package 'libreoffice-l10n-sr' is not installed, so not removed
Package 'libreoffice-l10n-ss' is not installed, so not removed
Package 'libreoffice-l10n-st' is not installed, so not removed
Package 'libreoffice-l10n-sv' is not installed, so not removed
Package 'libreoffice-l10n-ta' is not installed, so not removed
Package 'libreoffice-l10n-te' is not installed, so not removed
Package 'libreoffice-l10n-tg' is not installed, so not removed
Package 'libreoffice-l10n-th' is not installed, so not removed
Package 'libreoffice-l10n-tn' is not installed, so not removed
Package 'libreoffice-l10n-tr' is not installed, so not removed
Package 'libreoffice-l10n-ts' is not installed, so not removed
Package 'libreoffice-l10n-ug' is not installed, so not removed
Package 'libreoffice-l10n-uk' is not installed, so not removed
Package 'libreoffice-l10n-uz' is not installed, so not removed
Package 'libreoffice-l10n-ve' is not installed, so not removed
Package 'libreoffice-l10n-vi' is not installed, so not removed
Package 'libreoffice-l10n-xh' is not installed, so not removed
Package 'libreoffice-l10n-za' is not installed, so not removed
Package 'libreoffice-l10n-zh-cn' is not installed, so not removed
Package 'libreoffice-l10n-zh-tw' is not installed, so not removed
Package 'libreoffice-l10n-zu' is not installed, so not removed
Package 'libreoffice-officebean' is not installed, so not removed
Package 'libreoffice-ogltrans' is not installed, so not removed
Package 'libreoffice-pdfimport' is not installed, so not removed
Package 'libreoffice-presentation-minimizer' is not installed, so not removed
Package 'libreoffice-sdbc-firebird' is not installed, so not removed
Package 'libreoffice-sdbc-hsqldb' is not installed, so not removed
Package 'libreoffice-style-human' is not installed, so not removed
Package 'libreoffice-style-tango' is not installed, so not removed
Package 'browser-plugin-libreoffice' is not installed, so not removed
Package 'libreoffice' is not installed, so not removed
Package 'libreoffice-emailmerge' is not installed, so not removed
Package 'libreoffice-gtk3' is not installed, so not removed
Package 'libreoffice-kde' is not installed, so not removed
Package 'libreoffice-librelogo' is not installed, so not removed
Package 'libreoffice-mysql-connector' is not installed, so not removed
Package 'libreoffice-presenter-console' is not installed, so not removed
Package 'libreoffice-report-builder' is not installed, so not removed
Package 'libreoffice-report-builder-bin' is not installed, so not removed
Package 'libreoffice-script-provider-bsh' is not installed, so not removed
Package 'libreoffice-script-provider-js' is not installed, so not removed
Package 'libreoffice-script-provider-python' is not installed, so not removed
Package 'libreoffice-sdbc-postgresql' is not installed, so not removed
Package 'libreoffice-style-crystal' is not installed, so not removed
Package 'libreoffice-style-hicontrast' is not installed, so not removed
Package 'libreoffice-style-oxygen' is not installed, so not removed
Package 'libreoffice-style-sifr' is not installed, so not removed
Package 'libreoffice-subsequentcheckbase' is not installed, so not removed
Package 'libreoffice-wiki-publisher' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mythes-de : Depends: libreoffice-core but it is not going to be installed or
                      openoffice.org-core (>= 3.0~) but it is not installable
 mythes-de-ch : Depends: libreoffice-core but it is not going to be installed or
                         openoffice.org-core (>= 3.0~) but it is not installable
 mythes-en-us : Depends: libreoffice-core but it is not going to be installed or
                         openoffice.org-core (>= 1.9) but it is not installable or
                         language-support-writing-en but it is not installable
 python3-uno : Depends: libreoffice-core (= 1:4.3.2~rc2-0ubuntu1~trusty2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
k@Anna-PC:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.3.2~rc2) but it is not installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-de : Depends: libreoffice-common but it is not installed
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not installed
 skype : Depends: skype-bin but it is not installable
E: Unmet dependencies. Try using -f.

```

---

### Post by ian-weisser on 2016-04-04
Deeper down the rabbit-hole.

Try:
```
sudo dpkg --remove mythes-de mythes-de-ch mythes-en-us libreoffice-core libreoffice-help-en-us libreoffice-l10n-de libreoffice-l10n-en-gb libreoffice-l10n-en-za skype
```

---

### Post by anna16 on 2016-04-06
And here the cat bites itself in the tail again... Same old error... :-(

```

k@Anna-PC:~$ LANG=C;sudo dpkg --remove mythes-de mythes-de-ch mythes-en-us libreoffice-core libreoffice-help-en-us libreoffice-l10n-de libreoffice-l10n-en-gb libreoffice-l10n-en-za skype
[sudo] password for k: 
dpkg: parse error, in file '/var/lib/dpkg/status' near line 90 package 'python-pkg-resources':
 `Depends' field, invalid package name `python:any': character `:' not allowed (only letters, digits and characters `-+._')

```

---

### Post by Bashing-om on 2016-04-06
anna16; ian-weisser;  Uh HuH ....

> 
Deeper down the rabbit-hole.


And back were we started.
Ian. I have been unable to determine the why :
> 
dpkg: parse error, in file '/var/lib/dpkg/status' near line 90 package 'python-pkg-resources':

Even tried to follow the bread crumbs and I can not find a fault in any of the config files.

Are we looking at some kind of imposed restriction on the field " python:any " ???

Looking to get light on the subject .

[INDENT][INDENT]something soon has got to shine
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2016-04-06
> **Bashing-om said:**
> Are we looking at some kind of imposed restriction on the field " python:any " ???

No such restriction. The field is valid, python:any has been a valid name for years, and ':' is certainly a permitted char in 14.04.
Seems like a corrupted status file, perhaps a non-printing char has inserted in there someplace.

Rename /var/lib/dpkg/status to something backup.
Copy /var/lib/dpkg/status-old to /var/lib/dpkg/status

And try again.

Disk corruption is a good reason to have backups....

---

