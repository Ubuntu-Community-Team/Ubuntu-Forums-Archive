---
title: "dpkg-preconfigure error"
date: 2007-01-04
forum: General Help
---

### Post by arche on 2007-01-04
Hello everyone, I have searched the forums and can't seem to figure out this problem. I have installed Ubuntu Server successfully once so far, the last three times I have installed I keep coming up with the same error ever time I run this:

apt-get upgrade

root@localhost:/home/arche# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gnupg info linux-image-2.6.17-10-server tar w3m x11-common
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 26.5MB of archives.
After unpacking 963kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main x11-common 1:7.1.1ubuntu6.2 [291kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main tar 1.15.91-2ubuntu0.3 [346kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main gnupg 1.4.3-2ubuntu3.2 [1056kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main info 4.8.dfsg.1-1ubuntu0.1 [163kB]                                             
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main w3m 0.5.1-4ubuntu2.6.10 [1085kB]                                               
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main linux-image-2.6.17-10-server 2.6.17.1-10.34 [23.6MB]                           
Fetched 26.5MB in 2m43s (163kB/s)                                                                                                  
E: Sub-process /usr/sbin/dpkg-preconfigure --apt || true returned an error code (100)
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true

I keep running into the same problem, I have reinstalled Ubuntu three times already and have not been able to get past this point. Can anyone give me a insite to what the problem is..

Thanks in advance

arche

---

### Post by arche on 2007-01-04
Does anyone have an answer?

---

### Post by taurus on 2007-01-04
Maybe paste your /etc/apt/sources.list to see what's going on...

```
cat /etc/apt/sources.list
```

---

### Post by arche on 2007-01-04
Hope this helps..

#
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by taurus on 2007-01-04
Try

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by arche on 2007-01-04
After doing the update I did the upgrade and got this:

root@localhost:/etc/apt# sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  gnupg info linux-image-2.6.17-10-server tar w3m x11-common 
6 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/26.5MB of archives. After unpacking 963kB will be used.
Do you want to continue? [Y/n/?] y
E: Sub-process /usr/sbin/dpkg-preconfigure --apt || true returned an error code (100)
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true
A package failed to install.  Trying to recover:
root@localhost:/etc/apt# 

Am I doing something wrong, or does something need to be replaced? Please help...

arche

---

### Post by arche on 2007-01-04
Anyone have any other suggestions?

Thanks

arche

---

### Post by ishift on 2007-01-04
i seem to be running into the same problem. is there something wrong with the repositories or something?

---

### Post by arche on 2007-01-04
> **ishift said:**
> i seem to be running into the same problem. is there something wrong with the repositories or something?

I am wondering the same thing, hopefully someone has an answer..

arche

---

### Post by taurus on 2007-01-04
Remove the **us.** from the repos in /etc/apt/sources.list and see if that helps...

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by arche on 2007-01-04
nope, I get the same response.

root@localhost:/home/arche# sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release [50.9kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release [34.7kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release [23.3kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release [23.3kB]                  
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [39.1kB]     
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages [940kB]                 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages [3514B]  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [8107B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources [925B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [17.0kB]       
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [1476B]           
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages [5974B]                                                                   
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources [274kB]                                                                          
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources [1436B]                                                                    
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages [3559kB]                                                                    
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources [1068kB]                                                                     
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [53.8kB]                                                                
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages [14B]                                                             
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources [16.3kB]                                                                 
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources [14B]                                                              
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages [1301B]                                                               
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages [14B]                                                           
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages [10.2kB]                                                          
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [1583B]                                                         
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources [685B]                                                                 
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources [14B]                                                            
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources [3325B]                                                            
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources [720B]                                                           
Fetched 6139kB in 40s (153kB/s)                                                                                                     
Reading package lists... Done
root@localhost:/home/arche# sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  gnupg info linux-image-2.6.17-10-server tar w3m x11-common 
6 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/26.5MB of archives. After unpacking 963kB will be used.
Do you want to continue? [Y/n/?] y
E: Sub-process /usr/sbin/dpkg-preconfigure --apt || true returned an error code (100)
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true
A package failed to install.  Trying to recover:
root@localhost:/home/arche#

---

### Post by goatflyer on 2007-01-04
Has anyone tried looking in /var/log/dpkg for clues?

---

### Post by arche on 2007-01-05
> **goatflyer said:**
> Has anyone tried looking in /var/log/dpkg for clues?

does not show anything in the log, after the install and the first update the log stops. So it is not recording any errors or anything else, so something happened after the very first update attempt.

arche

---

### Post by arche on 2007-01-05
Figured out the problem, some reason there was a problem with bash. I ran this and everything worked fine.

ln -s /bin/bash /bin/sh

Hope this helps someone else. Thanks for all the help.

arche

---

### Post by k5utcchad on 2007-01-11
removing the us. worked for me thank you very much!:D

---

