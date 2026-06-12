---
title: "Wine help"
date: 2007-12-14
forum: General Help
---

### Post by CanadianGuitarist on 2007-12-14
so im trying to get WINE for gutsy. can someone give me some instructions. i have only gotten errors so far

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

## WINE REPOSITORY
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## MEDIBUNTU REPOSITORY
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

## VIRTUALBOX REPOSITORY
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

---

### Post by PmDematagoda on 2007-12-14
What do you get when you do:-

```
sudo apt-get install wine
```

---

### Post by CanadianGuitarist on 2007-12-14
sorry i fell asleep then had school / hockey

i get this. im guessing a problem with cupsys eh?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support
The following NEW packages will be installed:
  binfmt-support wine
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 33.9MB of archives.
After unpacking 106MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe binfmt-support 1.2.10 [21.4kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe wine 0.9.46-0ubuntu1 [33.9MB]
Fetched 33.9MB in 1m6s (510kB/s)                                               
Selecting previously deselected package binfmt-support.
(Reading database ... 112892 files and directories currently installed.)
Unpacking binfmt-support (from .../binfmt-support_1.2.10_all.deb) ...
Selecting previously deselected package wine.
Unpacking wine (from .../wine_0.9.46-0ubuntu1_i386.deb) ...
Setting up cupsys (1.3.2-1ubuntu7.2) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Setting up binfmt-support (1.2.10) ...
 * Enabling additional executable binary formats binfmt-support          [ OK ] 

Setting up wine (0.9.46-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by r-mo on 2007-12-14
Make sure you've done a system update, I'm sure I remember having this problem with early gutsy and it looks like your package list is out of date as wine is 0.9.50 the budgetdedicated repo you have set up and apt is trying to install 0.9.46
```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install wine

```

---

### Post by CanadianGuitarist on 2007-12-14
i think im still getting errors. 

Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US  
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US   
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release [2723B]            
Get:7 [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release.gpg [189B]             
Ign [http://www.virtualbox.org](http://www.virtualbox.org) gutsy/non-free Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Hit [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release                          
Err [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release                          
  
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release.gpg [191B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                
Get:10 [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release [700B]                
Ign [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources            
Hit [http://www.virtualbox.org](http://www.virtualbox.org) gutsy/non-free Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages            
Get:11 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources [1502B]      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Packages    
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg                
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out
Fetched 5309B in 4m0s (22B/s)                                
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg](http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out
Reading package lists... Done
W: GPG error: [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cupsys (1.3.2-1ubuntu7.2) ...
Reloading AppArmor profiles : done.
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by r-mo on 2007-12-14
looks like you might have an internet connection problem.  Do you connect through a proxy? if so try:

```
export http_proxy=http://proxy:port
```

and try pinging to see if you get a response

```
ping wine.budgetdedicated.com -c4
```

---

### Post by CanadianGuitarist on 2007-12-14
i dont think so. I'm wireless on a LAN. ill give that a try tho. EDIT: im getting and error like this when i try and install other things too.

EDIT:
PING wine.budgetdedicated.com (81.171.111.184) 56(84) bytes of data.

--- wine.budgetdedicated.com ping statistics ---
4 packets transmitted, 0 received, 100% packet lost

---

### Post by CanadianGuitarist on 2007-12-15
so what do i do with this error?

dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by r-mo on 2007-12-15
try

```
sudo aptitude reinstall cupsys
```

I'm not entirely sure you're receiving updates though, it should find version 1.3.2-1ubuntu7.2)

---

### Post by CanadianGuitarist on 2007-12-15
I dont think that worked. is there another way to reinstall it?

A package failed to install.  Trying to recover:
Setting up cupsys (1.3.2-1ubuntu7.2) ...
Reloading AppArmor profiles : done.
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:4797: parser error : Extra content at the end of the document
toc></doc></sect>
^
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done

---

