---
title: "Updates fail on Ubuntu14.04"
date: 2016-08-19
forum: General Help
---

### Post by frank18 on 2016-08-19
Hi guys, lately when i open updater and i get this message on Ubuntu 14.04 see attach

---

### Post by &amp;KyT$0P# on 2016-08-19
What happens if you manually run these commands in a Terminal?  Please post the full output here.
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by frank18 on 2016-08-19
```

sudo apt-get update
sudo apt-get upgrade     
sudo apt-get dist-upgrade  

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4,990 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [481 kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [131 kB]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5,178 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Fetched 4,668 kB in 4s (1,101 kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems




Unpacking unity (7.2.6+14.04.20160408-0ubuntu1) over (7.2.6+14.04.20151021-0ubuntu1) ...
Preparing to unpack .../libunity-core-6.0-9_7.2.6+14.04.20160408-0ubuntu1_amd64.deb ...
Unpacking libunity-core-6.0-9 (7.2.6+14.04.20160408-0ubuntu1) over (7.2.6+14.04.20151021-0ubuntu1) ...
Preparing to unpack .../unity-services_7.2.6+14.04.20160408-0ubuntu1_amd64.deb ...
Unpacking unity-services (7.2.6+14.04.20160408-0ubuntu1) over (7.2.6+14.04.20151021-0ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
dpkg: error processing package ttf-mscorefonts-installer (--configure):
 package ttf-mscorefonts-installer is not ready for configuration
 cannot configure (current status `half-installed')
Setting up libgcrypt11:amd64 (1.5.3-2ubuntu4.4) ...
Setting up unity-services (7.2.6+14.04.20160408-0ubuntu1) ...
Setting up libunity-core-6.0-9 (7.2.6+14.04.20160408-0ubuntu1) ...
Setting up unity (7.2.6+14.04.20160408-0ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)







Setting up unity (7.2.6+14.04.20160408-0ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
frank@frank-ThinkCentre-M71e:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-88 linux-headers-3.13.0-88-generic
  linux-image-3.13.0-88-generic linux-image-extra-3.13.0-88-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/27.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
dpkg: error processing package ttf-mscorefonts-installer (--configure):
 package ttf-mscorefonts-installer is not ready for configuration
 cannot configure (current status `half-installed')
E: Sub-process /usr/bin/dpkg returned an error code (1)
frank@frank-ThinkCentre-M71e:~$ 
```

---

### Post by grahammechanical on 2016-08-19
I will have a guess. The package ttf-mscorefonts-installer requires user action. Which it did not get. In order for the installer to be able to install Microsoft's core fonts we need to accept the Microsoft End User License Agreement (EULA).

That is separate from the error caused by duplicated entries in the sources list file. I am fairly certain that the duplicate entry is as a result of more than one attempted to install Google Chrome. I have had that error when I messed up one attempt to install Chrome and then had to try again.

Regards.

---

### Post by QIII on 2016-08-19
frank18:

Please do not cut and paste formatting/BB Code from other Forums or Stack Exchange sites.  Please use the standard fonts and colors for the Ubuntu Forums.

Please show some courtesy to the volunteers here by taking the time to create a post rather than copy from somewhere else.

Thanks.

---

### Post by frank18 on 2016-08-21
> **grahammechanical said:**
> I will have a guess. The package ttf-mscorefonts-installer requires user action. Which it did not get. In order for the installer to be able to install Microsoft's core fonts we need to accept the Microsoft End User License Agreement (EULA).

That is separate from the error caused by duplicated entries in the sources list file. I am fairly certain that the duplicate entry is as a result of more than one attempted to install Google Chrome. I have had that error when I messed up one attempt to install Chrome and then had to try again.

Regards.

Thanks  **grahammechanical** : after a few more tries i was able to reinstall  ttf-mscorefonts-installer and The EULA poped up and i agreed on  the Microsoft fonts agreement and  now all  fine,also i'm presented with a notification that there is a 16.04  upgrade available,which i decline till all bugs are sorted out,which i  will doubt.I must say that i have not been very cordial with Ubuntu 16.04 folks,but it's my opinion on the facts are that never has been a so poor Ubuntu release for us Ubuntu Lovers that leads Ubuntu lovers to haters. believe me i just want to love Ubuntu not to hate it,more i installed all the previous  Ubuntu releases and none did me grief like 16.04 tell me why,am i right or not.

---

