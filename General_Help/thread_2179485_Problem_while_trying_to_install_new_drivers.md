---
title: "Problem while trying to install new drivers"
date: 2013-10-08
forum: General Help
---

### Post by pavacic-p on 2013-10-08
```
paulo@DancingPuppy:~$ sudo apt-get remove fglrx* -f
[sudo] password for paulo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx-driver-dev' for regex 'fglrx*'
Note, selecting 'fglrx-pxpress' for regex 'fglrx*'
Note, selecting 'fglrx-updates' for regex 'fglrx*'
Note, selecting 'fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-control' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle-updates' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-glx' for regex 'fglrx*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx*'
Note, selecting 'fglrx-driver' for regex 'fglrx*'
Note, selecting 'fglrx-updates-dev' for regex 'fglrx*'
Note, selecting 'fglrx' for regex 'fglrx*'
Package 'fglrx-glx' is not installed, so not removed
Package 'fglrx-control-qt2' is not installed, so not removed
Package 'xfree86-driver-fglrx-dev' is not installed, so not removed
Package 'xorg-driver-fglrx-dev' is not installed, so not removed
Package 'fglrx-pxpress' is not installed, so not removed
Package 'fglrx' is not installed, so not removed
Package 'fglrx-amdcccle' is not installed, so not removed
Package 'fglrx-amdcccle-updates' is not installed, so not removed
Package 'fglrx-dev' is not installed, so not removed
Package 'fglrx-updates' is not installed, so not removed
Package 'fglrx-updates-dev' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
paulo@DancingPuppy:~$ sudo apt-get update
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy InRelease
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy InRelease                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy Release.gpg                   
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates Release.gpg           
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg                                 
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease                        
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/main Sources                  
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/restricted Sources            
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/universe Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Sources               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                      
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/multiverse Sources            
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/main amd64 Packages           
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/restricted amd64 Packages     
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner amd64 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main amd64 Packages                         
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/universe amd64 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg            
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/multiverse amd64 Packages     
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/main i386 Packages            
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner i386 Packages                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                          
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/restricted i386 Packages      
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release                          
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/multiverse i386 Packages                
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/main Translation-hr                     
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/main Translation-en           
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/multiverse Translation-en               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources                     
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/restricted Translation-en     
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/universe Translation-hr       
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/universe Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources     
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/main Sources          
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/restricted Sources              
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/universe Sources                
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources       
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/main amd64 Packages   
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/restricted amd64 Packages
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/universe amd64 Packages         
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/multiverse amd64 Packages       
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/main i386 Packages    
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources               
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/universe i386 Packages          
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/multiverse i386 Packages
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/main Translation-en   
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-hr_HR     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main amd64 Packages    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-hr_HR            
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/multiverse Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-hr               
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/restricted Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-hr        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted amd64 Packages        
Hit [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/universe Translation-en         
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/main Translation-hr_HR
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/multiverse Translation-hr_HR
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/multiverse Translation-hr
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/restricted Translation-hr_HR
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/restricted Translation-hr
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy/universe Translation-hr_HR
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/main Translation-hr_HR
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/main Translation-hr
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/multiverse Translation-hr_HR
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/multiverse Translation-hr
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/restricted Translation-hr_HR
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/restricted Translation-hr
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/universe Translation-hr_HR
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Ign [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) saucy-updates/universe Translation-hr
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-hr_HR
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-hr
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-hr_HR
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-hr
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-hr_HR
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-hr
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-hr_HR
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-hr
Reading package lists... Done
paulo@DancingPuppy:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/88,2 MB of archives.
After this operation, 261 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 173717 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a13.101-0ubuntu3_amd64.deb) ...
One or more files have been altered since installation.
Uninstall will not be completed. See /etc/ati/fglrx-uninstall.log for details.
dpkg: error processing /var/cache/apt/archives/fglrx_2%3a13.101-0ubuntu3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a13.101-0ubuntu3_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a13.101-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
paulo@DancingPuppy:~$ sudo apt-get install fglrx_updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package fglrx_updates
paulo@DancingPuppy:~$ sudo apt-cache search fglrx
fglrx-pxpress - Tools to enable AMD's PowerXpress
ubuntu-drivers-common - Detect and install additional Ubuntu driver packages
xvba-va-driver - XvBA-based backend for VA API (AMD fglrx implementation)
fglrx - Video driver for the AMD graphics accelerators
fglrx-amdcccle - Catalyst Control Center for the AMD graphics accelerators
fglrx-amdcccle-updates - Catalyst Control Center for the AMD graphics accelerators
fglrx-dev - Video driver for the AMD graphics accelerators (devel files)
fglrx-updates - Video driver for the AMD graphics accelerators
fglrx-updates-dev - Video driver for the AMD graphics accelerators (devel files)
jockey-common - user interface and desktop integration for driver management
jockey-kde - KDE user interface and desktop integration for driver management
paulo@DancingPuppy:~$ ^C
paulo@DancingPuppy:~$ sudo apt-get remove fglrx-amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fglrx-amdcccle
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 12,4 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 173762 files and directories currently installed.)
Removing fglrx-amdcccle ...
dpkg: warning: while removing fglrx-amdcccle, directory '/usr/share/ati' not empty so not removed
dpkg: warning: while removing fglrx-amdcccle, directory '/usr/lib/fglrx' not empty so not removed


```

I had installed AMD 13.10 drivers. Problem appeared when I updated from Ubuntu 13.04 to 13.10 and had to remove drivers for some reason.

---

### Post by truxnor on 2013-10-16
I had this exact same problem, for me I had to manually remove the ati folder, and then I was able to install the fglrx drivers without any issues.

> [COLOR=#333333][FONT=Helvetica Neue][I]sudo rm -R /usr/lib/fglrx
[/I]*sudo rm -R /usr/share/ati*[/FONT][/COLOR]


Either or both of those might work, depending on where yours are installed.

This worked for me, so hopefully it does for you too.

---

