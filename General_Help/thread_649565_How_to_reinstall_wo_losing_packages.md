---
title: "How to reinstall w/o losing packages?"
date: 2007-12-25
forum: General Help
---

### Post by JusticeZero on 2007-12-25
Ubunto is running worse and worse over time as it updates things. How can I do a reinstall without having to remember and re-download all the packages I have installed from scratch?

---

### Post by TidusBlade on 2007-12-25
Im afraid theres not much to do but back up a few system folders maybe? Maybe backup the installation files if you still have them, and the system folders where the program was installed, there could be quite a few... Sounds stupid, but my only thought right now. And make a list of the programs you had, and if they are availible from the repos, set them to download overnight or something.

---

### Post by PmDematagoda on 2007-12-25
JusticeZero could you please explain exactly what you mean by saying that Ubuntu runs worse with every update?

---

### Post by JusticeZero on 2007-12-25
I no longer have sound, Cedega stopped working the way I was accustomed for no apparent reason, the system seems to be running a bit slower (can't verify this, though) and it seems like i'm getting more erratic behaviour in applications such as Firefox plugins. Also, sometimes reboots fail to initialize GNOME correctly.
A major issue is that I have to pay for bandwidth, so if I can avoid having to format and re-download the entire thing, it's a plus.

---

### Post by zvacet on 2007-12-25
>  How can I do a reinstall without having to remember and re-download all the packages I have installed from scratch?

You can do it with [APTonCD](http://aptoncd.sourceforge.net/download.html),but maybe your OS is slowing down because you never cleaned it.so you have many packages you don´t need anymore.If you want to remove them run

```
sudo apt-get autoremove
```

```
sudo apt-get autoclean
```

but if you want to keep them all on CD or DVD use APTonCD.

---

### Post by JusticeZero on 2007-12-25
The slowdown is mildly annoying - the fact that my sound stopped working along with Cedega and the sudden unreliability of rebooting and feeling confident of getting GNOME to run right, however, is downright infuriating.

---

### Post by PmDematagoda on 2007-12-25
Could you post the result of:-

```
cat /etc/apt/sources.list
```

---

### Post by JusticeZero on 2007-12-25
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse

---

### Post by ugm6hr on 2007-12-25
> **JusticeZero said:**
> Ubunto is running worse and worse over time as it updates things. How can I do a reinstall without having to remember and re-download all the packages I have installed from scratch?

All updates and packages installed from Synaptic are stored in /var/cache/apt/archives

You could just back up all the .debs there, and copy them back after your re-install (using sudo).

You would still have to select and re-install from Synaptic though (or else double-click all files in turn).

---

### Post by glantucan on 2007-12-29
I must go further, 
What if you want to upgrade to gutsy from feisty, but without the automatic upgrade, which could be a disaster if you installed packages from non official repos or manually (compiling from sources) 
How could you obtain the list of installed packages and tel synaptic to install that list of packages?

Am I asking for too much?

Cheers
Glantu

---

