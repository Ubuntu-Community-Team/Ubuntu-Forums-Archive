---
title: "Repository not found? Problem Installing NixNote (Nevernote, Evernote client)"
date: 2021-11-16
forum: General Help
---

### Post by webmanoffesto on 2021-11-16
I'm trying to install Nevernote / Nixnote and I'm getting errors I don't understand. "Repository not found?"

```

$ sudo add-apt-repository ppa:vincent-c/nevernote
[sudo] password for tom: 
Sorry, try again.
[sudo] password for tom: 
Sorry, try again.
[sudo] password for tom: 
Cannot add PPA: 'ppa:~vincent-c/ubuntu/nevernote'.
The user named '~vincent-c' has no PPA named 'ubuntu/nevernote'
Please choose from the following available PPAs:
 * 'conky':  Conky
 * 'ponysay':  Ponysay
 * 'ppa':  ppa
 * 'vincents-sandbox':  vincents-sandbox
 * 'wesnoth':  Wesnoth
tom@tom-hplaptop17cn0xxx:~$ sudo add-apt-repository ppa:nixnote/nixnote2-daily
 NixNote2 binaries built from the code at https://github.com/baumgarr/nixnote2. Project is published under OSI Approved GPLv2 license.

**As the original maintainer is not available now, this DOEN'T get any updates. But you can use it to install the original v.2.0.2 + minor few changes **

Check out How to Use this PPA at https://github.com/artmg/nixnote2-packaging/wiki/How-to-use-the-PPAs - you'll also find details about how the PPA was put together in that same wiki.
 More info: https://launchpad.net/~nixnote/+archive/ubuntu/nixnote2-daily
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease
Ign:2 http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu focal InRelease      
Hit:3 http://security.ubuntu.com/ubuntu focal-security InRelease             
Hit:4 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease            
Hit:5 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease          
Ign:6 http://ppa.launchpad.net/nixnote/nixnote2-daily/ubuntu focal InRelease 
Hit:7 https://apt.spideroak.com/ubuntu release InRelease                     
Err:8 http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu focal Release        
  404  Not Found [IP: 91.189.95.85 80]
Err:9 http://ppa.launchpad.net/nixnote/nixnote2-daily/ubuntu focal Release
  404  Not Found [IP: 91.189.95.85 80]
Reading package lists... Done                      
E: The repository 'http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/nixnote/nixnote2-daily/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
tom@tom-hplaptop17cn0xxx:~$ sudo apt update && sudo apt install nixnote2
Hit:1 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu focal InRelease                    
Hit:3 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease            
Hit:4 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease          
Ign:5 http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu focal InRelease      
Hit:6 https://apt.spideroak.com/ubuntu release InRelease                     
Ign:7 http://ppa.launchpad.net/nixnote/nixnote2-daily/ubuntu focal InRelease
Err:8 http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu focal Release
  404  Not Found [IP: 91.189.95.85 80]
Err:9 http://ppa.launchpad.net/nixnote/nixnote2-daily/ubuntu focal Release
  404  Not Found [IP: 91.189.95.85 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/nixnote/nixnote2-daily/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
tom@tom-hplaptop17cn0xxx:~$ ^C
tom@tom-hplaptop17cn0xxx:~$ sudo add-apt-repository ppa:nixnote/nixnote2-stable                                                                                                        
 NixNote v2.1+ builds from https://github.com/robert7/nixnote2                                                                                                                         
This will contains builds considered "stable".                                                                                                                                         
                                                                                                                                                                                       
Available packages:                                                                                                                                                                    
* nixnote2 - NixNote v2.1 - more info: https://github.com/robert7/nixnote2/wiki/Getting-started                                                                                        
* nixnote2-tidy - Build of original code from https://github.com/htacg/tidy-html5 with tag 5.6.0 with simplified packagingfor nixnote2                                                 
 More info: https://launchpad.net/~nixnote/+archive/ubuntu/nixnote2-stable                                                                                                             
Press [ENTER] to continue or Ctrl-c to cancel adding it.                                                                                                                               
                                                                                                                                                                                       
Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease                                                                                                                              
Hit:2 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease                                                                                                                      
Hit:3 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease                                                                                                                    
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease                                                                                                                       
Ign:5 http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu focal InRelease                                                                                                                
Hit:6 https://apt.spideroak.com/ubuntu release InRelease                                                                                                                               
Ign:7 http://ppa.launchpad.net/nixnote/nixnote2-daily/ubuntu focal InRelease                                                                                                           
Get:8 http://ppa.launchpad.net/nixnote/nixnote2-stable/ubuntu focal InRelease [18.1 kB]                                                                                                
Err:9 http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu focal Release
  404  Not Found [IP: 91.189.95.85 80]
Err:10 http://ppa.launchpad.net/nixnote/nixnote2-daily/ubuntu focal Release
  404  Not Found [IP: 91.189.95.85 80]
Get:11 http://ppa.launchpad.net/nixnote/nixnote2-stable/ubuntu focal/main amd64 Packages [884 B]
Get:12 http://ppa.launchpad.net/nixnote/nixnote2-stable/ubuntu focal/main Translation-en [788 B]
Reading package lists... Done                       
E: The repository 'http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/nixnote/nixnote2-daily/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
tom@tom-hplaptop17cn0xxx:~$ sudo apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease                                                                                        
Hit:3 http://security.ubuntu.com/ubuntu focal-security InRelease                                                                                         
Hit:4 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease                                                         
Ign:5 http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu focal InRelease                                                     
Hit:6 https://apt.spideroak.com/ubuntu release InRelease                                             
Ign:7 http://ppa.launchpad.net/nixnote/nixnote2-daily/ubuntu focal InRelease                         
Hit:8 http://ppa.launchpad.net/nixnote/nixnote2-stable/ubuntu focal InRelease
Err:9 http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu focal Release
  404  Not Found [IP: 91.189.95.85 80]
Err:10 http://ppa.launchpad.net/nixnote/nixnote2-daily/ubuntu focal Release
  404  Not Found [IP: 91.189.95.85 80]
Reading package lists... Done                      
E: The repository 'http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/nixnote/nixnote2-daily/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
tom@tom-hplaptop17cn0xxx:~$ sudo apt-get install nixnote2-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nixnote2-stable
tom@tom-hplaptop17cn0xxx:~$ 


```

---

### Post by tea for one on 2021-11-16
```
apt search nixnote
```
```
Sorting... Done
Full Text Search... Done
nixnote2/focal 2.1.5+dfsg1-1build1 amd64
  Open Source Evernote client

```

Looks like nixnote2 is in the repo - any good?

---

### Post by deadflowr on 2021-11-16
You need to disable/remove both the clipgrab and nixnote2 PPAs.
Neither has an archive for Ubuntu 20.04/focal.

---

### Post by webmanoffesto on 2021-11-16
> **deadflowr said:**
> You need to disable/remove both the clipgrab and nixnote2 PPAs.
Neither has an archive for Ubuntu 20.04/focal.

I managed to install Nixnote2 on Ubuntu 20. Is there something about that which will create problems?

---

### Post by tea for one on 2021-11-16
These PPAs do not have an application for Ubuntu 20.04 and you will constantly see the [COLOR="#0000FF"]does not have a Release file[/COLOR] messages.

I would find this somewhat irritating and would fix it by removing the PPAs.

Also, if the PPAs are still active, unbeknown to you, the developer might add a supported version and you could download it accidentally.

Two versions might create a bit of conflict and lead to more complicated remedies.

---

