---
title: "Added PPA - but things Changed ???"
date: 2015-04-09
forum: General Help
---

### Post by Rick St. George on 2015-04-09
Recently added PPA for LinPhone from [https://launchpad.net/~linphone/+archive/ubuntu/release](https://launchpad.net/~linphone/+archive/ubuntu/release)
After sudo update, desktop changed a little, and Linphone does not show up under INTERNET. 
Tried to add it back with UBUNTU SOFTWARE CENTER and it crashes and sends an Error Report.

Stumped as to what to do now!  Any suggestions?  Did I corrupt my system?

System: AMD 64bit 8 Core CPU; 16 GB Ram; SSD HD; UbuntuStudio 14.10 Trusty


Thanks,
Rick

---

### Post by Rick St. George on 2015-04-10
If this post is in the wrong place - could someone please move it to the right one.

Thanks
Rick

---

### Post by Bucky Ball on 2015-04-10
*Thread moved to **General Help**.*

Sure! ;)
[I][B]
Installations and Upgrades[/B][/I] section is for installing and upgrading the OS itself.

---

### Post by tjiagoM on 2015-04-10
Please tell us how you added the PPA and what is the content of the error report. This way it will be easy to us to analyse your problem :)

---

### Post by Bucky Ball on 2015-04-10
> **tiago-manuel said:**
> Please tell us how you added the PPA and what is the content of the error report. This way it will be easy to us to analyse your problem :)

How the PPA was added is explained right there on the link provided in the first post. Look under 'Adding this PPA to your system' on the linked page. ;)

If it was added any other way than this I'd be curious to know how myself. :-k

@OP: As tiago-manuel mentions, prior to it sending the error report you can read the details of what it is going to send. Perhaps click 'Details', have a look there and copy/paste the error report here. Might throw some light.

---

### Post by Rick St. George on 2015-04-10
> 
@OP: As tiago-manuel mentions, prior to it sending the error report you can read the details of what it is going to send. Perhaps click 'Details', have a look there and copy/paste the error report here. Might throw some light.

Sorry - wish I had done that!  And yes, it was according to instructions at said link.
I also noticed, "Audacious" audio player disappeared as well. Had to reinstall, but my playlist was still intact.  
<<< Strange >>>

Thanks for any feedback, as to what I can do next as I can't get Linphone to install. Also, Software Update shows "partial install" but seems to do nothing. If I click OK it shows "Computer Up To Date". 

Rick

---

### Post by Bucky Ball on 2015-04-10
Try this in a terminal:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linphone
```

Please report any and all errors. Rest assured, these commands will NOT upgrade your release to a newer one, just the software you have installed, if it needs to be.

Perhaps some new clues can help us get to the bottom of this ... :-k

---

### Post by Rick St. George on 2015-04-12
> **Bucky Ball said:**
> Try this in a terminal:

Please report any and all errors. Rest assured, these commands will NOT  upgrade your release to a newer one, just the software you have  installed, if it needs to be. Perhaps some new clues can help us get to the bottom of this ... [IMG]http://ubuntuforums.org/images/smilies/eusa_think.gif[/IMG]

THANKS BuckyBall - Here is the Terminal Output ....

> 
stephen@stephen-evo-5723:~$ sudo apt-get autoremove
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linphone-common
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
After this operation, 7,885 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 238071 files and directories currently installed.)
Removing linphone-common (3.7.0-0ubuntu0~ppa2~trusty) ...
stephen@stephen-evo-5723:~$ sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Ign [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender InRelease                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender Release.gpg                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free amd64 Packages        
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free i386 Packages         
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [63.5 kB]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [190 kB]        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [2,564 B] 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [495 kB] 
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                       
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [9,238 B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [485 kB]  
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [9,256 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Ign [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free Translation-en
Fetched 1,256 kB in 3s (373 kB/s)
Reading package lists... Done
stephen@stephen-evo-5723:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libgail-common libgail18 libgtk2.0-0 libgtk2.0-bin
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
stephen@stephen-evo-5723:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  audacious gtk2-engines-pixbuf ubuntustudio-desktop
The following packages will be upgraded:
  libgail-common libgail18 libgtk2.0-0 libgtk2.0-bin
4 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 1,873 kB of archives.
After this operation, 2,193 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libgail-common amd64 2.24.23-0ubuntu1.2 [110 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libgtk2.0-bin amd64 2.24.23-0ubuntu1.2 [9,798 B]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libgail18 amd64 2.24.23-0ubuntu1.2 [14.1 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libgtk2.0-0 amd64 2.24.23-0ubuntu1.2 [1,739 kB]
Fetched 1,873 kB in 2s (858 kB/s)        
(Reading database ... 237960 files and directories currently installed.)
Removing audacious (3.4.3-1) ...
Removing ubuntustudio-desktop (0.126) ...
Removing gtk2-engines-pixbuf:amd64 (2.24.23-0ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
(Reading database ... 237877 files and directories currently installed.)
Preparing to unpack .../libgail-common_2.24.23-0ubuntu1.2_amd64.deb ...
Unpacking libgail-common:amd64 (2.24.23-0ubuntu1.2) over (2.24.23-0ubuntu1.1) ...
Preparing to unpack .../libgtk2.0-bin_2.24.23-0ubuntu1.2_amd64.deb ...
Unpacking libgtk2.0-bin (2.24.23-0ubuntu1.2) over (2.24.23-0ubuntu1.1) ...
Preparing to unpack .../libgail18_2.24.23-0ubuntu1.2_amd64.deb ...
Unpacking libgail18:amd64 (2.24.23-0ubuntu1.2) over (2.24.23-0ubuntu1.1) ...
Preparing to unpack .../libgtk2.0-0_2.24.23-0ubuntu1.2_amd64.deb ...
Unpacking libgtk2.0-0:amd64 (2.24.23-0ubuntu1.2) over (2.24.23-0ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libgtk2.0-0:amd64 (2.24.23-0ubuntu1.2) ...
Setting up libgail18:amd64 (2.24.23-0ubuntu1.2) ...
Setting up libgail-common:amd64 (2.24.23-0ubuntu1.2) ...
Setting up libgtk2.0-bin (2.24.23-0ubuntu1.2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
stephen@stephen-evo-5723:~$ sudo apt-get install linphone
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linphone : Depends: liblinphone6 (>= 3.7.0) but it is not going to be installed
            Depends: linphone-nogtk (= 3.7.0-0ubuntu0~ppa2~trusty) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
stephen@stephen-evo-5723:~$ 


<-----------End Printout ------------->



NOTICE that it removed "Linphone", then it could not complete install, and that it removed "Audacious" and "UbuntuStudio Dekstop"!  
Why?

---

### Post by Rick St. George on 2015-04-12
Note: Found "liblinphone6" in Synaptic Pkg Mgr, but it has a [COLOR=#ff0000]RED ![/COLOR]  and will not allow selection of "Mark for Removal" or "Mark for Reinstallation" or anything else except "Mark for Installation" and "Unmark". 

I also get the following ERROR:

E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the list directory



How do I fix this broken library?

---

### Post by CantankRus on 2015-04-12
Do you still have the ppa you added enabled?

---

### Post by ian-weisser on 2015-04-12
> Depends: linphone-nogtk (= 3.7.0-0ubuntu0~ppa2~trusty) but it is not going to be installed
This looks like a 14.04 package. I don't see a 14.10 version in that PPA, nor any package published after May 2014.
I also don't see some of the required dependencies in that PPA. For example, I don't see a package for liblinphone6. 
I would not use that PPA on a 14.10 system.

I would disable or delete that PPA, then re-try the steps that Bucky Ball recommended in Post #7 of this thread.

Linphone is already in the Ubuntu repositories. Do you really need Linphone from that particular PPA?

---

### Post by Bucky Ball on 2015-04-13
> **ian-weisser said:**
> 

I would disable or delete that PPA, then re-try the steps that Bucky Ball recommended in Post #7 of this thread.

Linphone is already in the Ubuntu repositories. Do you really need Linphone from that particular PPA?

^^^
This.

Kill that PPA then run the commands I gave to autoremove and update/upgrade then install linphone from package manager, Synaptics or Software Centre. Always look there prior to installing third-party repos. Good luck.

---

### Post by Rick St. George on 2015-04-13
That did the trick. Removed the PPA, did autoremove; update; upgrade in terminal, then installed Linphone under Software Center.
Now audio / video works like it should. Better alternative to Skype (since Microsoft bought it). 

Thanks everyone! 
Ubuntu Reigns ! ! !

Will consider closed.
Rick

---

### Post by Bucky Ball on 2015-04-13
Nice to hear it's all working. Enjoy. ;)

---

