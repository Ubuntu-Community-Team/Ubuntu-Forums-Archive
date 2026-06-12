---
title: "problem installing updates"
date: 2017-02-21
forum: General Help
---

### Post by juntjoo2 on 2017-02-21
how do I fix this?

The following packages have unmet dependencies:


kde-telepathy-minimal: Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not installed
                       Depends: telepathy-connection-manager but it is a virtual package
                       Depends: telepathy-mission-control-5 (>= 1:5.12) but 1:5.16.3-1ubuntu6 is installed

---

### Post by oldos2er on 2017-02-21
Which version of Ubuntu?

---

### Post by juntjoo2 on 2017-02-21
16.0.4. thanks

---

### Post by wildmanne39 on 2017-02-22
Please post the output of:
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```
Thanks

---

### Post by juntjoo2 on 2017-02-22
thanks:

```
cat /etc/apt/sources.list# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
deb http://archive.canonical.com/ precise partner
# deb-src http://archive.canonical.com/ precise partner
deb http://archive.canonical.com/ xenial partner
# deb-src http://archive.canonical.com/ xenial partner
# deb-src http://archive.canonical.com/ xenial partner
ben@Hal:~$ ls /etc/apt/sources.list.d/
d-apt.list
d-apt.list.save
google-chrome.list
google-chrome.list.save
inameiname-ubuntu-stable-xenial.list
inameiname-ubuntu-stable-xenial.list.save
nrbrtx-ubuntu-sysvinit-backlight-xenial.list
nrbrtx-ubuntu-sysvinit-backlight-xenial.list.save
playonlinux.list
playonlinux.list.save
ubuntu-wine-ubuntu-ppa-xenial.list
ubuntu-wine-ubuntu-ppa-xenial.list.save
wine-ubuntu-wine-builds-xenial.list
wine-ubuntu-wine-builds-xenial.list.save
xubuntu-dev-ubuntu-xfce-4_12-xenial.list
```

what are "cat" and "ls" BTW?" Would like to gain some knowledge to stick in my pocket for later.

---

### Post by wildmanne39 on 2017-02-22
Please do:
```
sudo -H gedit /etc/apt/sources.list
```
Then remove:
```
# deb-src http://archive.canonical.com/ precise partner
deb http://archive.canonical.com/ xenial partner
```
save then close gedit.
Then do:
```
sudo apt update && sudo apt upgrade
```
That should fix the issue, if not we may have to clean up:
```
/etc/apt/sources.list.d/
```
file as well, but I believe this will not be needed.
both the cat and ls command show what is in a file.

---

### Post by howefield on 2017-02-22
> **wildmanne39 said:**
> Please do:
```
sudo -H /etc/apt/sources.list
```

missed the gedit in there (assuming that's what you were advising to use :)

```
sudo -H gedit /etc/apt/sources.list
```

---

### Post by wildmanne39 on 2017-02-22
Thanks howefield!:)

---

### Post by juntjoo2 on 2017-02-22
maybe I did something wrong

```
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InReleaseGet:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:4 http://archive.canonical.com xenial InRelease                            
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:7 http://ppa.launchpad.net/inameiname/stable/ubuntu xenial InRelease       
Hit:8 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial InRelease         
Hit:9 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease        
Ign:10 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu xenial InRelease  
Err:11 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu xenial Release    
  404  Not Found
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

here's what my list looks like now:

```
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner
ben@Hal:~$ ls /etc/apt/sources.list.d/
d-apt.list                            inameiname-ubuntu-stable-xenial.list.save          ubuntu-wine-ubuntu-ppa-xenial.list
d-apt.list.save                       nrbrtx-ubuntu-sysvinit-backlight-xenial.list       ubuntu-wine-ubuntu-ppa-xenial.list.save
google-chrome.list                    nrbrtx-ubuntu-sysvinit-backlight-xenial.list.save  wine-ubuntu-wine-builds-xenial.list
google-chrome.list.save               playonlinux.list                                   wine-ubuntu-wine-builds-xenial.list.save
inameiname-ubuntu-stable-xenial.list  playonlinux.list.save                              xubuntu-dev-ubuntu-xfce-4_12-xenial.list
```

---

### Post by wildmanne39 on 2017-02-22
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2017-02-22
Please do:
```
sudo -H gedit /etc/apt/sources.list.d/
```
Remove:
```
xubuntu-dev-ubuntu-xfce-4_12-xenial.list
```
Save then close gedit.

Do:
```
sudo apt update && sudo apt upgrade
```
I have to leave for a while be back as soon as possible.
Thanks

---

### Post by juntjoo2 on 2017-02-22
Sorry. Thanks. I was never quite sure why we did that so I just did it for terminal output

thank YOU. i appreciate you taking the time to help out.  It's telling me it's a directory.  I tried manually deleting but looks like I need the sudo.  Maybe you missed some code?

---

### Post by howefield on 2017-02-22
You seem comfortable enough with the terminal... to remove the file, do a

```
sudo rm /etc/apt/sources.list.d/xubuntu-dev-ubuntu-xfce-4_12-xenial.list
```

---

### Post by juntjoo2 on 2017-02-22
Thanks. Cool, now I know how to RM stuff :D and possibly destroy my system.

```
You might want to run 'apt-get -f install' to correct these.The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not installed
E: Unmet dependencies. Try using -f.

```

yes, just what it tells me when I do the upgrade the gui way.  This 'telepathy' file is "broken" in synaptic and I can't do anything with it.  Is it what I need to delete being related to "precise" or do we need to fix it?

---

### Post by wildmanne39 on 2017-02-22
That error message should go away when you do what I posted in post 6.

It is my fault, I assumed you knew when the window came up to enter you password, then gedit will open and carefully remove the lines I posted in post 6, save and close gedit, then continue with the directions in that post and I believe your issue will be resolved.

If not post all the output from running the update and upgrade command.
Thanks

---

### Post by juntjoo2 on 2017-02-23
thanks.  Getting the same as I posted just above in #14.

[COLOR=#000000][FONT=&quot]```
[/FONT][/COLOR]# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

```

maybe I missed something?

---

### Post by juntjoo2 on 2017-02-23
```
The following packages have unmet dependencies:

kde-telepathy-minimal: Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not installed
                       Depends: telepathy-connection-manager but it is a virtual package
                       Depends: telepathy-mission-control-5 (>= 1:5.12) but 1:5.16.3-1ubuntu6 is installed
```

---

