---
title: "Error running apt update"
date: 2020-06-10
forum: General Help
---

### Post by satimis on 2020-06-10
Ubuntu 18.04 on VM of VirturalBox

On running apt update following errors displayed```

.....
Err:7 http://www.getdeb.net/ubuntu yakkety-getdeb InRelease             
  403  Forbidden [IP: 143.95.32.90 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://archive.getdeb.net/ubuntu/dists/yakkety-getdeb/InRelease  403  Forbidden [IP: 143.95.32.90 80]
E: The repository 'http://archive.getdeb.net/ubuntu yakkety-getdeb InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```
But 'http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu bionic Release' is not on /etc/apt/sources.list

Pls help.  Thanks

Regards
satimis

---

### Post by dino99 on 2020-06-10
Check your old / deprecated ? / external sources first (which could introduce version conflicts) via 'synaptic' or ' software-properties-gtk' to disable them.

---

### Post by satimis on 2020-06-10
> **dino99 said:**
> Check your old / deprecated ? / external sources first (which could introduce version conflicts) via 'synaptic' or ' software-properties-gtk' to disable them.
Hi,

Thanks for your advice.

I have performed follows;

$ sudo apt update
$ sudo apt autoclean
$ sudo dpkg --configure -a

Problem still remains

$ sudo apt update```

Hit:1 http://hk.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://hk.archive.ubuntu.com/ubuntu bionic-updates InRelease                                  
Hit:3 http://hk.archive.ubuntu.com/ubuntu bionic-backports InRelease                                
Hit:5 http://security.ubuntu.com/ubuntu bionic-security InRelease                                   
Ign:6 http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu bionic InRelease                     
Err:4 http://www.getdeb.net/ubuntu yakkety-getdeb InRelease                                      
  403  Forbidden [IP: 143.95.32.90 80]
Err:7 http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done                      
E: Failed to fetch http://archive.getdeb.net/ubuntu/dists/yakkety-getdeb/InRelease  403  Forbidden [IP: 143.95.32.90 80]
E: The repository 'http://archive.getdeb.net/ubuntu yakkety-getdeb InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Tried again;

$ sudo apt install ppa-purge
$ sudo ppa-purge [http://ppa.launchpad.net](http://ppa.launchpad.net)```

Updating packages lists
E: Failed to fetch http://archive.getdeb.net/ubuntu/dists/yakkety-getdeb/InRelease  403  Forbidden [IP: 143.95.32.90 80]
E: The repository 'http://archive.getdeb.net/ubuntu yakkety-getdeb InRelease' is not signed.
E: The repository 'http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu bionic Release' does not have a Release file.
Warning:  apt-get update failed for some reason

```

Regards
satimis

---

### Post by deadflowr on 2020-06-10
You need to disable/remove both the getdeb repository and the listed launchpad ppa entries from your sources before anything can work correctly again.

---

### Post by Holger_Gehrke on 2020-06-10
'getdeb' does not really exist any more, it's turned into a spammy clickbait graveyard. The n-muench/programs-ppa seems rather dead, too. The last update was 222 weeks ago.

If neither of those is in '/etc/apt/sources.list' you should check for configuration fragments in the directory '/etc/apt/sources.list.d/'.

The right call to remove the n-muench/programs-ppa using ppa-purge should be 'ppa-purge ppa:n-muench/programs-ppa'.

Holger

---

### Post by deadflowr on 2020-06-10
I doubt ppa-purge is even necessary since the sources are for a non-existent archive,
so unless a release upgrade (moving from something like 19.10 to 20.04 or some other upgrade path), nothing would have ever been installed from the ppa.

---

### Post by satimis on 2020-06-10
Hi all,

$ cat /etc/apt/souces.list```


# deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted

deb http://hk.archive.ubuntu.com/ubuntu/ bionic main restricted

deb http://hk.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

deb http://hk.archive.ubuntu.com/ubuntu/ bionic universe

deb http://hk.archive.ubuntu.com/ubuntu/ bionic-updates universe

deb http://hk.archive.ubuntu.com/ubuntu/ bionic multiverse

deb http://hk.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

deb http://hk.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu bionic-security main restricted

deb http://security.ubuntu.com/ubuntu bionic-security universe

deb http://security.ubuntu.com/ubuntu bionic-security multiverse

```

Which repos shall I comment out?  Thanks

Regards

---

### Post by satimis on 2020-06-10
> **Holger_Gehrke said:**
>  - snip -

If neither of those is in '/etc/apt/sources.list' you should check for configuration fragments in the directory '/etc/apt/sources.list.d/'.


$ ls /etc/apt/apt.conf.d/```

00aptitude    01autoremove-kernels  15update-stamp   20dbus        50appstream            60icons
00trustcdrom  01-vendor-ubuntu      20archive        20packagekit  50command-not-found    70debconf
01autoremove  10periodic            20auto-upgrades  20snapd.conf  50unattended-upgrades  99update-notifier

```

---

### Post by CelticWarrior on 2020-06-10
> **satimis said:**
> Hi all,

$ cat /etc/apt/souces.list```


# deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted

deb http://hk.archive.ubuntu.com/ubuntu/ bionic main restricted

deb http://hk.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

deb http://hk.archive.ubuntu.com/ubuntu/ bionic universe

deb http://hk.archive.ubuntu.com/ubuntu/ bionic-updates universe

deb http://hk.archive.ubuntu.com/ubuntu/ bionic multiverse

deb http://hk.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

deb http://hk.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu bionic-security main restricted

deb http://security.ubuntu.com/ubuntu bionic-security universe

deb http://security.ubuntu.com/ubuntu bionic-security multiverse

```

Which repos shall I comment out?  Thanks

Regards

Nothing.
> you should check for configuration fragments in the directory '/etc/apt/sources.list.d/'.

Using a GUI you can also check in Software & Updates > 2nd tab (other software).

---

### Post by ActionParsnip on 2020-06-10
If you run:
```

sudo grep -R muench /etc/apt/*

```

Then (If it is in it's own file) delete it, or open the file in a text editor and comment out the lines. Not all PPAs support all releases

---

### Post by satimis on 2020-06-10
> **ActionParsnip said:**
> If you run:
```

sudo grep -R muench /etc/apt/*

```

Then (If it is in it's own file) delete it, or open the file in a text editor and comment out the lines. Not all PPAs support all releases
Performed following steps.

$ sudo grep -R muench /etc/apt/*
```
 
/etc/apt/sources.list.d/n-muench-ubuntu-programs-ppa-bionic.list:deb http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu bionic main
/etc/apt/sources.list.d/n-muench-ubuntu-programs-ppa-bionic.list:# deb-src http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu bionic main

```

$ sudo gedit /etc/apt/sources.list.d/n-muench-ubuntu-programs-ppa-bionic.list ```

** (gedit:10923): WARNING **: 09:23:35.714: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported

** (gedit:10923): WARNING **: 09:23:35.715: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:10923): WARNING **: 09:23:38.409: Set document metadata failed: Setting attribute metadata::gedit-position not supported

```

There are only 2 lines on the file```

deb http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu bionic main
# deb-src http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu bionic main

```

Moved the file running;
$ sudo mv n-muench-ubuntu-programs-ppa-bionic.list-old /home/satimis/Documents/

$ sudo apt update```

Hit:1 http://hk.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://hk.archive.ubuntu.com/ubuntu bionic-updates InRelease                                     
Hit:3 http://hk.archive.ubuntu.com/ubuntu bionic-backports InRelease                                   
Hit:5 http://security.ubuntu.com/ubuntu bionic-security InRelease                                                             
Err:4 http://www.getdeb.net/ubuntu yakkety-getdeb InRelease                
  403  Forbidden [IP: 143.95.32.90 80]
Reading package lists... Done
E: Failed to fetch http://archive.getdeb.net/ubuntu/dists/yakkety-getdeb/InRelease  403  Forbidden [IP: 143.95.32.90 80]
E: The repository 'http://archive.getdeb.net/ubuntu yakkety-getdeb InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Error still found

Regards
satimis

---

### Post by jijothic on 2020-12-17
[COLOR=#242729][FONT=Arial] [/FONT]There is a file named [/COLOR]*getdeb.list*[COLOR=#242729] in the [/COLOR]/etc/apt/sources.list.d/
Open the terminal and type:
sudo vi /etc/apt/sources.list.d/getdeb.list 

**comment** deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) yakkety-getdeb apps

run  sudo apt update you should be ok :)

---

