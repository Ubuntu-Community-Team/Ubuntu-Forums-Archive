---
title: "[SOLVED] repositories failed"
date: 2008-07-08
forum: General Help
---

### Post by stubblepoo on 2008-07-08
i was trying to add a repository via system>administration>software sources and now when i open any update or install managers i get errors saying: 
E: Type ‘sudo’ is not known on line 52 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

i tried fixing apt-get via terminal but i get the message:
kiran@kiran-laptop:~$ apt-get check
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
kiran@kiran-laptop:~$ sudo apt-get check
[sudo] password for kiran: 
E: Type ‘sudo’ is not known on line 52 in source list /etc/apt/sources.list
E: The list of sources could not be read.
 
any advice would be welcome.

---

### Post by tszanon on 2008-07-08
Please, post the contents of your **/etc/apt/sources.list** file. It seems that there's something wrong written there.

---

### Post by drs305 on 2008-07-08
It would be best to post the entire contents of your sources.list, but for a quick shortcut to the problem line, you can use the following command. It will open /etc/apt/sources.list with gedit and adminstrator privileges and take you directly to Line 52 so you can edit and save the file.

The problem is that a sources.list file should not have a line that starts with "sudo ..."  A command probably got inadvertently inserted by mistake. There me other errors as well - that is why it would be best to check the entire file. If you feel lucky, the good news is there aren't any errors on lines 1-51. If there aren't any AFTER line 52, all you would have to do is put a # symbol at the start of the line, telling sources.list to disregard it.

```
gksu gedit +52 /etc/apt/sources.list
```

---

### Post by stubblepoo on 2008-07-08
this is all of it:

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

sudo apt-get update

---

### Post by drs305 on 2008-07-08
> **stubblepoo said:**
> 



**sudo apt-get update**

Open sources.list as I described in the earlier post and remove that line. Save the file and it will fix your problem. 

Once you have saved it, rerun:
```

sudo apt-get update && sudo apt-get upgrade
```

---

