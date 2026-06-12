---
title: "cannot get apt-get command to work, as well as ubuntu software center"
date: 2012-10-19
forum: General Help
---

### Post by Darth Poder on 2012-10-19
I cannot figure out how to fix the problem with my sudo apt-get install command to work as well as the software center, without killing Ubuntu and re-installing it. That is a problem seeing as how I have become attached to my currently install Ubuntu. I don't even understand what cause the problem; one minute my update manager is working fine and then I a message like this.

[HTML]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_lucid-bleed_ppa_ubuntu_dists_precise_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'
[/HTML]and then from that point on I could not update or using my Ubuntu software center, or sudo apt-get command. When I try to run them I get the kind of message.

                                  [HTML]W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_source_Sources  Hash Sum mismatch  
 

 W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources  404  Not Found [IP: 91.189.91.23 80]  
 

 W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.23 80]  
 

 W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages  Hash Sum mismatch  
 

 W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.23 80]  
 

 W: Failed to fetch http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found  
 

 W: Failed to fetch http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found  
 

 W: Failed to fetch http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found  
 

 E: Some index files failed to download. They have been ignored, or old ones used instead.
 

 Reading package lists... Error!  
 E: Encountered a section with no Package: header  
 E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_lucid-bleed_ppa_ubuntu_dists_precise_main_binary-amd64_Packages 
 E: The package lists or status file could not be parsed or opened.  
  [/HTML]and for the software center it just crashes. Please can someone tell me how to fix this problem.

---

### Post by SlugSlug on 2012-10-19
can you post in CODE tags

the out put of 

```
cat /etc/apt/sources.list
```


and

```
ls -l /etc/apt/sources.list.d/
```

---

### Post by ajgreeny on 2012-10-19
Perhaps also worth trying using synaptic rather than the software-centre; synaptic is much more flexible and will possibly show you much more information if there is a problem, though I wonder if the **lucid-bl;eed ppa** is your problem.

---

### Post by Darth Poder on 2012-10-20
> **SlugSlug said:**
> can you post in CODE tags

the out put of 

```
cat /etc/apt/sources.list
```and

```
ls -l /etc/apt/sources.list.d/
```


sure no problem anything to get this fixed

                                  [HTML]# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/ 
  
 # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/ 
 # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted 
  
 # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to 
 # newer versions of the distribution. 
 deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted 
 deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
 deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted 
 deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
 deb http://us.archive.ubuntu.com/ubuntu/ precise universe 
 deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe 
 deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe 
 deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
 deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse 
 deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse 
 deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse 
 deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse 
  
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
 deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
 deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
  
 deb http://security.ubuntu.com/ubuntu precise-security main restricted 
 deb-src http://security.ubuntu.com/ubuntu precise-security main restricted 
 deb http://security.ubuntu.com/ubuntu precise-security universe 
 deb-src http://security.ubuntu.com/ubuntu precise-security universe 
 deb http://security.ubuntu.com/ubuntu precise-security multiverse 
 deb-src http://security.ubuntu.com/ubuntu precise-security multiverse 
  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. 
 ## This software is not part of Ubuntu, but is offered by Canonical and the 
 ## respective vendors as a service to Ubuntu users. 
 # deb http://archive.canonical.com/ubuntu precise partner 
 # deb-src http://archive.canonical.com/ubuntu precise partner 
  
 ## This software is not part of Ubuntu, but is offered by third-party 
 ## developers who want to ship their latest software. 
 deb http://extras.ubuntu.com/ubuntu precise main 
 deb-src http://extras.ubuntu.com/ubuntu precise main 
 deb http://archive.canonical.com/ precise partner 
 deb-src http://archive.canonical.com/ precise partner 
 

 
[/HTML]
 
[HTML]
 -rw-r--r-- 1 root root 132 Oct 20 08:24 diesch-testing-precise.list 
 -rw-r--r-- 1 root root 132 Oct 20 08:24 diesch-testing-precise.list.save 
 -rw-r--r-- 1 root root 134 Oct 20 08:24 lucid-bleed-ppa-precise.list 
 -rw-r--r-- 1 root root 134 Oct 20 08:24 lucid-bleed-ppa-precise.list.save 
 -rw-r--r-- 1 root root   0 Oct 20 08:15 n-muench-vlc-precise.list 
 -rw-r--r-- 1 root root  66 Oct 20 08:15 n-muench-vlc-precise.list.save 
 -rw-r--r-- 1 root root 130 Oct 20 08:24 openmw-openmw-precise.list 
 -rw-r--r-- 1 root root 130 Oct 20 08:24 openmw-openmw-precise.list.save 
 -rw-r--r-- 1 root root 150 Oct 20 08:24 otto-kesselgulasch-gimp-precise.list 
 -rw-r--r-- 1 root root 150 Oct 20 08:24 otto-kesselgulasch-gimp-precise.list.save 
 -rw-r--r-- 1 root root  58 Oct 20 08:24 playdeb.list 
 -rw-r--r-- 1 root root  58 Oct 20 08:24 playdeb.list.save[/HTML]

---

### Post by ajgreeny on 2012-10-20
Try using software-sources to disable the various ppa repos you have one by one until you can refresh the sources.  I still think you have a problem perhaps with the two shown as
```
-rw-r--r-- 1 root root 134 Oct 20 08:24 lucid-bleed-ppa-precise.list
-rw-r--r-- 1 root root 134 Oct 20 08:24 lucid-bleed-ppa-precise.list.save
``` which seem to make no sense to me; the lucid-bleed repo was for lucid, not precise.

---

### Post by Darth Poder on 2012-10-20
> **ajgreeny said:**
> Try using software-sources to disable the various ppa repos you have one by one until you can refresh the sources.  I still think you have a problem perhaps with the two shown as
```
-rw-r--r-- 1 root root 134 Oct 20 08:24 lucid-bleed-ppa-precise.list
-rw-r--r-- 1 root root 134 Oct 20 08:24 lucid-bleed-ppa-precise.list.save
``` which seem to make no sense to me; the lucid-bleed repo was for lucid, not precise.

well I removed the two files and it was a complete fix. Thank you both, I was really worried that I would have to un-install and re-install Ubuntu.

---

### Post by ajgreeny on 2012-10-20
Great!

Please go to Thread Tools at the top and mark as "Solved".

---

