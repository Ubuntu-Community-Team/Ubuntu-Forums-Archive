---
title: "Problem with sudo apt-get update"
date: 2019-07-18
forum: General Help
---

### Post by Old Jimma on 2019-07-18
Hi Community:

I'm having trouble with updating my computer.

When I do a

> sudo apt-get update 

I get a ton of weird messages listed below. In other attempts that I can't duplicate, the > sudo apt-get update  complains that chromium can't be updated or something like that.

What should I do?

THanks,
Old Jimma

> 
sudo apt-get update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease                                                           
Ign:3 [http://ppa.launchpad.net/aims/sagemath/ubuntu](http://ppa.launchpad.net/aims/sagemath/ubuntu) bionic InRelease                                                
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease                                                       
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease                                                        
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease                                                     
Hit:7 [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) bionic InRelease                          
Hit:8 [http://ppa.launchpad.net/bluetooth/bluez/ubuntu](http://ppa.launchpad.net/bluetooth/bluez/ubuntu) bionic InRelease        
Hit:9 [http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu](http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu) bionic InRelease 
Hit:10 [http://ppa.launchpad.net/elementary-os/stable/ubuntu](http://ppa.launchpad.net/elementary-os/stable/ubuntu) bionic InRelease  
Ign:11 [http://ppa.launchpad.net/gezakovacs/pdfocr/ubuntu](http://ppa.launchpad.net/gezakovacs/pdfocr/ubuntu) bionic InRelease     
Hit:12 [http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu](http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu) bionic InRelease
Err:13 [http://ppa.launchpad.net/aims/sagemath/ubuntu](http://ppa.launchpad.net/aims/sagemath/ubuntu) bionic Release           
  404  Not Found [IP: 91.189.95.83 80]
Err:14 [http://ppa.launchpad.net/gezakovacs/pdfocr/ubuntu](http://ppa.launchpad.net/gezakovacs/pdfocr/ubuntu) bionic Release        
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done                                                  
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11-icons-small (non-free/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target CNF (non-free/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target CNF (non-free/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
E: The repository 'http://ppa.launchpad.net/aims/sagemath/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/bookworm-team-ubuntu-bookworm-bionic.list:2 and /etc/apt/sources.list.d/bookworm-team-ubuntu-bookworm-bionic.list:4
E: The repository 'http://ppa.launchpad.net/gezakovacs/pdfocr/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11-icons-small (non-free/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target CNF (non-free/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target CNF (non-free/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:53 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/bookworm-team-ubuntu-bookworm-bionic.list:2 and /etc/apt/sources.list.d/bookworm-team-ubuntu-bookworm-bionic.list:4


---

### Post by kc1di on 2019-07-18
Hi, 
You have two things going on here.

1. you have a bad ppa that is either no longer available or it's server is down at the moment.

2.  you have multiple entries in your /etc/apt/source.list 

You can fix the first one by removing or disabling the this ppa ```
http://ppa.launchpad.net/gezakovacs/pdfocr/ubuntu 
```
You can fix the other problem by disabling or removing the duplicate entries in your /etc/apt/source.list

Good Luck.

---

### Post by deadflowr on 2019-07-18
Repeat the same as above to remove the aims/sagemath ppa as well.
That has no archive for bionic.

---

### Post by Old Jimma on 2019-07-18
Hi kc1di and deadflowr:

Thanks for your replies!

When I removed the repositories you indicated, and updated  it worked seemlessly.

I have no idea how those odd repositories got added. I'll have to be more careful in the fugure!

Many thanks!

Old Jimma

---

### Post by kc1di on 2019-07-18
Glad it worked for you!

---

