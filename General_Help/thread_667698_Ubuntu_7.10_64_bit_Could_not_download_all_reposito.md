---
title: "Ubuntu 7.10 64 bit Could not download all repository indexes"
date: 2008-01-14
forum: General Help
---

### Post by kingleer on 2008-01-14
When I try to do an update I get the following error -

> 
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.canonical.com/ubuntu/...4/Packages.gz:](http://archive.canonical.com/ubuntu/...4/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/di...4/Packages.gz:](http://medibuntu.sos-sts.com/repo/di...4/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/di...4/Packages.gz:](http://medibuntu.sos-sts.com/repo/di...4/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/di...ce/Sources.gz:](http://medibuntu.sos-sts.com/repo/di...ce/Sources.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/di...ce/Sources.gz:](http://medibuntu.sos-sts.com/repo/di...ce/Sources.gz:) 404 Not Found
I already tried Synaptic package manager to solve this problem and restarting. I checked to make sure all the right boxes are ticked under Software Sources.


When I type

> 
cat /etc/apt/sources.list


in the terminal, I get the following output

> 
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free


Just tried entering sudo apt-get update in the terminal.

I got the following error

> 
Some index files failed to download, they have been ignored, or old ones used instead.
 

Can anyone tell me what I'm doing wrong? Thanks in advance...

---

### Post by taurus on 2008-01-14
Edit /etc/apt/sources.list and change these current repos

```

deb http://archive.canonical.com/ubuntu gutsy-commercial main

deb http://medibuntu.sos-sts.com/repo/ gutsy free non-free
deb-src http://medibuntu.sos-sts.com/repo/ gutsy free non-free 

```
to

```

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

```
Save it and then run

```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

---

### Post by kingleer on 2008-01-14
I get the following output 

> 
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy-commercial Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy-commercial/main Translation-en_CA       
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_CA                     
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_CA               
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy-commercial Release                      
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_CA           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_CA               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_CA                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_CA               
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_CA             
Get:5 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release [6998B]                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_CA     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_CA       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_CA     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_CA         
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_CA           
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy-commercial/main Packages                
Get:7 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages [1993B]              
Get:8 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources [1221B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_CA     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_CA     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                          
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy-commercial/main Packages                
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [2901B]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                      
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages [9226B]     
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages [48.2kB]      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages              
Get:12 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_CA                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_CA             
Get:13 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release [2718B]                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Get:14 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages [5880B]               
Get:15 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages [2562B]           
Fetched 82.1kB in 2m5s (656B/s)                                                
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-amd64/Packages.gz) 404 Not Found
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_universe_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


after entering

> 
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update


I also get the following error when I try using update manager

> 
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://packages.medibuntu.org/dists/gutsy/Release.gpg](http://packages.medibuntu.org/dists/gutsy/Release.gpg)
[http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_CA.bz2](http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_CA.bz2)
[http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_CA.bz2](http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_CA.bz2)
[http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-amd64/Packages.gz:](http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-amd64/Packages.gz:) 404 Not Found


---

