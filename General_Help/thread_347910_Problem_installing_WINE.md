---
title: "Problem installing WINE"
date: 2007-01-28
forum: General Help
---

### Post by Scooter7 on 2007-01-28
Hi, I'm trying to install WINE.   I'm using [www.ubuntuguide.org](www.ubuntuguide.org).   I had WINE installed previously using the exact same method.   I removed WINE today because I no longer needed it, by typing 'sudo apt-get remove wine'.   After doing that, later on, I decided I wanted to try World of Warcraft with it.   So I tried installing again.   I tried many installs, and uninstalls, but WINE doesn't seem to work.   Before, right-clicking on an .exe file opened up a menu with the choice 'open using WINE windows emulator', but now that choice won't appear.   Now, I have WINE uninstalled, and I tried installing again after removing all changes described in the Ubuntu Guide, then doing them over, but I get this error:

> Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

I get that using 'sudo apt-get install wine'.   I also get it if I try using the Synaptic Package Manager.   What's wrong?   As far as I know, I did nothing to make WINE stop working, and now I can't even install it again. :mad:

---

### Post by taurus on 2007-01-28
What does your /etc/apt/sources.list look like anyway?

```
cat /etc/apt/sources.list
```

---

### Post by Scooter7 on 2007-01-28
> deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

# Repository for Beryl?
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info](http://xgl.compiz.info) dapper main

# Other stuff O_o

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

The repository for wine is the same as it was when I first installed, as far as I know...

---

### Post by taurus on 2007-01-28
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove all the # in front of deb.  Save it and then run

```
sudo apt-get update
sudo apt-get install wine
```

---

### Post by Scooter7 on 2007-01-28
Okay, I edited sources.list, and then when I entered:

```
sudo apt-get update
```

I got this output:

> Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release.gpg
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Translation-en_CA                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]                  
Get:4 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]                       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Translation-en_CA             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Translation-en_CA             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_CA            
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Translation-en_CA                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_CA      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Translation-en_CA               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_CA                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_CA                
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release                                    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_CA      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Translation-en_CA               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_CA        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_CA        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages                              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Translation-en_CA           
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages                              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Translation-en_CA     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Translation-en_CA     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Translation-en_CA       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports Release.gpg [191B]           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/main Translation-en_CA         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/restricted Translation-en_CA   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/universe Translation-en_CA     
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [2739B]        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Translation-en_CA                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/multiverse Translation-en_CA   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release                          
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports Release [38.4kB]             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Packages                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release                                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Packages                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Sources                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Sources                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Packages
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Sources [1068kB]
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg                               
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages                            
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages                            
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Translation-en_CA                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Packages                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Sources               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Packages                
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/main Packages [2857B]       
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/restricted Packages [14B]   
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/universe Packages [15.7kB]  
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/multiverse Packages [4183B] 
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/main Sources [1592B]        
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/restricted Sources [14B]    
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/universe Sources [5156B]    
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/multiverse Sources [1277B]  
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release                                      
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages                                
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources                                 
Err [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
  503 Service Unavailable
Err [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
  503 Service Unavailable
Fetched 1140kB in 32s (34.7kB/s)
Failed to fetch [http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz](http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz) 503 Service Unavailable
Failed to fetch [http://xgl.compiz.info/dists/dapper/main/source/Sources.gz](http://xgl.compiz.info/dists/dapper/main/source/Sources.gz) 503 Service Unavailable
Reading package lists... Done
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_edgy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

I ignored these errors, and tried

```
sudo apt-get install wine
```

And got this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

So, the same error as before. :???:

---

### Post by taurus on 2007-01-28
If I were you, I would make my /etc/apt/sources.list to look like this for now.

```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

# Repository for wine
#deb http://wine.budgetdedicated.com/apt edgy main
#deb-src http://wine.budgetdedicated.com/apt edgy main

# Repository for Beryl?
#deb http://www.beerorkid.com/compiz/ dapper main
#deb http://xgl.compiz.info/ dapper main
#deb-src http://xgl.compiz.info dapper main

# Other stuff O_o

#deb http://blognux.free.fr/debian unstable main

```
Save it and then run

```
sudo apt-get update
sudo apt-get install wine
```

[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by Scooter7 on 2007-01-28
Well, that almost worked, but I still get the error when trying to install wine...

---

### Post by taurus on 2007-01-28
In that case, why don't you install automatix2 and use it to install wine then.

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by Scooter7 on 2007-01-28
...well, tried that, didn't work.  I just got a message saying

> FATAL ERROR: WINE
An apt-based error occured and installation was unsuccessful.

---

