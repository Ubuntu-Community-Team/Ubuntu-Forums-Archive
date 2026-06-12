---
title: "E:package autoconf has no installition candidate"
date: 2007-06-09
forum: General Help
---

### Post by hadeel on 2007-06-09
am try to install ns-allinone-2.31 on Ubuntu 7.04  when run this command 
" sudo apt-get install build-essential autoconf automake libxmu-dev "
got this error " E:package autoconf has no installition candidate "
any ideas how to solve 
thnx

---

### Post by taurus on 2007-06-09
How about 

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by hadeel on 2007-06-10
thnx for ur replay 
i try this but i still have the same error:(
any more ideas :(

---

### Post by taurus on 2007-06-10
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by hadeel on 2007-06-11
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by taurus on 2007-06-11
What's the output from a terminal when you run this command?

```
sudo aptitude update
```

---

### Post by hadeel on 2007-06-11
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty Release.gpg
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/main Translation-en_US
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/restricted Translation-en_US
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
  Could not resolve 'security.ubuntu.com'
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/universe Translation-en_US
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/multiverse Translation-en_US
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates Release.gpg
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/main Translation-en_US
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
  Could not resolve 'eg.archive.ubuntu.com'
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty Release
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates Release
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/main Packages
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/restricted Packages
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/main Sources
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/restricted Sources
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/universe Packages
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/universe Sources
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/main Packages
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/main Sources
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/restricted Sources
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/main Packages
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/restricted Packages
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/main Sources
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/restricted Sources
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/universe Packages
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/universe Sources
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/multiverse Packages
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty/multiverse Sources
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/main Packages
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/restricted Packages
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/main Sources
  Could not resolve 'eg.archive.ubuntu.com'
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) feisty-updates/restricted Sources
  Could not resolve 'eg.archive.ubuntu.com'
Reading package lists... Done

---

### Post by taurus on 2007-06-11
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **eg.** from the repos.  Then, save it and run

```
sudo aptitude clean
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by hadeel on 2007-06-11
sudo aptitude update i got this 

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
  Could not resolve 'archive.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
  Could not resolve 'security.ubuntu.com'
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Reading package lists... Done



and finally i still have the same error

note: i face problem with enternet connection

---

### Post by taurus on 2007-06-11
Sounds to me like you are behind a proxy or a firewall.  How does your machine connect to the net anyway?

---

### Post by hadeel on 2007-06-11
:D it dosen't connect either adsl nor wireless both have problems

---

### Post by taurus on 2007-06-11
You first need to get your network working first before you can use synaptic/apt-get/apttitude.

However, build-essential is on the installer CD so insert it into a drive and run

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by hadeel on 2007-06-12
i try this and that what i get " sudoaptitude update "
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  Could not resolve 'security.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
  Could not resolve 'archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
  Could not resolve 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done


and " sudo aptitude install build-essential "

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

