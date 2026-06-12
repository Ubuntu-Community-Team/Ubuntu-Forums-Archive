---
title: "Gutsy 7.10 sources.list"
date: 2007-10-18
forum: General Help
---

### Post by sweener on 2007-10-18
Just wanted to share my updated sources.list for Gutsy 7.10 with everyone. This is based off of Trevino's original Fiesty Fawn repository list found here: [http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/]("http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/")

Use you favorite editor and edit /etc/apt/sources.list with root privileges. Use at your own risk.

```

# Sweener's Ubuntu Gutsy Gibbon 7.10 Sources list
# 
# Repository List based on standard gutsy with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
#  gpg --keyserver subkeys.pgp.net --recv KEY
#  gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
#  wget -q URL -O- | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
#  sudo apt-key add FILE

# Ubuntu supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

# Ubuntu Proposed packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe

#Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu gutsy partner
#deb-src http://archive.canonical.com/ubuntu gutsy partner

# UbuntuStudio Repository (GPG key: B6A4EB33)
#deb http://archive.ubuntustudio.org/ubuntustudio gutsy main
#deb-src http://archive.ubuntustudio.org/ubuntustudio gutsy main

# Bleeding edge wine packages
deb http://wine.budgetdedicated.com/apt gutsy main
deb-src http://wine.budgetdedicated.com/apt gutsy main

# Seveas&#8217; packages (GPG key: 1135D466)
# GPG key-file: http://mirror.ubuntulinux.nl/1135D466.gpg
deb http://mirror.ubuntulinux.nl gutsy-seveas all
deb-src http://mirror.ubuntulinux.nl gutsy-seveas all

# Upstream Opera (GPG key: 6A423791)
deb http://deb.opera.com/opera etch non-free

# Upstream Beryl (GPG key: ed8a569e)
deb http://ubuntu.beryl-project.org/ edgy main 
deb-src http://ubuntu.beryl-project.org/ edgy main

# Medibuntu - Ubuntu 7.10 "gutsy gibbon"
# GPG key-file: http://packages.medibuntu.org/medibuntu-key.gpg
deb http://packages.medibuntu.org/ gutsy free non-free
#deb-src http://packages.medibuntu.org/ gutsy free non-free

# The repository from Kubuntu Germany
# GPG key-file: http://archive.czessi.net/ubuntu/kczessi.gpg
deb http://archive.czessi.net/ubuntu gutsy main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu gutsy main restricted universe multiverse preview

# Achim&#8217;s Unofficial &#8216;gutsy&#8217; Kubuntu packages
# GPG key-file: http://www.mpe.mpg.de/~ach/ach-gpg.asc
deb http://www.mpe.mpg.de/~ach/kubuntu/gutsy ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/gutsy ./

# Ekiga and Debian pkg-voip
deb http://pkg-voip.buildserver.net/ubuntu gutsy main

# Ubuntu repository for Screenlets (GPG key: F854AFD7)
# GPG key-file: http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
deb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets
deb-src http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets

# Subpixel Font rendering packages (GPG key: 937215FF)
# Improved fonts on LCDs - WARNING: May violate some patents
# GPG key-file: http://www.telemail.fi/mlind/ubuntu/937215FF.gpg
deb http://www.telemail.fi/mlind/ubuntu feisty fonts main
deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts main

# Skype packages
deb http://download.skype.com/linux/repos/debian/ stable non-free

# gnomemeeting - ekiga (GPG key: 52ABFCB1)
deb http://snapshots.ekiga.net/ubuntu/ gutsy main
deb-src http://snapshots.ekiga.net/ubuntu/ gutsy main

# Cafuego&#8217;s feisty Stuff: Broadcom firmware, google-earth, secondlife
deb http://au.ubuntu.cafuego.net gutsy-cafuego all
#deb-src http://au.ubuntu.cafuego.net gutsy-cafuego all

# Debuntu Ubuntu gutsy packages
# GPG Key: http://repository.debuntu.org/GPG-Key-chantra.txt
deb  http://repository.debuntu.org/ gutsy multiverse
#deb-src http://repository.debuntu.org/ gutsy multivers

# Automatix Repo
deb http://www.getautomatix.com/apt gutsy main

# The Ubuntu NLP Repository (GPG key: 8ABD1965)
# GPG key-file: http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg
deb http://cl.naist.jp/~eric-n/ubuntu-nlp gutsy all
deb-src http://cl.naist.jp/~eric-n/ubuntu-nlp feisty all

# syzygy42 repository: avant-window-navigator, exaile, closure&#8230; (GPG key: 8434D43A)
# GPG key-file: http://download.tuxfamily.org/syzygy42/8434D43A.gpg
deb http://download.tuxfamily.org/syzygy42/ gutsy all
deb-src http://download.tuxfamily.org/syzygy42/ gutsy all

## Swiftfox (enhanced Firefox for linux) packages
deb http://getswiftfox.com/builds/debian unstable non-free

# Le dépomaniak repository (GPG key: 1D59E694)
# GPG key-file: http://ubuntu.davromaniak.eu/1D59E694.gpg
deb http://ubuntu.davromaniak.eu gutsy-depomaniak all
deb-src http://ubuntu.davromaniak.eu gutsy-depomaniak all

# Ryan Kavanagh&#8217;s packages (GPG key: 02544D0E)
# GPG key-file: http://packages.ryanak.ca/02544D0E.gpg
deb http://packages.ryanak.ca ryan-gutsy all
deb-src http://packages.ryanak.ca ryan-gutsy all

# Iuculano&#8217;s debian packages (GPG key: AE3BE9AA)
# GPG key-file: http://ubuntu.iuculano.it/AE3BE9AA.gpg
deb http://ubuntu.iuculano.it gutsy all
deb-src http://ubuntu.iuculano.it gutsy all

# Elisa Debian Packages
# GPG key-file: http://elisa.fluendo.com/packages/philn.asc
deb http://elisa.fluendo.com/packages gutsy main

# Virtualbox PUEL
# GPG key-file: http://www.virtualbox.org/debian/innotek.asc
deb http://www.virtualbox.org/debian gutsy non-free

#Deluge
deb http://ppa.launchpad.net/zachtib/ubuntu gutsy main universe

## Elbuntu
# GPG key-file: http://lut1n.ifrance.com/repo_key.asc
deb http://e17.dunnewind.net/ubuntu gutsy e17

```

---

### Post by OXIj on 2007-10-21
a little trick for lazy people =)

```
 KEYS=`cat /etc/apt/sources.list | grep 'GPG key:' | cut -d'(' -f2- | cut -d" " -f3 | cut -d")" -f1 | xargs echo`
for KEY in $KEYS; do echo gpg --keyserver subkeys.pgp.net --recv $KEY && echo "gpg --export --armor $KEY | sudo apt-key add -"; done
```

---

### Post by chadraytay on 2007-10-21
Ah, the second part of this would make things a lot easier. From the feisty page...

for i in $(grep -o -E "http.*\.(gpg|asc|key)" /etc/apt/sources.list); do echo -n "$i "; wget $i -q -O - | sudo apt-key add -; done; keylist=""; for key in $(grep -o "[A-Fa-f0-9]\{8\}" /etc/apt/sources.list); do if [ -z "$(echo "$keylist"|grep "$key")" ]; then keylist="$keylist $key"; gpg --keyserver subkeys.pgp.net --recv $key && gpg --export --armor $key | sudo apt-key add -; fi; done;

---

### Post by BLTicklemonster on 2007-10-21
Some splaining, please? What does the stuff in post 2 do, automagically create a new list? Is there no way to make this an integral part of ubuntu in order to further facilitate the ease of keeping current something blah lost my train of thought. Dang.

---

### Post by dan.abramov on 2007-10-23
Nope. It automatically downloads all required gpg's if I got it right.

---

### Post by octoberdan on 2007-11-20
What fantastic collection! Thank you! Thanks also for the scripts!

---

### Post by octoberdan on 2007-11-20
I thinned mine down to the following:
```

# Ubuntu supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

# Ubuntu Proposed packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe

#Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu gutsy partner
#deb-src http://archive.canonical.com/ubuntu gutsy partner

# UbuntuStudio Repository (GPG key: B6A4EB33)
#deb http://archive.ubuntustudio.org/ubuntustudio gutsy main
#deb-src http://archive.ubuntustudio.org/ubuntustudio gutsy main

# Bleeding edge wine packages
deb http://wine.budgetdedicated.com/apt gutsy main
deb-src http://wine.budgetdedicated.com/apt gutsy main

# Medibuntu - Ubuntu 7.10 "gutsy gibbon"
# GPG key-file: http://packages.medibuntu.org/medibuntu-key.gpg
deb http://packages.medibuntu.org/ gutsy free non-free
#deb-src http://packages.medibuntu.org/ gutsy free non-free

# Iuculano’s debian packages (GPG key: AE3BE9AA)
# GPG key-file: http://ubuntu.iuculano.it/AE3BE9AA.gpg
deb http://ubuntu.iuculano.it gutsy all
deb-src http://ubuntu.iuculano.it gutsy all

#Deluge
deb http://ppa.launchpad.net/zachtib/ubuntu gutsy main universe

```

---

### Post by brjoon1021 on 2007-12-03
Uh, sorry, but I have to ask what some or all of these other repo's. do for you? Do you have them all checked at the same time? Can synaptic handle picking the right package to upgrade to, for instance, if 4 or 5 of these repos all have mplayer with codecs or flash.

I was worried about enabling medibuntu, I guess I am really conservative !!!

---

### Post by superchargingmachine on 2007-12-31
> **OXIj said:**
> a little trick for lazy people =)

```
 KEYS=`cat /etc/apt/sources.list | grep 'GPG key:' | cut -d'(' -f2- | cut -d" " -f3 | cut -d")" -f1 | xargs echo`
for KEY in $KEYS; do echo gpg --keyserver subkeys.pgp.net --recv $KEY && echo "gpg --export --armor $KEY | sudo apt-key add -"; done
```

I tried the code above and hoped this would import all the keys for that huge apt repo but I didn't have any luck with it.  Any help or better explanation?

Importing these gpg keys manually for a large sources.list file is a PITA!!!

---

### Post by Trinary on 2008-01-06
Use chadraytay's post, it worked for me.

---

### Post by of_darkness on 2008-01-07
> **brjoon1021 said:**
> Uh, sorry, but I have to ask what some or all of these other repo's. do for you? Do you have them all checked at the same time? Can synaptic handle picking the right package to upgrade to, for instance, if 4 or 5 of these repos all have mplayer with codecs or flash.

I was worried about enabling medibuntu, I guess I am really conservative !!!
Well in synaptic you can chose the standard version , like gutsy,gutsy back ports,gutsy security or simply but most dangerous especially if you have any Debian repos - latest version.. i have put mine on Gutsy cause it seams 2 work the best 4 me and i have allot of unsupported repos in my list.. even some Debian repos..

---

### Post by abhiroopb on 2008-03-24
I'd appreciate it if someone could just take a look at my sources.list and let me know if there are any possible issues:

```

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

##Universe

deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

# Medibuntu - Ubuntu 7.10 "gutsy gibbon"
# GPG key-file: http://packages.medibuntu.org/medibuntu-key.gpg
deb http://packages.medibuntu.org/ gutsy free non-free
#deb-src http://packages.medibuntu.org/ gutsy free non-free

#avant window navigator
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

#Virtualbox
deb http://www.virtualbox.org/debian gutsy non-free

#Gnome-Do
deb http://ppa.launchpad.net/do-core/ubuntu gutsy main

#Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

#Miro
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu gutsy/

#Deluge
deb http://ppa.launchpad.net/zachtib/ubuntu gutsy main universe


```

The only issue I have is that I get the following error when I do sudo apt-get update (scroll to the bottom):

```

$ sudo apt-get update
[sudo] password for USER:
Ign http://ppa.launchpad.net gutsy Release.gpg
Ign http://ppa.launchpad.net gutsy/main Translation-en_SG                      
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Get:1 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_SG               
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_SG           
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_SG     
Get:3 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://ppa.launchpad.net gutsy/main Translation-en_SG                      
Ign http://ppa.launchpad.net gutsy/universe Translation-en_SG                  
Ign http://archive.ubuntu.com gutsy/main Translation-en_SG                     
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_SG               
Hit http://ppa.launchpad.net gutsy Release                                     
Ign http://download.skype.com stable Release.gpg                               
Ign http://download.skype.com stable/non-free Translation-en_SG                
Get:4 http://www.virtualbox.org gutsy Release.gpg [189B]                       
Ign http://www.virtualbox.org gutsy/non-free Translation-en_SG                 
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_SG       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_SG     
Hit http://security.ubuntu.com gutsy-security Release                          
Ign http://archive.ubuntu.com gutsy/universe Translation-en_SG                 
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_SG               
Get:5 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]               
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_SG             
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_SG       
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_SG         
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_SG       
Hit http://archive.canonical.com gutsy Release                                 
Get:6 http://download.tuxfamily.org gutsy Release.gpg [189B]                   
Hit http://ppa.launchpad.net gutsy Release                                     
Get:7 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Ign http://packages.medibuntu.org gutsy/free Translation-en_SG                 
Ign http://download.skype.com stable Release                                   
Get:8 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]             
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_SG           
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_SG     
Hit http://www.virtualbox.org gutsy Release                                    
Ign http://download.tuxfamily.org gutsy/avant-window-navigator Translation-en_SG
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Ign http://ppa.launchpad.net gutsy/main Packages                               
Hit http://archive.canonical.com gutsy/partner Packages                        
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_SG       
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_SG     
Get:9 http://archive.ubuntu.com gutsy Release [65.9kB]                         
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_SG             
Hit http://packages.medibuntu.org gutsy Release                                
Hit http://download.skype.com stable/non-free Packages                         
Hit http://www.virtualbox.org gutsy/non-free Packages                          
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Get:10 http://download.tuxfamily.org gutsy Release [10.9kB]                    
Hit http://archive.canonical.com gutsy/partner Sources                         
Ign http://ppa.launchpad.net gutsy/main Packages                               
Ign http://ppa.launchpad.net gutsy/universe Packages                           
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://security.ubuntu.com gutsy-security/universe Sources                 
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Hit http://security.ubuntu.com gutsy-security/multiverse Sources               
Hit http://ppa.launchpad.net gutsy/main Packages                               
Hit http://ppa.launchpad.net gutsy/main Packages                               
Ign http://packages.medibuntu.org gutsy/free Packages                          
Hit http://ppa.launchpad.net gutsy/universe Packages                           
Ign http://packages.medibuntu.org gutsy/non-free Packages                      
Ign http://ftp.osuosl.org gutsy/ Release.gpg                                   
Ign http://ftp.osuosl.org gutsy/ Translation-en_SG                             
Get:11 http://download.tuxfamily.org gutsy/avant-window-navigator Packages [3174B]
Hit http://packages.medibuntu.org gutsy/free Packages                          
Get:12 http://archive.ubuntu.com gutsy-updates Release [58.5kB]                
Get:13 http://download.tuxfamily.org gutsy/avant-window-navigator Sources [1351B]
Hit http://packages.medibuntu.org gutsy/non-free Packages                      
Ign http://ftp.osuosl.org gutsy/ Release                                     
Get:14 http://archive.ubuntu.com gutsy-backports Release [44.0kB]
Ign http://ftp.osuosl.org gutsy/ Packages                                    
Get:15 http://archive.ubuntu.com gutsy/main Packages [1075kB]
Hit http://ftp.osuosl.org gutsy/ Packages                                     
Get:16 http://archive.ubuntu.com gutsy/restricted Packages [7664B]
Get:17 http://archive.ubuntu.com gutsy/main Sources [306kB]
Get:18 http://archive.ubuntu.com gutsy/restricted Sources [2120B]
Get:19 http://archive.ubuntu.com gutsy/universe Packages [4065kB]
Get:20 http://archive.ubuntu.com gutsy/universe Sources [1226kB]               
Get:21 http://archive.ubuntu.com gutsy/multiverse Packages [158kB]             
Get:22 http://archive.ubuntu.com gutsy/multiverse Sources [56.8kB]             
Get:23 http://archive.ubuntu.com gutsy-updates/main Packages [247kB]           
Get:24 http://archive.ubuntu.com gutsy-updates/restricted Packages [4263B]     
Get:25 http://archive.ubuntu.com gutsy-updates/main Sources [68.9kB]           
Get:26 http://archive.ubuntu.com gutsy-updates/restricted Sources [937B]       
Get:27 http://archive.ubuntu.com gutsy-updates/universe Packages [72.4kB]      
Get:28 http://archive.ubuntu.com gutsy-updates/universe Sources [11.5kB]       
Get:29 http://archive.ubuntu.com gutsy-updates/multiverse Packages [9942B]     
Get:30 http://archive.ubuntu.com gutsy-updates/multiverse Sources [1883B]      
Get:31 http://archive.ubuntu.com gutsy-backports/main Packages [29.6kB]        
Get:32 http://archive.ubuntu.com gutsy-backports/restricted Packages [14B]     
Get:33 http://archive.ubuntu.com gutsy-backports/universe Packages [87.3kB]    
Get:34 http://archive.ubuntu.com gutsy-backports/multiverse Packages [15.2kB]  
Get:35 http://archive.ubuntu.com gutsy-backports/main Sources [8505B]          
Get:36 http://archive.ubuntu.com gutsy-backports/restricted Sources [14B]      
Get:37 http://archive.ubuntu.com gutsy-backports/universe Sources [19.3kB]     
Get:38 http://archive.ubuntu.com gutsy-backports/multiverse Sources [3230B]    
Fetched 7661kB in 17s (449kB/s)                                                
Reading package lists... Done
W: Duplicate sources.list entry http://packages.medibuntu.org gutsy/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_gutsy_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org gutsy/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_gutsy_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by plucky on 2008-03-24
Open a terminal and copy and paste this command into it ```
cat /etc/apt/sources.list.d/medibuntu.list
``` If it comes back with > ## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

Then you need to comment out this line in your sources list > deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

Then ```
 sudo apt-get update
sudo apt-get upgrade
```

Good Luck

---

### Post by abhiroopb on 2008-03-24
I see the point of what you said, it makes sense, but I still want to have the package.medibuntu, is it still there?

---

### Post by plucky on 2008-03-24
> is it still there?


Yes it is here ```
/etc/apt/sources.list.d/medibuntu.list
``` and is read when you do ```
sudo apt-get update
sudo apt-get upgrade
```

That was why you were getting >  W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_gutsy_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_gutsy_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


Try it

Good Luck

---

### Post by abhiroopb on 2008-03-24
Sorry I wasn't clear, it got rid of the error, but doesn't this mean that the I can't use the medibuntu repository anyway?

---

### Post by plucky on 2008-03-24
abhiroopb,

>  but doesn't this mean that the I can't use the medibuntu repository anyway?

Double negative = Positive (You can)

The Medibuntu repository is still accessible so you **can** use it as it is located in  sub directory of the sources list directory **/etc/apt/sources.list.d/medibuntu.list**


If you do ```
sudo apt-get update
``` you will find the Medibuntu repository has been read.


Good Luck

---

### Post by abhiroopb on 2008-03-24
thanks sorry its late and I didn't re-read what I'd written!

---

### Post by hamid.nyc on 2008-04-22
Thanks Sweener for that great sources.list. I was having problems with WinFF encoding from .flv to Xvid, as it turns out, I just wasn't getting the right codecs in my updates 'cause I had an outdated list. works fantastic now...

---

