---
title: "Can't update because of &quot;unauthenticated sources&quot;?"
date: 2012-12-30
forum: General Help
---

### Post by CFJensen on 2012-12-30
Hi,

Running my update manager i get the following: 
```
Requires installation of untrusted packages

This requires installing packages from unauthenticated sources.
```and when pressing details:
```
r-base r-base-core r-base-dev r-base-html r-cran-boot r-cran-class r-cran-cluster r-cran-codetools r-cran-foreign r-cran-mass r-cran-matrix r-cran-mgcv r-cran-nlme r-cran-nnet r-cran-rpart r-cran-spatial r-doc-html r-recommended
```If i run ```
sudo apt-get update
``` this is the response:
```
christian@Christians:~$ sudo apt-get update
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal InRelease
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal Release.gpg
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal Release
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main Translation-en_US
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main Translation-en
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted Translation-en_US
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted Translation-en
Ign http://archive.ubuntu.com quantal InRelease                                
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://mirrors.dotsrc.org quantal/ InRelease                               
Ign http://archive.canonical.com quantal InRelease                             
Ign http://ppa.launchpad.net quantal InRelease                                 
Ign http://archive.ubuntu.com quantal-updates InRelease                        
Hit http://extras.ubuntu.com quantal Release.gpg                               
Ign http://archive.ubuntu.com quantal-backports InRelease                      
Hit http://archive.canonical.com quantal Release.gpg                           
Hit http://extras.ubuntu.com quantal Release                                   
Ign http://ppa.launchpad.net quantal InRelease                                 
Get:1 http://mirrors.dotsrc.org quantal/ Release.gpg [490 B]                   
Ign http://archive.ubuntu.com quantal-security InRelease                       
Hit http://mirrors.dotsrc.org quantal/ Release                                 
Hit http://archive.canonical.com quantal Release                               
Hit http://extras.ubuntu.com quantal/main Sources                              
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://archive.ubuntu.com quantal Release.gpg                              
Hit http://mirrors.dotsrc.org quantal/ Sources                                 
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Hit http://archive.ubuntu.com quantal-updates Release.gpg                      
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://mirrors.dotsrc.org quantal/ Packages                                
Hit http://archive.canonical.com quantal/partner Sources                       
Hit http://archive.ubuntu.com quantal-backports Release.gpg                    
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Hit http://archive.ubuntu.com quantal-security Release.gpg                     
Ign http://ppa.launchpad.net quantal Release.gpg                               
Hit http://archive.ubuntu.com quantal Release                                  
Hit http://archive.ubuntu.com quantal-updates Release                          
Ign http://linux.dropbox.com precise InRelease                                 
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://archive.ubuntu.com quantal-backports Release                        
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://archive.ubuntu.com quantal-security Release                         
Hit http://archive.ubuntu.com quantal/restricted Sources                       
Ign http://mirrors.dotsrc.org quantal/ Translation-en_US                       
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://mirrors.dotsrc.org quantal/ Translation-en                          
Hit http://archive.ubuntu.com quantal/main Sources                             
Ign http://ppa.launchpad.net quantal Release                                   
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Hit http://linux.dropbox.com precise Release.gpg                               
Hit http://archive.ubuntu.com quantal/multiverse Sources                       
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://archive.ubuntu.com quantal/universe Sources                         
Hit http://archive.ubuntu.com quantal/main i386 Packages                       
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://linux.dropbox.com precise Release                                   
Hit http://archive.ubuntu.com quantal/restricted i386 Packages                 
Hit http://ppa.launchpad.net quantal/main i386 Packages              
Ign http://archive.canonical.com quantal/partner Translation-en_US   
Hit http://archive.ubuntu.com quantal/universe i386 Packages         
Ign http://archive.canonical.com quantal/partner Translation-en      
Hit http://archive.ubuntu.com quantal/multiverse i386 Packages       
Hit http://archive.ubuntu.com quantal/main Translation-en            
Hit http://linux.dropbox.com precise/main i386 Packages
Hit http://archive.ubuntu.com quantal/multiverse Translation-en
Hit http://archive.ubuntu.com quantal/restricted Translation-en
Hit http://archive.ubuntu.com quantal/universe Translation-en
Hit http://archive.ubuntu.com quantal-updates/restricted Sources
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://archive.ubuntu.com quantal-updates/main Sources
Hit http://archive.ubuntu.com quantal-updates/multiverse Sources
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://archive.ubuntu.com quantal-updates/universe Sources
Hit http://archive.ubuntu.com quantal-updates/main i386 Packages
Hit http://archive.ubuntu.com quantal-updates/restricted i386 Packages
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://archive.ubuntu.com quantal-updates/universe i386 Packages
Hit http://archive.ubuntu.com quantal-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com quantal-updates/main Translation-en    
Hit http://archive.ubuntu.com quantal-updates/multiverse Translation-en
Hit http://archive.ubuntu.com quantal-updates/restricted Translation-en
Hit http://archive.ubuntu.com quantal-updates/universe Translation-en
Hit http://archive.ubuntu.com quantal-backports/main Sources
Hit http://archive.ubuntu.com quantal-backports/restricted Sources
Hit http://archive.ubuntu.com quantal-backports/universe Sources
Hit http://archive.ubuntu.com quantal-backports/multiverse Sources   
Hit http://archive.ubuntu.com quantal-backports/main i386 Packages   
Hit http://archive.ubuntu.com quantal-backports/restricted i386 Packages
Hit http://archive.ubuntu.com quantal-backports/universe i386 Packages
Hit http://archive.ubuntu.com quantal-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com quantal-backports/main Translation-en
Hit http://archive.ubuntu.com quantal-backports/multiverse Translation-en
Hit http://archive.ubuntu.com quantal-backports/restricted Translation-en
Ign http://linux.dropbox.com precise/main Translation-en_US
Hit http://archive.ubuntu.com quantal-backports/universe Translation-en
Hit http://archive.ubuntu.com quantal-security/restricted Sources
Hit http://archive.ubuntu.com quantal-security/main Sources
Hit http://archive.ubuntu.com quantal-security/multiverse Sources
Hit http://archive.ubuntu.com quantal-security/universe Sources
Ign http://linux.dropbox.com precise/main Translation-en
Hit http://archive.ubuntu.com quantal-security/main i386 Packages
Hit http://archive.ubuntu.com quantal-security/restricted i386 Packages
Hit http://archive.ubuntu.com quantal-security/universe i386 Packages
Hit http://archive.ubuntu.com quantal-security/multiverse i386 Packages
Hit http://archive.ubuntu.com quantal-security/main Translation-en
Hit http://archive.ubuntu.com quantal-security/multiverse Translation-en
Hit http://archive.ubuntu.com quantal-security/restricted Translation-en
Hit http://archive.ubuntu.com quantal-security/universe Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://archive.ubuntu.com quantal/main Translation-en_US                   
Ign http://archive.ubuntu.com quantal/multiverse Translation-en_US             
Ign http://archive.ubuntu.com quantal/restricted Translation-en_US             
Ign http://archive.ubuntu.com quantal/universe Translation-en_US               
Ign http://archive.ubuntu.com quantal-updates/main Translation-en_US           
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-en_US     
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en_US     
Ign http://archive.ubuntu.com quantal-updates/universe Translation-en_US       
Ign http://archive.ubuntu.com quantal-backports/main Translation-en_US         
Ign http://archive.ubuntu.com quantal-backports/multiverse Translation-en_US   
Ign http://archive.ubuntu.com quantal-backports/restricted Translation-en_US   
Ign http://archive.ubuntu.com quantal-backports/universe Translation-en_US     
Ign http://archive.ubuntu.com quantal-security/main Translation-en_US          
Ign http://archive.ubuntu.com quantal-security/multiverse Translation-en_US    
Ign http://archive.ubuntu.com quantal-security/restricted Translation-en_US    
Ign http://archive.ubuntu.com quantal-security/universe Translation-en_US      
Fetched 490 B in 6s (70 B/s)                                                   
W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://ppa.launchpad.net/cooperjona/stormcloud/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/cooperjona/stormcloud/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


```Any ideas on how to fix my problem would be very much appreciated!
Thank you!

---

### Post by ibjsb4 on 2012-12-30
For starters, uncheck CDrom in software sources and update.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by ibjsb4 on 2012-12-30
The PPA cooperjona/stormcloud no longer seems to be available.  The only thing I am finding is a tarball.

[https://launchpad.net/stormcloud/+download](https://launchpad.net/stormcloud/+download)

So I would just uncheck it for now in software sourses.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

And try another update

---

### Post by Kirus on 2013-01-03
I had the same problem using update manager.
After finding this post, I also tried "sudo apt-get update" to see what I  would get. 
Right after that I decided to try "sudo apt-get upgrade" (gave up using update manager), and it worked for me.  :)
Very weird right? Would this work there for you too?

Cheers

---

