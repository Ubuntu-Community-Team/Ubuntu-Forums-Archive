---
title: "[SOLVED] 403 Forbidden"
date: 2008-07-01
forum: General Help
---

### Post by JohnnyPea on 2008-07-01
Hello,

my internet connection works all fine (Pidgin,xchat,Firefox...) but when I want to download Updates or some repositories it says:

> Failed to fetch ....... 403 Forbidden

I really dont know what to do, please help...

---

### Post by mbsullivan on 2008-07-01
Hi JohnnyPea,

Could you post the contents of your **/etc/apt/sources.list** file?

Mike

---

### Post by JohnnyPea on 2008-07-01
of course I can...I will do anything what can solve my problem ...

> # deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy main restricted
deb-src [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-updates main restricted
deb-src [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy universe
deb-src [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy universe
deb [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-updates universe
deb-src [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy multiverse
deb-src [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy multiverse
deb [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-updates multiverse
deb-src [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://sk.archive.ubuntu.com/ubuntu/](http://sk.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-security main restricted
deb-src [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-security main restricted
deb [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-security universe
deb-src [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-security universe
deb [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-security multiverse
deb-src [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-security multiverse
deb [http://blog.blackdown.de/static/debian/rhythmbox/](http://blog.blackdown.de/static/debian/rhythmbox/) hardy main
deb-src [http://blog.blackdown.de/static/debian/rhythmbox/](http://blog.blackdown.de/static/debian/rhythmbox/) hardy main
deb [http://ubuntu.sh.cvut.cz/](http://ubuntu.sh.cvut.cz/) hardy-backports main universe multiverse restricted
# deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) hardy avant-window-navigator
# deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) hardy avant-window-navigator

---

### Post by mbsullivan on 2008-07-01
Are you in the Czech Republic? There may just be a problem with your local server.

The US servers are working fine right now, if you'd like to give them a try.

Mike

---

### Post by russlar on 2008-07-01
I get 403 Forbidden errors a lot, but mostly when I talk to girls. :confused:

Seriously though, the only one of these that doesn't look normal is 
deb-src [http://blog.blackdown.de/static/debian/rhythmbox/](http://blog.blackdown.de/static/debian/rhythmbox/) hardy main

try commenting it out and see if that clears it up

---

### Post by JohnnyPea on 2008-07-01
the same :(

---

### Post by mbsullivan on 2008-07-01
JohnnyPea,

All of your repositories are based out of the Czech Republic. Those servers are down -- give the site a try.

All you have to do is replace them with other servers that are up (like  [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)), or perhaps wait a while.

If you want an easy way to do this, go ahead and try:

```
sudo -s
cp /etc/apt/sources.list /etc/apt/sources.old.list
sed -e 's/http:\/\/ubuntu.sh.cvut.cz\//http:\/\/us.archive.ubuntu.com\/ubuntu\//g' /etc/apt/sources.list > /etc/apt/sources.list

```

Mike

---

### Post by JohnnyPea on 2008-07-01
I have tried the US one, but no result :(

---

### Post by mbsullivan on 2008-07-01
Can you visit the US site (i.e. in Firefox)?

---

### Post by JohnnyPea on 2008-07-01
yop

---

### Post by mbsullivan on 2008-07-01
Could you print both the new contents of your /etc/apt/sources.list file again, as well as the exact output when you try an update? (i.e. "sudo aptitude update") ???

Mike

---

### Post by damis648 on 2008-07-01
Try System>Administration>Software Sources then click the dropdown list ("Download From") and select Other and click "Select Best Server". Click OK when done and close that (Refreshing the sources!) and see if that works after trying again.

---

### Post by JohnnyPea on 2008-07-01
> Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy Release.gpg                           
Ign [http://blog.blackdown.de](http://blog.blackdown.de) hardy Release.gpg                                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                           
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                
Ign [http://blog.blackdown.de](http://blog.blackdown.de) hardy/main Translation-en_US                       
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/main Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US                
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                  
Ign [http://blog.blackdown.de](http://blog.blackdown.de) hardy Release                                      
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/restricted Translation-en_US          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                               
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                         
Ign [http://blog.blackdown.de](http://blog.blackdown.de) hardy/main Packages                                
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/universe Translation-en_US            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                         
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                          
Ign [http://blog.blackdown.de](http://blog.blackdown.de) hardy/main Sources                                 
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/multiverse Translation-en_US          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                           
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Sources                          
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                         
  403 Forbidden
Err [http://blog.blackdown.de](http://blog.blackdown.de) hardy/main Packages                                
  403 Forbidden
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates Release.gpg                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                       
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                         
  403 Forbidden
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                          
  403 Forbidden
Err [http://blog.blackdown.de](http://blog.blackdown.de) hardy/main Sources                                 
  403 Forbidden
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/main Translation-en_US        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources                            
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Sources                          
  403 Forbidden
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/restricted Translation-en_US  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources                        
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/universe Translation-en_US    
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                           
  403 Forbidden
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/multiverse Translation-en_US  
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                       
  403 Forbidden
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security Release.gpg            
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources                            
  403 Forbidden
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/main Translation-en_US       
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources                        
  403 Forbidden
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/restricted Translation-en_US 
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/universe Translation-en_US
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports Release.gpg
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports/main Translation-en_US
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports/universe Translation-en_US
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy Release   
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates Release
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security Release
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports Release
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/main Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/restricted Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/main Sources
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/restricted Sources
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/universe Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/universe Sources
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/multiverse Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/multiverse Sources
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/main Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/restricted Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/main Sources
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/restricted Sources
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/universe Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/universe Sources
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/multiverse Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/multiverse Sources
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/main Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/restricted Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/main Sources
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/restricted Sources
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/universe Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/universe Sources
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/multiverse Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/multiverse Sources
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports/main Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports/universe Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports/multiverse Packages
Ign [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports/restricted Packages
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/main Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/restricted Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/main Sources
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/restricted Sources
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/universe Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/universe Sources
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/multiverse Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy/multiverse Sources
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/main Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/restricted Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/main Sources
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/restricted Sources
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/universe Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/universe Sources
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/multiverse Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-updates/multiverse Sources
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/main Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/restricted Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/main Sources
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/restricted Sources
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/universe Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/universe Sources
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/multiverse Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-security/multiverse Sources
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports/main Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports/universe Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports/multiverse Packages
  403 Forbidden
Err [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org) hardy-backports/restricted Packages
  403 Forbidden
Reading package lists... Done   

..and it is the same for all the servers :(

---

### Post by mbsullivan on 2008-07-01
I get errors when using  [http://archive.ubuntu-rocks.org](http://archive.ubuntu-rocks.org), too (but 404 errors -- not found).

If I were you, I'd use a larger and more reliable repository, like [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

Where are you located geographically? If a US site works for you, then I would stay away from the smaller ones.

Mike

---

### Post by JohnnyPea on 2008-07-01
> Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                 
Ign [http://blog.blackdown.de](http://blog.blackdown.de) hardy Release.gpg                                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                           
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                
Ign [http://blog.blackdown.de](http://blog.blackdown.de) hardy/main Translation-en_US                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US                
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                  
Ign [http://blog.blackdown.de](http://blog.blackdown.de) hardy Release                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                               
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                         
Ign [http://blog.blackdown.de](http://blog.blackdown.de) hardy/main Packages                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                         
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                          
Ign [http://blog.blackdown.de](http://blog.blackdown.de) hardy/main Sources                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                           
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                         
  403 Forbidden
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Sources                          
Err [http://blog.blackdown.de](http://blog.blackdown.de) hardy/main Packages                                
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                       
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                          
  403 Forbidden
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                         
  403 Forbidden
Err [http://blog.blackdown.de](http://blog.blackdown.de) hardy/main Sources                                 
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources                            
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Sources                          
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US    
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                           
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US        
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                       
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg                        
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources                            
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US             
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources                        
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages   
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources    
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
  403 Forbidden
Reading package lists... Done  

I dont know what that "403" means... all worked for me some time ago, but I have changed my ISP and it doesnt work any more...

---

### Post by mbsullivan on 2008-07-01
403 errors typically occur when the files in a web server do not have permissions that allow them to be read or executed by others.

I don't see how that would happen in this case, perhaps because you did not append the trailing "ubuntu" folder.

Replace [http://archive.ubuntu.com](http://archive.ubuntu.com) with literally "http://us.archive.ubuntu.com/ubuntu/" and try again.

Mike

---

### Post by JohnnyPea on 2008-07-01
ok thank you very much for you patience and your time...

If anybody else has something to say about it please do it...I really need to get this one solved...

---

### Post by avtolle on 2008-07-01
I've been reading about certain ISPs blocking downloads from sites, a recent development connected with verdicts in a few child porn cases here in the U.S. I don't have any idea of whether this is going on for you, but the ISPs have been quite vigilant about this as I understand it. I think the resolution of the problem revolves around the change in ISPs, whether or not related to what I posted above, given the OPs post that everything had been working until a change of ISP occurred.

---

### Post by JohnnyPea on 2008-07-02
I've tried at my home and at work...averywhere the same...omg...do you think so many ISPs are bloking that?

---

