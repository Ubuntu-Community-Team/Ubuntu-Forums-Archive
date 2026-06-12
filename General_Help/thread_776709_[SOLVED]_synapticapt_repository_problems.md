---
title: "[SOLVED] synaptic/apt repository problems"
date: 2008-04-30
forum: General Help
---

### Post by tramir on 2008-04-30
I have a strange problem with Synaptic/apt. If I only have the standard repositories enabled (all ubuntu repos, including partner, and all updates), things work fine. As soon as I try to add another 3rd party repo, things break down. Through trial and error I managed to figure out the following:

1. If no third party repos are enabled (except for the ubuntu partner repo), everything works fine.

2. If a third party repo is enabled and is the last repo in sources.list, apt-get fails to download (rather randomly) from ALL repos. Commenting the repo reduces the issue to case 1 above.

3. If the third party repo is moved in sources.list above another ubuntu repo, then the ubuntu repos work, but this third-party repo fails to download.

The weird thing is that the error message is about not being able to download Packages.gz, but I can manually download the file (wget or Firefox, both work). And it really doesn't matter which tird-party repo we're talking about. I got this error with the repos provided by Exaile, Virtualbox, Deluge etc. Anybody has any idea what could be going on?

---

### Post by tramir on 2008-05-01
*bump*

No idea, anybody?

EDIT: I forgot to mention I use Gutsy, fresh install, no proxy.

---

### Post by warp99 on 2008-05-01
> **tramir said:**
> I have a strange problem with Synaptic/apt. If I only have the standard repositories enabled (all ubuntu repos, including partner, and all updates), things work fine. As soon as I try to add another 3rd party repo, things break down. Through trial and error I managed to figure out the following:

1. If no third party repos are enabled (except for the ubuntu partner repo), everything works fine.

2. If a third party repo is enabled and is the last repo in sources.list, apt-get fails to download (rather randomly) from ALL repos. Commenting the repo reduces the issue to case 1 above.

3. If the third party repo is moved in sources.list above another ubuntu repo, then the ubuntu repos work, but this third-party repo fails to download.

The weird thing is that the error message is about not being able to download Packages.gz, but I can manually download the file (wget or Firefox, both work). And it really doesn't matter which tird-party repo we're talking about. I got this error with the repos provided by Exaile, Virtualbox, Deluge etc. Anybody has any idea what could be going on?

The repository your downloading from is broken or your the line in your /etc/apt/sources.list is incorrect. What 3rd party repos are you talking about?

---

### Post by tramir on 2008-05-01
Well, that's what I thought in the beginning. But I copy/paste the URL from the error message that Synaptic spits out and I can actually download the file. So the repo is not down.

I checked and triple checked sources.list, and the line seems fine. Here's an example of a repo that creates the errors described before:

```
deb http://ppa.launchpad.net/exaile-devel/ubuntu hardy main
```

And it is definitely up and running (or it was last time I checked).

EDIT: And, actually, just to make sure: the problem is not that I can't update this repo, but that once I add this to sources.list, I can't update ALMOST ANY repo (9and that's random, the number and which ones). That's completely weird.

---

### Post by joshsmith on 2008-05-01
give us terminal output of
cat /etc/apt/sources.list

and output of
sudo apt-get update

in both cases

---

### Post by tramir on 2008-05-01
**Case 1:** repo added as last line

sources.list:
```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.osuosl.org/ubuntu/ hardy main universe restricted multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ hardy main universe restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner


deb http://ubuntu.osuosl.org/ubuntu/ hardy-security main universe restricted multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ hardy-security main universe restricted multiverse
deb http://ubuntu.osuosl.org/ubuntu/ hardy-updates universe main restricted multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ hardy-updates universe main restricted multiverse
deb http://ubuntu.osuosl.org/ubuntu/ hardy-proposed universe main restricted multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ hardy-proposed universe main restricted multiverse
deb http://ubuntu.osuosl.org/ubuntu/ hardy-backports universe main restricted multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ hardy-backports universe main restricted multiverse

deb http://ppa.launchpad.net/exaile-devel/ubuntu hardy main
``` 

apt-get update output:
```
Ign http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://ppa.launchpad.net hardy/main Packages                               
Get:2 http://ppa.launchpad.net hardy/main Packages [985B]                  
Hit http://ubuntu.osuosl.org hardy Release.gpg                                 
Ign http://ubuntu.osuosl.org hardy/main Translation-en_US                  
Ign http://ubuntu.osuosl.org hardy/universe Translation-en_US  
Ign http://ubuntu.osuosl.org hardy/restricted Translation-en_US
Ign http://ubuntu.osuosl.org hardy/multiverse Translation-en_US
Hit http://ubuntu.osuosl.org hardy-security Release.gpg        
Ign http://ubuntu.osuosl.org hardy-security/main Translation-en_US
Ign http://ubuntu.osuosl.org hardy-security/universe Translation-en_US
Ign http://ubuntu.osuosl.org hardy-security/restricted Translation-en_US
Ign http://ubuntu.osuosl.org hardy-security/multiverse Translation-en_US
Hit http://ubuntu.osuosl.org hardy-updates Release.gpg         
Ign http://ubuntu.osuosl.org hardy-updates/universe Translation-en_US
Ign http://ubuntu.osuosl.org hardy-updates/main Translation-en_US
Ign http://ubuntu.osuosl.org hardy-updates/restricted Translation-en_US
Ign http://ubuntu.osuosl.org hardy-updates/multiverse Translation-en_US
Hit http://ubuntu.osuosl.org hardy-proposed Release.gpg        
Ign http://ubuntu.osuosl.org hardy-proposed/universe Translation-en_US
Ign http://ubuntu.osuosl.org hardy-proposed/main Translation-en_US
Ign http://ubuntu.osuosl.org hardy-proposed/restricted Translation-en_US
Ign http://ubuntu.osuosl.org hardy-proposed/multiverse Translation-en_US
Hit http://ubuntu.osuosl.org hardy-backports Release.gpg       
Ign http://ubuntu.osuosl.org hardy-backports/universe Translation-en_US
Ign http://ubuntu.osuosl.org hardy-backports/main Translation-en_US
Ign http://ubuntu.osuosl.org hardy-backports/restricted Translation-en_US
Ign http://ubuntu.osuosl.org hardy-backports/multiverse Translation-en_US
Hit http://ubuntu.osuosl.org hardy Release                     
Hit http://ubuntu.osuosl.org hardy-security Release            
Hit http://ubuntu.osuosl.org hardy-updates Release             
Hit http://ubuntu.osuosl.org hardy-proposed Release            
Hit http://ubuntu.osuosl.org hardy-backports Release           
Hit http://ubuntu.osuosl.org hardy/main Packages                               
Hit http://ubuntu.osuosl.org hardy/universe Packages           
Hit http://ubuntu.osuosl.org hardy/restricted Packages         
Hit http://ubuntu.osuosl.org hardy/multiverse Packages         
Hit http://ubuntu.osuosl.org hardy/main Sources                
Hit http://ubuntu.osuosl.org hardy/universe Sources            
Hit http://ubuntu.osuosl.org hardy/restricted Sources          
Hit http://ubuntu.osuosl.org hardy/multiverse Sources          
Hit http://ubuntu.osuosl.org hardy-security/main Packages      
Hit http://ubuntu.osuosl.org hardy-security/universe Packages  
Hit http://ubuntu.osuosl.org hardy-security/restricted Packages
Hit http://ubuntu.osuosl.org hardy-security/multiverse Packages
Hit http://ubuntu.osuosl.org hardy-security/main Sources       
Hit http://ubuntu.osuosl.org hardy-security/universe Sources   
Hit http://ubuntu.osuosl.org hardy-security/restricted Sources                 
Hit http://ubuntu.osuosl.org hardy-security/multiverse Sources                 
Hit http://ubuntu.osuosl.org hardy-updates/universe Packages                   
Hit http://ubuntu.osuosl.org hardy-updates/main Packages                       
Hit http://ubuntu.osuosl.org hardy-updates/restricted Packages                 
Hit http://ubuntu.osuosl.org hardy-updates/multiverse Packages                 
Hit http://ubuntu.osuosl.org hardy-updates/universe Sources                    
Hit http://ubuntu.osuosl.org hardy-updates/main Sources                        
Hit http://ubuntu.osuosl.org hardy-updates/restricted Sources                  
Hit http://ubuntu.osuosl.org hardy-updates/multiverse Sources                  
Hit http://ubuntu.osuosl.org hardy-proposed/universe Packages                  
Hit http://ubuntu.osuosl.org hardy-proposed/main Packages                      
Hit http://ubuntu.osuosl.org hardy-proposed/restricted Packages                
Hit http://ubuntu.osuosl.org hardy-proposed/multiverse Packages                
Hit http://ubuntu.osuosl.org hardy-proposed/universe Sources                   
Hit http://ubuntu.osuosl.org hardy-proposed/main Sources                       
Hit http://ubuntu.osuosl.org hardy-proposed/restricted Sources                 
Hit http://ubuntu.osuosl.org hardy-proposed/multiverse Sources                 
Hit http://ubuntu.osuosl.org hardy-backports/universe Packages                 
Hit http://ubuntu.osuosl.org hardy-backports/main Packages                     
Hit http://ubuntu.osuosl.org hardy-backports/restricted Packages               
Hit http://ubuntu.osuosl.org hardy-backports/multiverse Packages               
Hit http://ubuntu.osuosl.org hardy-backports/universe Sources                  
Hit http://ubuntu.osuosl.org hardy-backports/main Sources                      
Hit http://ubuntu.osuosl.org hardy-backports/restricted Sources                
Hit http://ubuntu.osuosl.org hardy-backports/multiverse Sources                
Ign http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://archive.canonical.com hardy Release                                 
Ign http://archive.canonical.com hardy/partner Packages                        
Ign http://archive.canonical.com hardy/partner Sources                         
Err http://archive.canonical.com hardy/partner Packages                        
  302 Found
Err http://archive.canonical.com hardy/partner Sources                         
  302 Found
Fetched 28.6kB in 10s (2696B/s)                                                
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz  302 Found

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

**Case 2:** repo added somewhere in the middle of the list of repos

sources.list:
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.osuosl.org/ubuntu/ hardy main universe restricted multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ hardy main universe restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://ppa.launchpad.net/exaile-devel/ubuntu hardy main

deb http://ubuntu.osuosl.org/ubuntu/ hardy-security main universe restricted multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ hardy-security main universe restricted multiverse
deb http://ubuntu.osuosl.org/ubuntu/ hardy-updates universe main restricted multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ hardy-updates universe main restricted multiverse
deb http://ubuntu.osuosl.org/ubuntu/ hardy-proposed universe main restricted multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ hardy-proposed universe main restricted multiverse
deb http://ubuntu.osuosl.org/ubuntu/ hardy-backports universe main restricted multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ hardy-backports universe main restricted multiverse
```

apt-get update output:
```
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://ppa.launchpad.net hardy/main Packages                           
Hit http://ppa.launchpad.net hardy/main Packages                           
Hit http://ubuntu.osuosl.org hardy Release.gpg                             
Ign http://ubuntu.osuosl.org hardy/main Translation-en_US      
Ign http://ubuntu.osuosl.org hardy/universe Translation-en_US  
Ign http://ubuntu.osuosl.org hardy/restricted Translation-en_US
Ign http://ubuntu.osuosl.org hardy/multiverse Translation-en_US
Hit http://ubuntu.osuosl.org hardy-security Release.gpg        
Ign http://ubuntu.osuosl.org hardy-security/main Translation-en_US
Ign http://ubuntu.osuosl.org hardy-security/universe Translation-en_US
Ign http://ubuntu.osuosl.org hardy-security/restricted Translation-en_US
Ign http://ubuntu.osuosl.org hardy-security/multiverse Translation-en_US
Hit http://ubuntu.osuosl.org hardy-updates Release.gpg         
Ign http://ubuntu.osuosl.org hardy-updates/universe Translation-en_US
Ign http://ubuntu.osuosl.org hardy-updates/main Translation-en_US
Ign http://ubuntu.osuosl.org hardy-updates/restricted Translation-en_US
Ign http://ubuntu.osuosl.org hardy-updates/multiverse Translation-en_US
Hit http://ubuntu.osuosl.org hardy-proposed Release.gpg        
Ign http://ubuntu.osuosl.org hardy-proposed/universe Translation-en_US
Ign http://ubuntu.osuosl.org hardy-proposed/main Translation-en_US
Ign http://ubuntu.osuosl.org hardy-proposed/restricted Translation-en_US
Ign http://ubuntu.osuosl.org hardy-proposed/multiverse Translation-en_US
Hit http://ubuntu.osuosl.org hardy-backports Release.gpg       
Ign http://ubuntu.osuosl.org hardy-backports/universe Translation-en_US
Ign http://ubuntu.osuosl.org hardy-backports/main Translation-en_US
Ign http://ubuntu.osuosl.org hardy-backports/restricted Translation-en_US
Ign http://ubuntu.osuosl.org hardy-backports/multiverse Translation-en_US
Hit http://ubuntu.osuosl.org hardy Release                     
Hit http://ubuntu.osuosl.org hardy-security Release            
Hit http://ubuntu.osuosl.org hardy-updates Release             
Hit http://ubuntu.osuosl.org hardy-proposed Release            
Hit http://ubuntu.osuosl.org hardy-backports Release           
Hit http://ubuntu.osuosl.org hardy/main Packages                               
Hit http://ubuntu.osuosl.org hardy/universe Packages                           
Hit http://ubuntu.osuosl.org hardy/restricted Packages         
Hit http://ubuntu.osuosl.org hardy/multiverse Packages         
Hit http://ubuntu.osuosl.org hardy/main Sources                
Hit http://ubuntu.osuosl.org hardy/universe Sources            
Hit http://ubuntu.osuosl.org hardy/restricted Sources          
Hit http://ubuntu.osuosl.org hardy/multiverse Sources          
Hit http://ubuntu.osuosl.org hardy-security/main Packages      
Hit http://ubuntu.osuosl.org hardy-security/universe Packages  
Hit http://ubuntu.osuosl.org hardy-security/restricted Packages
Hit http://ubuntu.osuosl.org hardy-security/multiverse Packages
Hit http://ubuntu.osuosl.org hardy-security/main Sources       
Hit http://ubuntu.osuosl.org hardy-security/universe Sources   
Hit http://ubuntu.osuosl.org hardy-security/restricted Sources 
Hit http://ubuntu.osuosl.org hardy-security/multiverse Sources 
Hit http://ubuntu.osuosl.org hardy-updates/universe Packages   
Hit http://ubuntu.osuosl.org hardy-updates/main Packages       
Hit http://ubuntu.osuosl.org hardy-updates/restricted Packages 
Hit http://ubuntu.osuosl.org hardy-updates/multiverse Packages 
Hit http://ubuntu.osuosl.org hardy-updates/universe Sources    
Hit http://ubuntu.osuosl.org hardy-updates/main Sources        
Hit http://ubuntu.osuosl.org hardy-updates/restricted Sources  
Hit http://ubuntu.osuosl.org hardy-updates/multiverse Sources  
Hit http://ubuntu.osuosl.org hardy-proposed/universe Packages
Hit http://ubuntu.osuosl.org hardy-proposed/main Packages
Hit http://ubuntu.osuosl.org hardy-proposed/restricted Packages
Hit http://ubuntu.osuosl.org hardy-proposed/multiverse Packages
Hit http://ubuntu.osuosl.org hardy-proposed/universe Sources   
Hit http://ubuntu.osuosl.org hardy-proposed/main Sources       
Hit http://ubuntu.osuosl.org hardy-proposed/restricted Sources 
Hit http://ubuntu.osuosl.org hardy-proposed/multiverse Sources 
Hit http://ubuntu.osuosl.org hardy-backports/universe Packages 
Hit http://ubuntu.osuosl.org hardy-backports/main Packages     
Hit http://ubuntu.osuosl.org hardy-backports/restricted Packages
Hit http://ubuntu.osuosl.org hardy-backports/multiverse Packages
Hit http://ubuntu.osuosl.org hardy-backports/universe Sources  
Hit http://ubuntu.osuosl.org hardy-backports/main Sources      
Hit http://ubuntu.osuosl.org hardy-backports/restricted Sources
Hit http://ubuntu.osuosl.org hardy-backports/multiverse Sources
Ign http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://archive.canonical.com hardy Release                                 
Ign http://archive.canonical.com hardy/partner Packages                        
Ign http://archive.canonical.com hardy/partner Sources                         
Err http://archive.canonical.com hardy/partner Packages                        
  302 Found
Err http://archive.canonical.com hardy/partner Sources                         
  302 Found
Fetched 1B in 10s (0B/s)                                                       
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz  302 Found

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

It seems like the error was the same now... Anyway, once I remove the exaile repo, things work fine.

---

### Post by warp99 on 2008-05-01
> EDIT: I forgot to mention I use Gutsy, fresh install, no proxy. 

```
deb http://ppa.launchpad.net/exaile-devel/ubuntu hardy main
```

Well your trying to update from the wrong repository since it says 'hardy' and you have 'gusty'. I would change that first to see if this is the problem. I tried the repository on both my gutsy and hardy installs and updated without any problems.

---

### Post by warp99 on 2008-05-01
This is your error:

> Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
  302 Found
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
  302 Found
Fetched 1B in 10s (0B/s)                                                       
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz)  302 Found

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz)  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

It failed to download the packages.gz files from the canonical partner repositories, not the other one. I would delete all of the repository information in your /var/lib/apt/lists/ directory, then 'sudo apt-get update' to see if this fixes the problem. Just for my own curiosity I did try an update using you sources.list without any errors.

---

### Post by tramir on 2008-05-01
Sorry, I just switched to Hardy, force of habit :) I'm using Hardy, actually, fresh install. 

I know the error reported is "could not download Packages.gz", but as you said, the repo is not down - I can download the file in Firefox. 

Let me explain my problem again: if I don't have the Exaile repo, everything works fine (I tried that already). If I add the Exaile repo, or any other 3rd party repo for that matter (I tried some others too), the OTHER repos don't work. Any idea what could cause that?

---

### Post by tramir on 2008-05-01
OK, this is really stupid. I should file an official complaint to Comcast... So, what happens is that their DNS server is crap and can't find addresses every once in while. Once I added the OpenDNS server, things work perfectly. Darn it. I had this set up before, in Gutsy, but I lost it once I installed Hardy. Sorry for wasting all of your time...

---

### Post by warp99 on 2008-05-01
> **tramir said:**
> OK, this is really stupid. I should file an official complaint to Comcast... So, what happens is that their DNS server is crap and can't find addresses every once in while. Once I added the OpenDNS server, things work perfectly. Darn it. I had this set up before, in Gutsy, but I lost it once I installed Hardy. Sorry for wasting all of your time...

I'm also on Comcast and use OpenDNS because of the same reason, but I set the OpenDNS servers at my router instead of each computer so I wouldn't run into this problem every time I switch machines.

---

### Post by hotstovejer on 2008-05-02
I had this same issue. I deleted the lock file in /var/lib/apt/lists and the partial directory. Recreated the partial directory (sudo mkdir /var/lib/apt/lists/partial) and 50 updates came thru after an apt-get update.

And yes, update-manager was one of the updates. Not shocked. :P

Jeremy

---

