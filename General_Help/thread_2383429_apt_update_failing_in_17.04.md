---
title: "apt update failing in 17.04"
date: 2018-01-25
forum: General Help
---

### Post by pictsidhe on 2018-01-25
This has been bugging me a week now. I tested my system on the in-laws wifi today, so I've ruled out my connection.

```
pictsidhe@T61:~$ sudo apt update
Ign:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty InRelease
Hit:2 [http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu](http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu) zesty InRelease
Ign:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates InRelease                                      
Ign:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports InRelease                                    
Hit:5 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) zesty InRelease
Ign:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security InRelease                                     
Err:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty Release                                                
  404  Not Found [IP: 91.189.88.162 80]
Err:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates Release                  
  404  Not Found [IP: 91.189.88.162 80]
Hit:9 [http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu) zesty InRelease
Err:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports Release
  404  Not Found [IP: 91.189.88.162 80]
Err:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security Release
  404  Not Found [IP: 91.189.88.162 80]
Reading package lists... Done
E: The repository 'http://archive.ubuntu.com/ubuntu zesty Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

```
pictsidhe@T61:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty
```

```
pictsidhe@T61:~$ uname -r
4.10.0-42-generic

```
```
pictsidhe@T61:~$ cat /etc/apt/sources.list
# deb cdrom:[Lubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty main restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates main restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates main restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) zesty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security main restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse
```

I don't remember messing with apt, but it was a week ago and as my connection was being really flaky, I put it down to that. My pi and debian systems are working fine. I've tried installing some software. when the debs can't be found, my browser can't find the files either. Google isn't finding anyone else with the issue, so it can't be the servers...
I was on us.ubuntu.com, I tried switching to the main archive and a few others with no luck. The GUI software centre failed to 'select best server' after 'failed to download repository information'.

---

### Post by Bashing-om on 2018-01-25
pictsidhe' Hey ...

zesty - 17.04 - is End_Of_Life .
Same same : [https://ubuntuforums.org/showthread.php?t=2382622&p=13730871#post13730871](https://ubuntuforums.org/showthread.php?t=2382622&p=13730871#post13730871)

[INDENT][INDENT]all she wrote
[/INDENT][/INDENT]

---

### Post by pictsidhe on 2018-01-25
Doh!
I usually use LTS...

---

