---
title: "problem with apt-get update"
date: 2007-10-07
forum: General Help
---

### Post by Ademon on 2007-10-07
Hello all,

I am using Kubuntu 7.04, i tried today to refresh my repositories list but something is wrong, when i use sudo apt-get update
```
acheron@acheron-laptop:~$ sudo apt-get update
Password:
Err http://wine.lowvoice.nl feisty Release.gpg
  Could not resolve ‘wine.lowvoice.nl’
Get: 1 http://gb.archive.ubuntu.com feisty Release.gpg [191B]
Hit http://gb.archive.ubuntu.com feisty/main Translation-en_GB
Get: 2 http://security.ubuntu.com feisty-security Release.gpg [191B]
Err http://wine.lowvoice.nl feisty/main Translation-en_GB
  Could not resolve ‘wine.lowvoice.nl’
Ign http://wine.lowvoice.nl feisty Release
Ign http://wine.lowvoice.nl feisty/main Packages
Get: 3 http://www.getautomatix.com feisty Release.gpg [189B]
Get: 4 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://www.getautomatix.com feisty/main Translation-en_GB
Get: 5 http://oss.oracle.com unstable Release.gpg [189B]
Err http://wine.lowvoice.nl feisty/main Packages
  Could not resolve ‘wine.lowvoice.nl’
Get: 6 http://archive.canonical.com feisty-commercial Release.gpg [191B]
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB
Ign http://security.ubuntu.com feisty-security/main Translation-en_GB
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_GB
Ign http://oss.oracle.com unstable/main Translation-en_GB
Ign http://archive.canonical.com feisty-commercial/main Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB
Get: 7 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://oss.oracle.com unstable/non-free Translation-en_GB
Hit http://oss.oracle.com unstable Release
Hit http://archive.canonical.com feisty-commercial Release
Ign http://security.ubuntu.com feisty-security/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_GB
Hit http://www.getautomatix.com feisty Release
Hit http://oss.oracle.com unstable/main Packages
Hit http://archive.canonical.com feisty-commercial/main Packages
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB
Hit http://security.ubuntu.com feisty-security Release
Hit http://gb.archive.ubuntu.com feisty Release
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com feisty-updates Release
Get: 8 http://archive.ubuntu.com feisty-updates Release.gpg [191B]
Err http://security.ubuntu.com feisty-security Release

Get: 9 http://security.ubuntu.com feisty-security Release [50.9kB]
Hit http://gb.archive.ubuntu.com feisty/main Packages
Hit http://gb.archive.ubuntu.com feisty/restricted Packages
Hit http://gb.archive.ubuntu.com feisty/main Sources
Ign http://security.ubuntu.com feisty-security Release
Hit http://gb.archive.ubuntu.com feisty/restricted Sources
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://gb.archive.ubuntu.com feisty/universe Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://gb.archive.ubuntu.com feisty/universe Sources
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://gb.archive.ubuntu.com feisty/multiverse Packages
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://gb.archive.ubuntu.com feisty/multiverse Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://gb.archive.ubuntu.com feisty-updates/main Sources
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://www.getautomatix.com feisty/main Packages
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_GB
Hit http://oss.oracle.com unstable/non-free Packages
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_GB
Get: 10 http://archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-security/main Translation-en_GB
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_GB
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_GB
Hit http://archive.ubuntu.com feisty-backports Release
Hit http://archive.ubuntu.com feisty-updates Release
Hit http://archive.ubuntu.com feisty-security Release
Hit http://archive.ubuntu.com feisty-backports/main Packages
Hit http://archive.ubuntu.com feisty-backports/restricted Packages
Hit http://archive.ubuntu.com feisty-backports/universe Packages
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://archive.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty-security/restricted Packages
Hit http://archive.ubuntu.com feisty-security/universe Packages
Hit http://archive.ubuntu.com feisty-security/multiverse Packages
Fetched 51.1kB in 6s (8397B/s)
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg  Could not resolve ‘wine.lowvoice.nl’
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_GB.bz2  Could not resolve ‘wine.lowvoice.nl’
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz  Could not resolve ‘wine.lowvoice.nl’
Reading package lists... Done
W: GPG error: http://security.ubuntu.com feisty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

anybody knows why this is happening?:confused:

---

### Post by PmDematagoda on 2007-10-07
Could you post your sources.list file using:-
```

sudo gedit /etc/apt/sources.list
```

---

### Post by Ademon on 2007-10-07
Here is my sources.list file.
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt feisty main

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://oss.oracle.com/debian unstable main non-free
deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
```

---

### Post by PmDematagoda on 2007-10-07
Make the following change:-

```
#deb http://wine.lowvoice.nl/apt feisty main
```

And try again.

---

### Post by Ademon on 2007-10-07
Now it seems it stuck at 

```
acheron@acheron-laptop:~$ sudo apt-get update
Get: 1 http://www.getautomatix.com feisty Release.gpg [189B]
Get: 2 http://oss.oracle.com unstable Release.gpg [189B]
Get: 3 http://security.ubuntu.com feisty-security Release.gpg [191B]
Get: 4 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Get: 5 http://gb.archive.ubuntu.com feisty Release.gpg [191B]
Hit http://gb.archive.ubuntu.com feisty/main Translation-en_GB
Ign http://oss.oracle.com unstable/main Translation-en_GB
Ign http://security.ubuntu.com feisty-security/main Translation-en_GB
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_GB
Get: 6 http://archive.canonical.com feisty-commercial Release.gpg [191B]
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB
Ign http://oss.oracle.com unstable/non-free Translation-en_GB
Hit http://oss.oracle.com unstable Release
Ign http://archive.canonical.com feisty-commercial/main Translation-en_GB
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB
Get: 7 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]
Hit http://archive.canonical.com feisty-commercial Release
Ign http://security.ubuntu.com feisty-security/universe Translation-en_GB
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB
Hit http://oss.oracle.com unstable/main Packages
Hit http://archive.canonical.com feisty-commercial/main Packages
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com feisty-security Release
Err http://security.ubuntu.com feisty-security Release
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB
Get: 8 http://security.ubuntu.com feisty-security Release [50.9kB]
Get: 9 http://archive.ubuntu.com feisty-updates Release.gpg [191B]
Hit http://gb.archive.ubuntu.com feisty Release
Hit http://gb.archive.ubuntu.com feisty-updates Release
Hit http://gb.archive.ubuntu.com feisty/main Packages
Hit http://gb.archive.ubuntu.com feisty/restricted Packages
Ign http://security.ubuntu.com feisty-security Release
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://gb.archive.ubuntu.com feisty/main Sources
Hit http://gb.archive.ubuntu.com feisty/restricted Sources
Hit http://gb.archive.ubuntu.com feisty/universe Packages
Hit http://gb.archive.ubuntu.com feisty/universe Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://gb.archive.ubuntu.com feisty/multiverse Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://gb.archive.ubuntu.com feisty/multiverse Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://gb.archive.ubuntu.com feisty-updates/main Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://oss.oracle.com unstable/non-free Packages
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_GB
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_GB
Get: 10 http://archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-security/main Translation-en_GB
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_GB
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_GB
Hit http://archive.ubuntu.com feisty-backports Release
Hit http://archive.ubuntu.com feisty-updates Release
Hit http://archive.ubuntu.com feisty-security Release
Hit http://archive.ubuntu.com feisty-backports/main Packages
Hit http://archive.ubuntu.com feisty-backports/restricted Packages
Hit http://archive.ubuntu.com feisty-backports/universe Packages
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://archive.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty-security/restricted Packages
Hit http://archive.ubuntu.com feisty-security/universe Packages
Hit http://archive.ubuntu.com feisty-security/multiverse Packages
Err http://www.getautomatix.com feisty/main Translation-en_GB
Connection failed
99% [Waiting for headers]
acheron@acheron-laptop:~$
```

---

### Post by Ademon on 2007-10-07
If after the fail i run it again i get the same Errors and Ignores and it stucks at the same point
```
Hit http://archive.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty-security/restricted Packages
Hit http://archive.ubuntu.com feisty-security/universe Packages
Hit http://archive.ubuntu.com feisty-security/multiverse Packages
99% [Waiting for headers]
```

---

### Post by PmDematagoda on 2007-10-07
Ok, deactivate ALL Automatix repos and try again.

---

### Post by Ademon on 2007-10-07
I comment:

#deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main
#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
(propably automatix site is down i cant get connected at [www.getautomatix.com](www.getautomatix.com))

but now i am getting a new error:
```
Hit http://oss.oracle.com unstable/non-free Packages
Fetched 51.1kB in 1s (33.4kB/s)
Reading package lists... Done
W: GPG error: http://security.ubuntu.com feisty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```

Everything were smoothly until 2 hours ago!?!

---

### Post by PmDematagoda on 2007-10-07
Okay disable all addresses with "security" infront such as:-
```

deb http://security.ubuntu.com/ubuntu feisty-security universe
```

---

### Post by Cruicky on 2007-10-07
I've also had this problem. I have found the cause to be one of the feisty-security mirrors appears to be out of sync and the gpg signature is coming from one server and the package list is coming from another, therefore they fail to verify.

If you compare [http://91.189.88.31/ubuntu/dists/feisty-security/Release](http://91.189.88.31/ubuntu/dists/feisty-security/Release) to [http://91.189.88.38/ubuntu/dists/feisty-security/Release](http://91.189.88.38/ubuntu/dists/feisty-security/Release) you will see the timestamp difference.

I fixed this problem by adding an entry to /etc/hosts which forced apt-get to use just one of the mirrors, which I will remove after the mirrors appear to be in sync again.

If you want to do this, add: -
```
91.189.88.31    security.ubuntu.com
```
to the bottom of the hosts file using
```
sudo gedit /etc/hosts
```

After adding this temporary workaround I no longer receive verification errors.

---

