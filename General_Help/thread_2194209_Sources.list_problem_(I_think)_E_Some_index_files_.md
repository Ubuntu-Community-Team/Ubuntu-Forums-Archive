---
title: "Sources.list problem (I think) E: Some index files failed to download. They have been"
date: 2013-12-17
forum: General Help
---

### Post by dreamspy on 2013-12-17
Hi there

This is probably a very common problem, but still I haven't been able to find a solution for this online.  I've tried deleting the contents of /var/lib/apt/lists as suggested on this forum, to no avail. When I run sudo apt-get update (and also sometimes when I try to install a certain package) I get this kind of an error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


Here below is the whole error output... and below that is the ingredients of sources.list.  Anyone?




Error output from "sudo apt-get update":

> Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                                                        
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                                                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                                                                                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                                                                                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security InRelease                                                                                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                                                                                      
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main i386 Packages                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main TranslationIndex                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                                                         
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security Release.gpg                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                             
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty InRelease                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                               
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                                                  
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                               
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                                      
  404  Not Found
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en                                                           
Get:1 [http://linux.dropbox.com](http://linux.dropbox.com) natty Release.gpg [489 B]                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/multiverse TranslationIndex
Get:2 [http://linux.dropbox.com](http://linux.dropbox.com) natty Release [2599 B]                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe TranslationIndex
Get:3 [http://linux.dropbox.com](http://linux.dropbox.com) natty/main i386 Packages [1148 B]     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                         
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty/main TranslationIndex             
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty/main Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe Translation-en
Fetched 4236 B in 3s (1188 B/s)
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-security/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.




contents of sources.list:

> # deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

---

### Post by deadflowr on 2013-12-17
Natty's dead.
Either upgrade your system or change the sources.list to reflect the [old-releases]("http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release").

Preferably, though, you would upgrade.
Just because the packages for natty are available in the old-release repos doesn't mean it is a good thing.
Those package will never be updated and any problems with them will go unfixed, forever.

---

### Post by claracc on 2013-12-17
Also, you have ppas for lucid release (10.04) mixed with repositories for natty.

The sources.list file is a mess and the software cannot be found either the repositories has been moved from the server, either they are for other ubuntu (lucid) and surely they won't fit the dependencies.

As you have been advised, install a supported ubuntu as for example 12.04 wich is LTS release till 2017.

---

