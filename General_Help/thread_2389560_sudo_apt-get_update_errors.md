---
title: "sudo apt-get update errors"
date: 2018-04-18
forum: General Help
---

### Post by dappcode on 2018-04-18
```
 ibnukholil@ibnukholil-Aspire-Z3-451 &#57520; ~ &#57520; sudo apt-get update                                                      &#57522; &#10004; &#57523; &#9881; &#57522; 3032 &#57522; 22:01:01 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                                                                                    
Hit:3 http://packages.microsoft.com/repos/vscode stable InRelease                                                                             
Hit:6 http://id.archive.ubuntu.com/ubuntu xenial InRelease                                                                                    
Hit:7 http://id.archive.ubuntu.com/ubuntu xenial-updates InRelease                             
Hit:8 http://security.ubuntu.com/ubuntu xenial-security InRelease                              
Hit:9 http://ppa.launchpad.net/atareao/atareao/ubuntu xenial InRelease                         
Hit:10 http://ppa.launchpad.net/atareao/telegram/ubuntu xenial InRelease                                       
Hit:11 http://id.archive.ubuntu.com/ubuntu xenial-backports InRelease                                                                     
Ign:12 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial InRelease                                                            
Ign:13 http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.04  InRelease                                            
Hit:14 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu xenial InRelease                                                               
Ign:15 http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.04  Release            
Ign:16 http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.04  Packages           
Hit:17 http://ppa.launchpad.net/morphis/anbox-support/ubuntu xenial InRelease
Ign:16 http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.04  Packages
Ign:4 https://attic.owncloud.com/org/download/repositories/stable/Ubuntu_14.04  InRelease
Ign:16 http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.04  Packages            
Get:18 http://download.owncloud.org/download/repositories/stable/Ubuntu_14.04  Release [965 B]      
Ign:16 http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.04  Packages                
Hit:19 http://ppa.launchpad.net/noobslab/apps/ubuntu xenial InRelease     
Get:20 http://download.owncloud.org/download/repositories/stable/Ubuntu_14.04  Release.gpg [481 B]                        ^[[C
Ign:16 http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.04  Packages                                              
Err:16 http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.04  Packages            
  404  Not Found [IP: 195.135.221.134 80]
Hit:21 http://ppa.launchpad.net/noobslab/macbuntu/ubuntu xenial InRelease     
Hit:22 http://ppa.launchpad.net/noobslab/themes/ubuntu xenial InRelease        
Hit:23 http://ppa.launchpad.net/numix/ppa/ubuntu xenial InRelease              
Ign:20 http://download.owncloud.org/download/repositories/stable/Ubuntu_14.04  Release.gpg
Hit:24 http://ppa.launchpad.net/ondrej/php/ubuntu xenial InRelease             
Hit:25 http://ppa.launchpad.net/phalcon/stable/ubuntu xenial InRelease                                                                        
Hit:26 http://ppa.launchpad.net/pi-rho/dev/ubuntu xenial InRelease                                                                            
Hit:27 http://ppa.launchpad.net/serge-rider/dbeaver-ce/ubuntu xenial InRelease                                                                
Hit:28 http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu xenial InRelease                                                            
Hit:29 http://ppa.launchpad.net/webupd8team/atom/ubuntu xenial InRelease                                                                      
Hit:30 http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu xenial InRelease                                                            
Hit:31 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease                                                                      
Ign:32 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial Release                                                                   
Ign:33 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 Packages                                                       
Ign:34 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main i386 Packages                                                        
Ign:35 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main all Packages                                                         
Ign:33 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 Packages                                                       
Ign:34 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main i386 Packages
Ign:35 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main all Packages
Ign:33 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 Packages
Ign:34 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main i386 Packages
Ign:35 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main all Packages
Ign:33 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 Packages
Ign:34 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main i386 Packages
Ign:35 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main all Packages
Ign:33 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 Packages
Ign:34 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main i386 Packages
Ign:35 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main all Packages
Err:33 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main amd64 Packages
  404  Not Found
Ign:34 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main i386 Packages
Ign:35 http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial/main all Packages
Fetched 1.446 B in 20s (71 B/s)
Reading package lists... Done
W: The repository 'http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.04  Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://download.owncloud.org/download/repositories/stable/Ubuntu_14.04  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 47AE7F72479BC94B
W: The repository 'http://download.owncloud.org/download/repositories/stable/Ubuntu_14.04  Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.04/Packages  404  Not Found [IP: 195.135.221.134 80]
E: Failed to fetch http://ppa.launchpad.net/colingille/freshlight/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by cruzer001 on 2018-04-18
That's quite the collection you got going on.  You should start by removing everything not in use, followed by everything that's not Xenial.

```
software-properties-gtk
```

[https://www.google.com/search?client=ubuntu&channel=fs&q=remove+ppa&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=remove+ppa&ie=utf-8&oe=utf-8)

---

### Post by howefield on 2018-04-18
Thread moved to the "*General Help*" forum.

---

### Post by ajgreeny on 2018-04-18
You may find it easier tyo simply rename the old /etc/apt/sources.list file as a backup the create a new sources list file using [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) where you can get a clean start, or add certain PPA repositories that you may want.

---

