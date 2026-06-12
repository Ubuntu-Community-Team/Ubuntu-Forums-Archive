---
title: "Ubuntu 18.04 Nvidia fails on Samba install"
date: 2019-07-22
forum: General Help
---

### Post by kangus-m on 2019-07-22
The final error is "Failed on broken package" 

sudo apt-get install samba -y

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: python-samba but it is not going to be installed
         Depends: samba-common-bin (= 2:4.7.6+dfsg~ubuntu-0ubuntu2) but it is not going to be installed
         Depends: samba-libs (= 2:4.7.6+dfsg~ubuntu-0ubuntu2) but 2:4.7.6+dfsg~ubuntu-0ubuntu2.11 is to be installed
         Recommends: attr but it is not going to be installed
         Recommends: samba-dsdb-modules but it is not going to be installed
         Recommends: samba-vfs-modules but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by #&amp;thj^% on 2019-07-22
Try this and post back any errors:
```
sudo apt install -f
```
Mine:
```
apt policy samba
samba:
  Installed: 2:4.10.0+dfsg-0ubuntu2.2
  Candidate: 2:4.10.0+dfsg-0ubuntu2.2
  Version table:
 *** 2:4.10.0+dfsg-0ubuntu2.2 500
        500 http://us.archive.ubuntu.com/ubuntu disco-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu disco-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2:4.10.0+dfsg-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu disco/main amd64 Packages
```
Depends needed:
```
apt depends samba
samba
  PreDepends: dpkg (>= 1.15.6~)
    dpkg:i386
  Depends: adduser
  Depends: libpam-modules
  Depends: libpam-runtime (>= 1.0.1-11)
  Depends: lsb-base (>= 4.1+Debian)
  Depends: procps
    procps:i386
  Depends: python3 (<< 3.8)
  Depends: python3-dnspython
  Depends: python3-samba
  Depends: samba-common (= 2:4.10.0+dfsg-0ubuntu2.2)
  Depends: samba-common-bin (= 2:4.10.0+dfsg-0ubuntu2.2)
  Depends: tdb-tools
  Depends: python3 (>= 3.7~)
  Depends: <python3:any>
    python3:i386
    python3
  Depends: libbsd0 (>= 0.6.0)
  Depends: libc6 (>= 2.14)
  Depends: libldb1 (>= 2:1.5.3)
  Depends: libpopt0 (>= 1.14)
  Depends: libpython3.7 (>= 3.7.0)
  Depends: libtalloc2 (>= 2.0.4~git20101213)
  Depends: libtdb1 (>= 1.2.7+git20101214)
  Depends: libtevent0 (>= 0.9.16)
  Depends: libwbclient0 (= 2:4.10.0+dfsg-0ubuntu2.2)
  Depends: samba-libs (= 2:4.10.0+dfsg-0ubuntu2.2)
  Recommends: attr
    attr:i386
  Recommends: logrotate
    logrotate:i386
  Recommends: samba-dsdb-modules
  Recommends: samba-vfs-modules
  Suggests: bind9 (>= 1:9.5.1)
  Suggests: bind9utils
  Suggests: ctdb
    ctdb:i386
  Suggests: ldb-tools
 |Suggests: ntp
  Suggests: chrony (>= 3.0-1)
  Suggests: smbldap-tools
  Suggests: ufw
  Suggests: winbind
  Enhances: bind9
  Enhances: ntp

```

---

### Post by kangus-m on 2019-07-22
sudo apt install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

kevin@Nvidia:~$ apt policy samba
samba:
  Installed: (none)
  Candidate: 2:4.7.6+dfsg~ubuntu-0ubuntu2
  Version table:
     2:4.7.6+dfsg~ubuntu-0ubuntu2 500
        500 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic/main arm64 Packages

I'm returning 2.4.7 while yours appears to be 2.4.10

From my sources.list:
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) bionic main restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) bionic universe

---

### Post by #&amp;thj^% on 2019-07-23
> **kangus-m said:**
> 
I'm returning 2.4.7 while yours appears to be 2.4.10

From my sources.list:
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) bionic main restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) bionic universe

Ah, I "think" I have the problem:
```
cat /etc/apt/sources.list
```
You will need to add the missing repos with:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
```
Now update and upgrade, and try again to install samba.
The reason for a newer samba on my end is I'm using 19.04 atm.
Also what are the specs for your machine:
```
inxi -FC
```

---

### Post by kangus-m on 2019-07-29
added:
```
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
```


but the update shows errors:
```
kevin@Nvidia:/etc/apt$ sudo apt update
Get:1 file:/var/cuda-repo-10-0-local-10.0.166  InRelease
Ign:1 file:/var/cuda-repo-10-0-local-10.0.166  InRelease
Get:2 file:/var/visionworks-repo  InRelease
Ign:2 file:/var/visionworks-repo  InRelease
Get:3 file:/var/visionworks-sfm-repo  InRelease
Ign:3 file:/var/visionworks-sfm-repo  InRelease
Get:4 file:/var/visionworks-tracking-repo  InRelease
Ign:4 file:/var/visionworks-tracking-repo  InRelease
Get:5 file:/var/cuda-repo-10-0-local-10.0.166  Release [574 B]
Get:6 file:/var/visionworks-repo  Release [1,999 B]
Get:7 file:/var/visionworks-sfm-repo  Release [2,003 B]
Get:8 file:/var/visionworks-tracking-repo  Release [2,008 B]
Get:5 file:/var/cuda-repo-10-0-local-10.0.166  Release [574 B]
Get:6 file:/var/visionworks-repo  Release [1,999 B]
Get:7 file:/var/visionworks-sfm-repo  Release [2,003 B]
Get:8 file:/var/visionworks-tracking-repo  Release [2,008 B]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease [242 kB]
Hit:11 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic InRelease
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main arm64 Packages
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main Translation-en [516 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main arm64 DEP-11 Metadata [472 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main DEP-11 48x48 Icons [118 kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main DEP-11 64x64 Icons [245 kB]
Ign:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/restricted arm64 Packages
Get:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/restricted Translation-en [3,584 B]
Ign:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe arm64 Packages
Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe Translation-en [4,941 kB]
Get:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe arm64 DEP-11 Metadata [3,243 kB]
Get:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe DEP-11 48x48 Icons [2,151 kB]
Get:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe DEP-11 64x64 Icons [8,420 kB]
Ign:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse arm64 Packages
Get:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse Translation-en [108 kB]
Get:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse arm64 DEP-11 Metadata [44.4 kB]
Get:31 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse DEP-11 48x48 Icons [8,931 B]
Get:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse DEP-11 64x64 Icons [225 kB]
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main arm64 Packages
Ign:33 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe arm64 Packages
Get:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [296 kB]
Get:35 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe arm64 DEP-11 Metadata [246 kB]
Get:36 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 48x48 Icons [197 kB]
Get:37 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [423 kB]
Ign:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse arm64 Packages
Get:39 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse Translation-en [3,556 B]
Get:40 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse DEP-11 48x48 Icons [29 B]
Get:41 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse DEP-11 64x64 Icons [2,638 B]
Ign:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/restricted arm64 Packages
Ign:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe arm64 Packages
Ign:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse arm64 Packages
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main arm64 Packages
Ign:33 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe arm64 Packages
Ign:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse arm64 Packages
Ign:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/restricted arm64 Packages
Ign:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe arm64 Packages
Ign:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse arm64 Packages
Err:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main arm64 Packages
  404  Not Found [IP: 2001:67c:1562::16 80]
Ign:33 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe arm64 Packages
Ign:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse arm64 Packages
Ign:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/restricted arm64 Packages
Ign:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe arm64 Packages
Ign:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse arm64 Packages
Err:33 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe arm64 Packages
  404  Not Found [IP: 2001:67c:1562::16 80]
Ign:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse arm64 Packages
Fetched 22.0 MB in 8s (2,700 kB/s)
Reading package lists... Done
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-arm64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-arm64/Packages)  404  Not Found [IP: 2001:67c:1562::16 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/universe/binary-arm64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/universe/binary-arm64/Packages)  404  Not Found [IP: 2001:67c:1562::16 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

When I try to install samba I get the same errors:
```
kevin@Nvidia:/etc/apt$ sudo apt install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: python-samba but it is not going to be installed
         Depends: samba-common-bin (= 2:4.7.6+dfsg~ubuntu-0ubuntu2) but it is not going to be installed
         Depends: samba-libs (= 2:4.7.6+dfsg~ubuntu-0ubuntu2) but 2:4.7.6+dfsg~ubuntu-0ubuntu2.11 is to be installed
         Recommends: attr but it is not going to be installed
         Recommends: samba-dsdb-modules but it is not going to be installed
         Recommends: samba-vfs-modules but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by deadflowr on 2019-07-29
arm packages should be in the ports repositories.
[https://wiki.ubuntu.com/UbuntuDevelopment/PackageArchive#Ports]("https://wiki.ubuntu.com/UbuntuDevelopment/PackageArchive#Ports")

**Edit:** It looks like you only have it set up for arm64
(You can confirm with the commands
```
dpkg --print-architecture
dpkg --print-foreign-architectures
```
--print-architecture prints the systems default architecture
and --print-foreign-architectures prints any added architectures.

I see you have at least one ports.ubuntu.com output in the apt update output.
So you have it set somewhere, but not in the main sources.list.
(Perhaps it's in a file in the /etc/apt/sources.list.d/ directory)

You might consider disabling the sources.list files entries as those are for the main x86 archived packages. (x86 has two architectures: amd64 (64-bit) and i386 (32-bit))
Or if you need the x86 packages add the restriction option to the sources.list entries

Where yours currently says

```
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
```
you add [arch=amd64]
to it like
```
deb [arch=amd64] http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
deb [arch=amd64] http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb [arch=amd64] http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb [arch=amd64] http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb [arch=amd64] http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
```

This forces it to only look for that particular arch-type in those archives.
Of course this depends on what the dpkg commands tell you.
If the only arch-type listed is arm64, then you can just disable the file

(You can either rename the file to something like sources.list.bak or add # to the front of the deb entries to disable them.
I wouldn't delete or recommend removing the file wholesale,
as you might want it later in life.)

That's my rambling two cents

---

### Post by kangus-m on 2019-07-29
This OS is the default image from Nvidia for their Jetson Nano, when I check the OS version it is 18.04

---

### Post by #&amp;thj^% on 2019-07-29
> **kangus-m said:**
> This OS is the default image from Nvidia for their Jetson Nano, when I check the OS version it is 18.04

That would of / should of been stated from the very beginning. Missing details like this can cause you to get very bad information. (Mine for just an example! ;))
And I know nothing of the image your using, so I have nothing relevant to add.
Follow deadflowr advice to get back to the proper source list

---

