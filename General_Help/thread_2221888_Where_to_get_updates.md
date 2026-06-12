---
title: "Where to get updates ?"
date: 2014-05-04
forum: General Help
---

### Post by sarahfoxnz on 2014-05-04
hello. when going to my update manager - it says the archives / updates are over 200+ days old (see image)

Question 1 :- how do i know WHERE my computer is checking the archives / updates from ?

Question 2 :- Where can i find a more up-to-date place to get updates from ?

Question 3 :- how do I change the settings to get the updates from new location  ??

(I have frequent updates top my PC - so if i'm updating every day / every few days - why does it say over 200+ days ago ?)

[ATTACH=CONFIG]252833[/ATTACH]

---

### Post by bapoumba on 2014-05-04
Which Ubuntu release are you on ?
You can check the Software Sources to see which repos you are using.

Please also post the output to :
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

---

### Post by sarahfoxnz on 2014-05-04
[ATTACH=CONFIG]252834[/ATTACH]


Is this whaty is needed ?

$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-security main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-security main restricted
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-security universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-security universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-security multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
sarah@LinuxPC:~$ ls /etc/apt/sources.list.d
dropbox.list             google-earth.list.save
dropbox.list.save        google.list
google-chrome.list       google.list.save
google-chrome.list.save  otto-kesselgulasch-gimp-precise.list
google-earth.list        otto-kesselgulasch-gimp-precise.list.save
sarah@LinuxPC:~$ 


PS are my imges Ok ? seem a bit small.

---

### Post by bapoumba on 2014-05-04
OK thanks.

Please post the output to 
```
sudo apt-get update
sudo apt-get upgrade
```
That will refresh your repos listing and upgrade your current packages to the newest versions for Precise.

---

### Post by buzzingrobot on 2014-05-04
> **sarahfoxnz said:**
> 
Question 1 :- how do i know WHERE my computer is checking the archives / updates from ?



The servers -- aka repositories -- where your software updates are drawn from are listed in sources.list.

From the listing in your sources.list file,  the server at 'http:// nz.archive.ubuntu.com" is used most often.  So, it's the server Canonical maintains for New Zealand.

When you run "sudo apt-get update" in a terminal, or refresh the Update Manager, what's happening is that a list of packages installed on your machines is compared with a list of software maintained on that server to determine if newer version are available.  The actual upgrade, either via the Update Manager of with "sudo apt-get upgrade" downloads and install the updates.

---

### Post by sarahfoxnz on 2014-05-05
> **bapoumba said:**
> OK thanks.

Please post the output to 
```
sudo apt-get update
sudo apt-get upgrade
```
That will refresh your repos listing and upgrade your current packages to the newest versions for Precise.

Hello. I've donbe the above two commands & there are a few errors reported.

> 
sarah@LinuxPC:~$ sudo apt-get update
[sudo] password for sarah: 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise Release.gpg [198 B]                 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security Release.gpg                  
Get:2 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg [489 B]                     
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise Release                               
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates Release                       
Get:4 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release [2,603 B]                       
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise Release                               
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security Release                      
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:6 [http://linux.dropbox.com](http://linux.dropbox.com) precise/main amd64 Packages [1,143 B]           
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main Sources/DiffIndex                
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted Sources/DiffIndex          
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe Sources/DiffIndex            
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse Sources/DiffIndex          
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main amd64 Packages/DiffIndex         
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted amd64 Packages/DiffIndex   
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe amd64 Packages/DiffIndex     
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse amd64 Packages/DiffIndex   
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main i386 Packages/DiffIndex          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
  
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex      
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex    
Get:7 [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages [1,143 B]            
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                     
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/restricted Sources            
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse Sources            
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages/DiffIndex                  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/main amd64 Packages           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/restricted amd64 Packages     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Ign [http://dl.google.com](http://dl.google.com) stable/main i386 Packages/DiffIndex                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/universe amd64 Packages       
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse amd64 Packages     
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/main Sources                 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/restricted Sources           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/universe Sources             
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/multiverse Sources           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/main amd64 Packages          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/restricted amd64 Packages    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/universe amd64 Packages      
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/multiverse amd64 Packages    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/main i386 Packages           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/restricted i386 Packages     
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/universe i386 Packages       
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/multiverse i386 Packages     
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/main TranslationIndex        
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/multiverse TranslationIndex  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/restricted TranslationIndex  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/universe TranslationIndex    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main Sources                          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe Sources                      
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse Translation-en             
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_NZ                    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/main Translation-en          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/multiverse Translation-en    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                       
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/restricted Translation-en    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-security/universe Translation-en      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_NZ                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_NZ
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_NZ
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_NZ
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_NZ
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Fetched 5,846 B in 5s (1,004 B/s)
Reading package lists... Done
W: GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
sarah@LinuxPC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sarah@LinuxPC:~$ 





Update:  ive been to my update manager & it says the things are 246= days old (forget exact wording).    

i am not worried or anything, but - if i use manager (a few days ago) & download 100+ MB of updates - it SJOULD say  the updates / archives or watever wee last updated 3 days ago (or something small) - within the time I last updated & todays / now date.  shouldn't it ?

& If it HASN'T been updated  since 246= days ago - my computer should in theory have all the updates available & no more is needed.   i'm not concerned - just curious.  it says one thing, but doing another.

---

