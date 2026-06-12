---
title: "Updates Failing"
date: 2018-07-10
forum: General Help
---

### Post by ayyyy on 2018-07-10
Hi my updates fail every time (I'am using the terminal). Help is much appreciated. This is what it looks like:

```
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                     
Ign:2 [http://ppa.launchpad.net/hsoft/ppa/ubuntu](http://ppa.launchpad.net/hsoft/ppa/ubuntu) bionic InRelease               
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]   
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]    
Ign:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:6 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable InRelease                         
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:8 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview InRelease                        
Hit:9 [http://ppa.launchpad.net/leaeasy/dde/ubuntu](http://ppa.launchpad.net/leaeasy/dde/ubuntu) bionic InRelease             
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Hit:12 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) bionic InRelease              
Ign:13 [http://ppa.launchpad.net/noobslab/macbuntu/ubuntu](http://ppa.launchpad.net/noobslab/macbuntu/ubuntu) bionic InRelease      
Ign:14 [https://mega.nz/linux/MEGAsync/xUbuntu_18.04](https://mega.nz/linux/MEGAsync/xUbuntu_18.04) ./ InRelease               
Ign:15 [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) bionic InRelease        
Hit:16 [http://ppa.launchpad.net/numix/ppa/ubuntu](http://ppa.launchpad.net/numix/ppa/ubuntu) bionic InRelease              
Get:17 [https://mega.nz/linux/MEGAsync/xUbuntu_18.04](https://mega.nz/linux/MEGAsync/xUbuntu_18.04) ./ Release [951 B]         
Hit:19 [http://ppa.launchpad.net/ricotz/docky/ubuntu](http://ppa.launchpad.net/ricotz/docky/ubuntu) bionic InRelease           
Hit:20 [http://ppa.launchpad.net/snwh/pulp/ubuntu](http://ppa.launchpad.net/snwh/pulp/ubuntu) bionic InRelease              
Hit:21 [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) bionic InRelease
Err:22 [http://ppa.launchpad.net/hsoft/ppa/ubuntu](http://ppa.launchpad.net/hsoft/ppa/ubuntu) bionic Release                
  404  Not Found [IP: 91.189.95.83 80]
Err:23 [http://ppa.launchpad.net/noobslab/macbuntu/ubuntu](http://ppa.launchpad.net/noobslab/macbuntu/ubuntu) bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Err:24 [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) bionic Release          
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/hsoft/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/noobslab/macbuntu/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/noobslab/themes/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by deadflowr on 2018-07-10
Neither the hsoft nor the noobslab/macbuntu and themes PPAs have bionic archives yet, so you'll need to disable those.

---

