---
title: "[SOLVED] update manager errors in Hardy"
date: 2008-06-18
forum: General Help
---

### Post by dopple on 2008-06-18
Hullo. When I hit the "check button on the update manager, I get the error

"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://morgoth.free.fr](http://morgoth.free.fr) dapper-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8CC68B397E2E4741Failed to fetch [http://www.virtualbox.org/debian/dists/gutsy/non-free/binary-i386/Packages.gz](http://www.virtualbox.org/debian/dists/gutsy/non-free/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

I have googled this a few times but cannot find out what the issue is. I had something similar to a while ago when I had to add in the Public key for VirtualBox.

---

### Post by dopple on 2008-06-25
bump.

---

### Post by dopple on 2008-06-25
Here is my sources.list file btw

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe multiverse
#AUTOMATIX REPOS END
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free
deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
deb-src [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) source/
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) dapper-backports main

---

### Post by avtolle on 2008-06-25
AFAIK, automatix is no longer extant. I'd suggest editing the sources.list ```
cp /etc/apt/sources.list /etc/apt/sources.list.bak #make a backup, to be safe
sudo nano /etc/apt/sources.list #opens for editing
``` and comment out (by putting a # before the lines) all references to automatix as well as to any other non-Hardy source. Then, at terminal again```
sudo aptitude update && sudo aptitude safe-upgrade
```and see if updates download and are installed. Oh, and to save the new sources.list, after you have finished editing it, ^o to write, <Enter>to accept the default name, and ^x to exit nano before running the update and safe-upgrade commands.

---

### Post by dopple on 2008-06-25
That's it working now. Cheers. The only problem after commenting out Automatix and any dapper references was
```
Failed to fetch http://www.virtualbox.org/debian/dists/gutsy/non-free/binary-i386/Packages.gz  403 Forbidden
```
And when I went to [http://www.virtualbox.org/debian/](http://www.virtualbox.org/debian/) I saw that sun had taken over virtualBox. So I removed this as well. Thanks again! :KS

---

### Post by nivekyru on 2008-07-05
I am rather new to ubuntu, running 8.04 i open my update manager i download the listed updates and before any updates can be installed i get this error message, 

dpkg: parse error, in file '/var/lib/dpkg/status' near line 26071 package 'ekiga': Depends' field, reference to 'libice6' : version contain ' '
E: Subprocess /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover

---

### Post by nivekyru on 2008-07-05
I am rather new to ubuntu, running 8.04 i open my update manager i download the listed updates and before any updates can be installed i get this error message, 

dpkg: parse error, in file '/var/lib/dpkg/status' near line 26071 package 'ekiga': Depends' field, reference to 'libice6' : version contain ' '
E: Subprocess /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover

This has disabled my ability to update my machine. Thanks in advance

---

### Post by ConstAnton on 2008-07-05
I have just finished updating (not upgrading!) Ubuntu 6.06 (dapper) using
the update manager: in addition to the expected "Your system is up-to-date"
I also get an error message almost identical to the one you got, namely
the update manager complains not being able to find

[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)

although the file IS there, I read it in Firefox, also downloaded it to
the Desktop. The Help for "update manager" mentions, among other things,
the "Preferences" button on the invocation panel: there is NONE!

I would like to add that I stayed with Ubuntu 6.06 because I found that
Ubuntu 8.04 uses more system resources (memory) and is somewhat slower.

I would like to know how to incorporate the above-mentioned file into the
/etc/apt/sources.list which is written in a different format.

---

