---
title: "Updating Problems (plus a couple more (that may be possibly related)"
date: 2013-02-13
forum: General Help
---

### Post by headcheese3 on 2013-02-13
Hello fellow forum lurkers,

I am currently running Ubuntu 12.04 and I seem to be having problems updating and various other problems that my stem from the updating one (I'm not sure). So, I'm getting an error when I try to update, I use the Update Manager, get an error, so I go to the Terminal, update there, and get the same answer. It says that the package lists or status file could not be parsed or opened. I've also tried disabling some of the repos that I know I don't use and changing the server location to the Main Server, but nothing has changed, with the exception of it returning errors for less repos.

Now, the other problem, I can't seem to run Ubuntu Software Center. Whenever I run it, it just sits there loading for about a minute, then crashes. After it crashes, if I have Chromium up, it crashes, and all my other programs either lag terribly or crash themselves. 

Could somebody help me get to the bottom of this?

Many thanks,
headcheeese3

P.S. My current solution has been to avoid updating or opening the Software Center.

---

### Post by plucky on 2013-02-13
> **headcheese3 said:**
> Hello fellow forum lurkers,

I am currently running Ubuntu 12.04 and I seem to be having problems updating and various other problems that my stem from the updating one (I'm not sure). So, I'm getting an error when I try to update, I use the Update Manager, get an error, so I go to the Terminal, update there, and get the same answer. It says that the package lists or status file could not be parsed or opened. I've also tried disabling some of the repos that I know I don't use and changing the server location to the Main Server, but nothing has changed, with the exception of it returning errors for less repos.

Now, the other problem, I can't seem to run Ubuntu Software Center. Whenever I run it, it just sits there loading for about a minute, then crashes. After it crashes, if I have Chromium up, it crashes, and all my other programs either lag terribly or crash themselves. 

Could somebody help me get to the bottom of this?

Many thanks,
headcheeese3

P.S. My current solution has been to avoid updating or opening the Software Center.

Open a terminal and run ```
sudo apt-get update
``` and cut and paste all of the output to the forum between [noparse] ```
 Your Text
```[/noparse] blocks.

We need to know the exact wording of the error so we can give the correct answer.

Good Luck

---

### Post by headcheese3 on 2013-02-13
Okay! Here it is. 
Error: ```
Reading package lists... Error!
W: GPG error: http://download.opensuse.org ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31046AC4BEF2A6F4
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

```

Everything: ```
 Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                      
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Get:3 http://dl.google.com stable Release [1,338 B]                            
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://extras.ubuntu.com precise InRelease                                 
Get:4 http://dl.google.com stable Release [1,347 B]                            
Ign http://archive.canonical.com precise InRelease                             
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release                                   
Get:5 http://dl.google.com stable/main amd64 Packages [469 B]                  
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise/main Sources                              
Get:6 http://dl.google.com stable/main i386 Packages [464 B]                   
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://download.opensuse.org ./ InRelease                                  
Hit http://archive.canonical.com precise/partner amd64 Packages                
Ign http://archive.ubuntu.com precise-updates InRelease                        
Get:7 http://dl.google.com stable/main amd64 Packages [777 B]                  
Get:8 http://download.opensuse.org ./ Release.gpg [189 B]                      
Get:9 http://dl.google.com stable/main i386 Packages [772 B]                   
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://download.opensuse.org ./ Release                                    
Ign http://download.opensuse.org ./ Release                                    
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://archive.ubuntu.com precise-backports InRelease                      
Ign http://archive.canonical.com precise/partner TranslationIndex              
Ign http://download.opensuse.org ./ Sources/DiffIndex                          
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://archive.ubuntu.com precise-security InRelease                       
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://download.opensuse.org ./ Packages/DiffIndex                         
Hit http://archive.ubuntu.com precise Release.gpg                              
Ign http://ppa.launchpad.net precise InRelease                                 
Get:10 http://archive.ubuntu.com precise-updates Release.gpg [198 B]           
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:11 http://archive.ubuntu.com precise-backports Release.gpg [198 B]         
Get:12 http://archive.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.ubuntu.com precise Release                                  
Hit http://ppa.launchpad.net precise Release                                   
Get:13 http://archive.ubuntu.com precise-updates Release [49.6 kB]             
Hit http://ppa.launchpad.net precise Release                                   
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit http://ppa.launchpad.net precise/main Sources                              
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Ign http://archive.canonical.com precise/partner Translation-en
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources         
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Get:14 http://archive.ubuntu.com precise-backports Release [49.6 kB]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:15 http://archive.ubuntu.com precise-security Release [49.6 kB]            
Err http://archive.ubuntu.com precise-security Release                         
  
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://download.opensuse.org ./ Sources                           
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://download.opensuse.org ./ Packages                                   
Hit http://archive.ubuntu.com precise/universe Sources                       
Hit http://archive.ubuntu.com precise/multiverse Sources                       
Ign http://download.opensuse.org ./ Translation-en_US                          
Ign http://download.opensuse.org ./ Translation-en
Hit http://archive.ubuntu.com precise/main amd64 Packages
Hit http://archive.ubuntu.com precise/restricted amd64 Packages
Hit http://archive.ubuntu.com precise/universe amd64 Packages                
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages              
Hit http://archive.ubuntu.com precise/main i386 Packages                     
Hit http://archive.ubuntu.com precise/restricted i386 Packages               
Hit http://archive.ubuntu.com precise/universe i386 Packages                 
Ign http://ppa.launchpad.net precise/main Translation-en_US                  
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Get:16 http://archive.ubuntu.com precise-updates/main Sources [367 kB]         
Get:17 http://archive.ubuntu.com precise-updates/restricted Sources [5,135 B]  
Get:18 http://archive.ubuntu.com precise-updates/universe Sources [78.6 kB]    
Get:19 http://archive.ubuntu.com precise-updates/multiverse Sources [4,726 B]  
Get:20 http://archive.ubuntu.com precise-updates/main amd64 Packages [574 kB]  
Get:21 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [9,565 B]
Get:22 http://archive.ubuntu.com precise-updates/universe amd64 Packages [180 kB]
Get:23 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [9,435 B]
Get:24 http://archive.ubuntu.com precise-updates/main i386 Packages [584 kB]   
Get:25 http://archive.ubuntu.com precise-updates/restricted i386 Packages [9,503 B]                                                                   
Get:26 http://archive.ubuntu.com precise-updates/universe i386 Packages [181 kB]                                                                      
Get:27 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]                                                                   
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex                                                                                   
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                             
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex                                                                             
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex                                                                               
Get:28 http://archive.ubuntu.com precise-backports/main Sources [2,422 B]                                                                             
Get:29 http://archive.ubuntu.com precise-backports/restricted Sources [14 B]                                                                          
Get:30 http://archive.ubuntu.com precise-backports/universe Sources [21.8 kB]                                                                         
Get:31 http://archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]                                                                       
Get:32 http://archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]                                                                      
Get:33 http://archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]                                                                   
Get:34 http://archive.ubuntu.com precise-backports/universe amd64 Packages [22.3 kB]                                                                  
Get:35 http://archive.ubuntu.com precise-backports/multiverse amd64 Packages [2,489 B]                                                                
Get:36 http://archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]                                                                       
Get:37 http://archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                                                                    
Get:38 http://archive.ubuntu.com precise-backports/universe i386 Packages [22.4 kB]                                                                   
Get:39 http://archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]                                                                 
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex                                                                                 
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex                                                                           
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex                                                                           
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex                                                                             
Hit http://archive.ubuntu.com precise/main Translation-en                                                                                             
Hit http://archive.ubuntu.com precise/multiverse Translation-en                                                                                       
Hit http://archive.ubuntu.com precise/restricted Translation-en                                                                                       
Hit http://archive.ubuntu.com precise/universe Translation-en                                                                                         
Hit http://archive.ubuntu.com precise-updates/main Translation-en                                                                                     
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en                                                                               
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en                                                                               
Hit http://archive.ubuntu.com precise-updates/universe Translation-en                                                                                 
Hit http://archive.ubuntu.com precise-backports/main Translation-en                                                                                   
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en                                                                             
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en                                                                             
Hit http://archive.ubuntu.com precise-backports/universe Translation-en                                                                               
Fetched 2,247 kB in 26s (85.3 kB/s)                                                                                                                   
Reading package lists... Error!
W: GPG error: http://download.opensuse.org ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31046AC4BEF2A6F4
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

```

---

### Post by Bufeu on 2013-02-13
Please post the output of ```
cat /etc/apt/sources.list
```

---

### Post by headcheese3 on 2013-02-14
Here it is: 
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://archive.getdeb.net/ubuntu oneiric-getdeb games # disabled on upgrade to precise
# deb-src http://archive.getdeb.net/ubuntu oneiric-getdeb games # disabled on upgrade to precise
# deb http://archive.getdeb.net/ubuntu oneiric-getdeb games
# deb-src http://archive.getdeb.net/ubuntu oneiric-getdeb games
# deb http://archive.getdeb.net/ubuntu/ precise-getdeb games
deb http://download.opensuse.org/repositories/home:/JanSimek/xUbuntu_12.04/ ./
deb-src http://download.opensuse.org/repositories/home:/JanSimek/xUbuntu_12.04/ ./
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main 
```

---

### Post by plucky on 2013-02-14
> W: GPG error: [http://download.opensuse.org](http://download.opensuse.org) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31046AC4BEF2A6F4


Try removing that repository from your sources.list

Not a good idea to mix repositories from different distros.


> W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)

For this error,open a terminal and run ```
sudo rm /var/lib/apt/lists/* -vf
``` then run ```
sudo apt-get update
``` and see if you still get the same error.


Good Luck

---

### Post by skeptical4life on 2013-02-14
error
W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by plucky on 2013-02-14
> W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs


Please do not hi-jack someone else's thread as your problem is completely different.

You just need to disable ```
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
``` in your Sources.list.

Good Luck

---

### Post by schragge on 2013-02-14
> **plucky said:**
> Not a good idea to mix repositories from different distros.AFAICS, it's someone's private repository for Ubuntu 12.04 hosted on *download.opensuse.org* akin to Ubuntu's PPA. But OP needs to import the GPG key for the repository as described [there]("http://www.etlegacy.com/projects/etlegacy/wiki/Ubuntu_1204").

---

### Post by headcheese3 on 2013-02-15
Well, seeing as I haven't played Enemy Territory in months, I'll just delete it.

[EDIT] I want to delete this post, but don't know how to.

---

### Post by headcheese3 on 2013-02-15
> AFAICS, it's someone's private repository for Ubuntu 12.04 hosted on download.opensuse.org akin to Ubuntu's PPA. But OP needs to import the GPG key for the repository as described there.
Well, seeing as I haven't played Enemy Territory in months, I'll just delete it.

---

### Post by headcheese3 on 2013-02-15
Hey. I deleted that package and got an error. Should I just delete the package? It's for oneiric, so I shouldn't need it now. ```
E: GPG error: http://archive.getdeb.net precise-getdeb Release: The following signatures were invalid: NODATA 1 NODATA 2 
```

---

### Post by schragge on 2013-02-15
How is it for oneiric if it says *precise-getdeb* in the error message?

---

### Post by headcheese3 on 2013-02-16
> **schragge said:**
> How is it for oneiric if it says *precise-getdeb* in the error message?
Woops, there's a couple oneiric getdeb packages that I took out of the update list, and I must have immediately assumed that it was one of the oneiric packages

---

### Post by headcheese3 on 2013-02-18
Well, I went ahead and changed the sources.list file in etc/apt to sources.list.back and then opened Software Sources and selected the sources that I wanted. I then attempted update from Terminal and got this error. 

E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

Also, Software Center still won't run.

---

### Post by Gangwolff on 2013-06-20
I had this problem and used the Code you posted and it fixed my problem. Thank you!!!!!


sudo rm /var/lib/apt/lists/* -vf

Reading package lists... Error! 

 E: Encountered a section with no Package: header 
 E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en 
 E: The package lists or status file could not be parsed or opened. 
 gangwolff@gangwolff-TOSHIBA-NB305:~$ sudo apt-get dist-upgrade 
 Reading package lists... Error! 
 E: Encountered a section with no Package: header 
 E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en 

 E: The package lists or status file could not be parsed or opened.

---

