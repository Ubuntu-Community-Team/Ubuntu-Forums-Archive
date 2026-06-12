---
title: "Virtual Box 6 Installation Failure on Ubuntu 18.10"
date: 2019-04-07
forum: General Help
---

### Post by planetrocker on 2019-04-07
```
virtualbox-6.0 : Depends: libqt5opengl5 (>= 5.0.2) but it is not installable
                  Recommends: libsdl-ttf2.0-0 but it is not installable
```

i cannot locate and install packages libqt5opengl5 and libsdl-ttf2.0-0 
in order to have virtualbox-6.0 working

---

### Post by SeijiSensei on 2019-04-07
I suggest using Oracle's repository for VB. Follow the instructions for "Debian-based" distributions at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by planetrocker on 2019-04-08
i have already added it ! :(

so we are missing 1 or 2 packages which need to be installed

---

### Post by SeijiSensei on 2019-04-08
I just installed VB from the Oracle repository. It brought in libsdl-ttf as well. I also have /usr/share/lintian/overrides/libqt5opengl5.

Now, I'm running Kubuntu which is built on the Qt platform, so I don't know if that library comes with vanilla Ubuntu.

For the record, I'm using 19.04, with the VirtualBox package for bionic (18.04).  My apt entry reads:

```
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian bionic contrib
```

---

### Post by planetrocker on 2019-04-08
I updated ```
/etc/apt/sources.list
```
and tried to reinstall

still stuck on these packages

---

### Post by cruzer001 on 2019-04-08
> **planetrocker said:**
> still stuck on these packages

Hello
I do not have this problem either, but I run 18.04

Is it available?  In terminal:
```
apt-cache libqt5opengl5
```
Also try:```

sudo apt install libqt5opengl5
```
That may give details as to why it will not install.

---

### Post by planetrocker on 2019-04-08
i get the message

```
Package libqt5opengl5 is not available, but is referred to by another package.
```
This may mean that the package is missing, has been obsoleted, or
is only available from another source

---

### Post by cruzer001 on 2019-04-08
```
sudo apt update libqt5opengl5
```
If it will not update please post your sources
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

---

### Post by cruzer001 on 2019-04-08
The package exist

[https://packages.ubuntu.com/cosmic/libqt5opengl5](https://packages.ubuntu.com/cosmic/libqt5opengl5)

---

### Post by planetrocker on 2019-04-08
```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
# deb [http://ftp.ntua.gr/ubuntu/](http://ftp.ntua.gr/ubuntu/) bionic main restricted multiverse


## Major bug fix updates produced after the final release of the
## distribution.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://ftp.ntua.gr/ubuntu/](http://ftp.ntua.gr/ubuntu/) bionic universe


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


# deb [http://ftp.ntua.gr/ubuntu/](http://ftp.ntua.gr/ubuntu/) bionic-security main restricted multiverse
# deb [http://ftp.ntua.gr/ubuntu/](http://ftp.ntua.gr/ubuntu/) bionic-security universe


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic multiverse

#deb [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) cosmic contrib
i tried with this distribution too

deb [arch=amd64] [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) bionic contrib
```

---

### Post by cruzer001 on 2019-04-08
Your sources are incomplete.  You need to build and install a new sources list:

I think this is what you need for a sources.list.  
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) cosmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) cosmic-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) cosmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) cosmic-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security multiverse

Create a file in your home folder (1st Level) and name it sources.list
Then copy and paste the above to the newly created sources.list file.

Then run```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.old && sudo cp ~/sources.list /etc/apt/
```

Now you should be able to run an update/upgrade.
```
sudo apt update && sudo apt full-upgrade

```
I have based this sources list on 18.04, should be ok for you if using U.S.

---

### Post by planetrocker on 2019-04-09
i still get this message

```
Package libqt5opengl5 is not available, but is referred to by another package.
```
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```

E: Package 'libqt5opengl5' has no installation candidate
```

---

### Post by cruzer001 on 2019-04-10
Just to verify.
The only entries in sources.list are the above posted ones.  Can verify with:
```
cat /etc/apt/sources.list
```
When you update in terminal there are no error messages?

I thought we hit on the solution and you would of received a big update.  Is this a recent upgrade 
to 18.10?  I have no further suggestions right now other than running some maintenance commands.  
```
sudo apt clean
sudo apt update
sudo apt full-upgrade
sudo apt -f install
```
Look for any error reports when running these commands.

---

### Post by planetrocker on 2019-04-11
not on my machine, very weird :(

---

### Post by cruzer001 on 2019-04-12
Apt-clean command should of wiped everything out of cache, but you have something
I do not understand going on so lets make sure it did get all and do a manual clean.
```
sudo rm -r /var/cache/apt/archives
sudo mkdir -p /var/cache/apt/archives/partial
```
Then try:
```
sudo apt update && sudo apt install libqt5opengl5
```

---

### Post by kafqa on 2019-09-03
Had the same problem, added an additional source and it worked [though I used bionic instead of cosmic for my system].

```
[COLOR=#000000]*deb *[/COLOR][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[COLOR=#000000]* cosmic-security main*[/COLOR]
```

---

### Post by slickymaster on 2019-09-03
Thread moved to **General Help** for a better fit

**@planetrocker**:
I've edited all your posts in this thread adding code tags to each. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

