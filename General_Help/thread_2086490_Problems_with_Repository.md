---
title: "Problems with Repository"
date: 2012-11-21
forum: General Help
---

### Post by lumaja on 2012-11-21
I been having problems installing certain applications and every time I update Ubuntu 12.04 there is a warning that I dint update since and date.
 I asked for help, I got some but still problems with Sources List, after searching in the Web found “sudo gedit /etc/apt/sources.list”the Terminal result follows, it shows I been update from a wrong site “ZA” I think is reference of my location.
 I am new on this things and need help to fix this please.
 Thank you.
 

 luis@luis-G41M-Combo:~$ sudo gedit /etc/apt/sources.list  
 [sudo] password for luis:  
 luis@luis-G41M-Combo:~$ cat /etc/apt/sources.list  
 # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted  
 

 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to  
 # newer versions of the distribution.  
 

 ## Major bug fix updates produced after the final release of the  
 ## distribution.  
 

 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team. Also, please note that software in universe WILL NOT receive any  
 ## review or updates from the Ubuntu security team.  
 deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise universe  
 deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise universe  
 deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-updates universe  
 deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-updates universe  
 

 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu  
 ## security team.  
 

 ## N.B. software from this repository may not have been tested as  
 ## extensively as that contained in the main release, although it includes  
 ## newer versions of some applications which may provide useful features.  
 ## Also, please note that software in backports WILL NOT receive any review  
 ## or updates from the Ubuntu security team.  
 

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe  
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe  
 

 ## Uncomment the following two lines to add software from Canonical's  
 ## 'partner' repository.  
 ## This software is not part of Ubuntu, but is offered by Canonical and the  
 ## respective vendors as a service to Ubuntu users.  
 # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner  
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner  
 

 ## This software is not part of Ubuntu, but is offered by third-party  
 ## developers who want to ship their latest software.  
 deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main  
 # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main  
 deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib  
 luis@luis-G41M-Combo:~$

---

### Post by lisati on 2012-11-21
Thread closed, it follows on from [http://ubuntuforums.org/showthread.php?t=2085881](http://ubuntuforums.org/showthread.php?t=2085881)

---

