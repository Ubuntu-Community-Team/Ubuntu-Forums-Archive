---
title: "Can't install teamviewer after dist-upgrade on 16.04"
date: 2017-11-08
forum: General Help
---

### Post by martijn12 on 2017-11-08
Original problem: 
After an apt dist-upgrade teamviewer and a number of i386 libraries were no longer available.

Root cause:
Repositories in /etc/apt/sources.list had been restricted to [arch=amd64] as both i386 and arm64 were added as foreign architectures. However arm64 isn't available on a number of repositories leading to errors after an apt update. Removing the arch limitation didn't resolve the issue, however changing it to [arch=amd64,i386] did.

Solution:
Adding [arch=amd64,i386] to the repositories listed in /etc/apt/sources.list that gave errors. As in:
```
deb [arch=amd64,i386] http://nl.archive.ubuntu.com/ubuntu/ xenial universe
```





Original post:

I performed a dist-upgrade seeming the amount of packages being held back was starting to stack up considerably, resulting in the following;
```
Start-Date: 2017-11-07  11:18:46Commandline: apt dist-upgrade
Upgrade: libmpx0:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libgcrypt20-dev:amd64 (1.6.5-2ubuntu0.2, 1.6.5-2ubuntu0.3), libgcc-5-dev:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libc6-dbg:amd64 (2.23-0ubuntu5, 2.23-0ubuntu9), libc6-dev:amd64 (2.23-0ubuntu5, 2.23-0ubuntu9), libsystemd0:amd64 (229-4ubuntu16, 229-4ubuntu21), libexpat1-dev:amd64 (2.1.0-7ubuntu0.16.04.2, 2.1.0-7ubuntu0.16.04.3), cpp-5:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), zlib1g:amd64 (1:1.2.8.dfsg-2ubuntu4, 1:1.2.8.dfsg-2ubuntu4.1), libitm1:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libc6:amd64 (2.23-0ubuntu5, 2.23-0ubuntu9), libcilkrts5:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), zlib1g-dev:amd64 (1:1.2.8.dfsg-2ubuntu4, 1:1.2.8.dfsg-2ubuntu4.1), libasan2:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libquadmath0:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libexpat1:amd64 (2.1.0-7ubuntu0.16.04.2, 2.1.0-7ubuntu0.16.04.3), gcc-5-base:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libstdc++-5-dev:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libtsan0:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libubsan0:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), g++-5:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libgfortran3:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libuuid1:amd64 (2.27.1-6ubuntu3.2, 2.27.1-6ubuntu3.3), gcc-5:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libgcrypt20:amd64 (1.6.5-2ubuntu0.2, 1.6.5-2ubuntu0.3), libc6-i386:amd64 (2.23-0ubuntu5, 2.23-0ubuntu9), libpam-systemd:amd64 (229-4ubuntu16, 229-4ubuntu21), liblsan0:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), systemd:amd64 (229-4ubuntu16, 229-4ubuntu21), libgomp1:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libssl-dev:amd64 (1.0.2g-1ubuntu4.6, 1.0.2g-1ubuntu4.9), uuid-dev:amd64 (2.27.1-6ubuntu3.2, 2.27.1-6ubuntu3.3), libc-dev-bin:amd64 (2.23-0ubuntu5, 2.23-0ubuntu9), libfreetype6:amd64 (2.6.1-0.1ubuntu2, 2.6.1-0.1ubuntu2.3), libatomic1:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libcc1-0:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libstdc++6:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libssl1.0.0:amd64 (1.0.2g-1ubuntu4.6, 1.0.2g-1ubuntu4.9)
Remove: libxdmcp6:i386 (1:1.1.2-1.1), libcomerr2:i386 (1.42.13-1ubuntu1), gns3-iou:amd64 (0.0.1~xenial1), libdbus-1-3:i386 (1.10.6-1ubuntu3.3), libsystemd0:i386 (229-4ubuntu16), libxrender1:i386 (1:0.9.9-0ubuntu1), libgpg-error0:i386 (1.21-2ubuntu1), zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4), libc6:i386 (2.23-0ubuntu5), libjpeg62:i386 (1:6b2-2), libx11-6:i386 (2:1.6.3-1ubuntu2), libexpat1:i386 (2.1.0-7ubuntu0.16.04.2), libgcc1:i386 (1:6.0.1-0ubuntu1), libsm6:i386 (2:1.2.2-1), gcc-5-base:i386 (5.4.0-6ubuntu1~16.04.4), libxau6:i386 (1:1.0.8-1), libtinfo5:i386 (6.0+20160213-1ubuntu1), libxcb1:i386 (1.11.1-1ubuntu1), libxtst6:i386 (2:1.2.2-1), libpcre3:i386 (2:8.38-3.1), libxinerama1:i386 (2:1.1.3-1), libuuid1:i386 (2.27.1-6ubuntu3.2), libgcrypt20:i386 (1.6.5-2ubuntu0.2), libselinux1:i386 (2.4-3build2), libxrandr2:i386 (2:1.5.0-1), libxfixes3:i386 (1:5.0.1-2), libfontconfig1:i386 (2.11.94-0ubuntu1.1), libasound2:i386 (1.1.0-0ubuntu1), libxdamage1:i386 (1:1.1.4-2), libfreetype6:i386 (2.6.1-0.1ubuntu2), libice6:i386 (2:1.0.9-1), liblzma5:i386 (5.1.1alpha+20120614-2ubuntu2), libpng12-0:i386 (1.2.54-1ubuntu1), libssl1.0.0:i386 (1.0.2g-1ubuntu4.6), libxext6:i386 (2:1.3.3-1), teamviewer:i386 (12.0.85001)
End-Date: 2017-11-07  11:19:09

```

Long story short, a lot of i386 libraries are no longer available because they've been replaced. Unfortunately, I lost teamviewer as well. I've been trying various things to get it back up and running.

For teamviewer_12.0.85001_i386.deb
```
The following packages have unmet dependencies:
 teamviewer:i386 : Depends: libc6:i386 (>= 2.11) but it is not installable
                   Depends: libgcc1:i386 but it is not installable
                   Depends: libasound2:i386 but it is not installable
                   Depends: libdbus-1-3:i386 but it is not installable
                   Depends: libexpat1:i386 but it is not installable
                   Depends: libfontconfig1:i386 but it is not installable
                   Depends: libfreetype6:i386 but it is not installable
                   Depends: libjpeg62:i386 but it is not installable
                   Depends: libsm6:i386 but it is not installable
                   Depends: libxdamage1:i386 but it is not installable
                   Depends: libxext6:i386 but it is not installable
                   Depends: libxfixes3:i386 but it is not installable
                   Depends: libxinerama1:i386 but it is not installable
                   Depends: libxrandr2:i386 but it is not installable
                   Depends: libxrender1:i386 but it is not installable
                   Depends: libxtst6:i386 but it is not installable
                   Depends: zlib1g:i386 but it is not installable

```

```
Package libc6:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libc6 libdb1-compat tzdata initscripts

```

This had me thinking I was just missing i386 completely, but it's still shown;
```
dpkg --print-foreign-architectures
i386
arm64
```

I will note my repository list specifies amd64 on many of the repositories which could be relevant? I've tried messing with it briefly, but I'm a bit hesitant/worried I'll break it. Should I drop the [arch=amd64] and reload? It's on the edge of what I'm comfortable with.
```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb [arch=amd64] http://nl.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://nl.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [arch=amd64] http://nl.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://nl.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [arch=amd64] http://nl.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://nl.archive.ubuntu.com/ubuntu/ xenial universe
deb [arch=amd64] http://nl.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://nl.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [arch=amd64] http://nl.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ xenial multiverse
deb [arch=amd64] http://nl.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [arch=amd64] http://nl.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb [arch=amd64] http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb [arch=amd64] http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse



```



For teamviewer_12.0.85001_amd64.deb

```
The following packages have unmet dependencies:
 teamviewer : Depends: lib32asound2 but it is not installable              Depends: lib32z1 but it is not installed
              Depends: ia32-libs but it is not installable

```

Apparently ia32-libs is horridly outdated, so I just stopped there.

I'd much appreciate any guidance you guys can give me.

---

### Post by #&amp;thj^% on 2017-11-08
Yuck and not sure I can help but..Did you see this?

> However the following packages replace it:
  libc6 libdb1-compat tzdata initscripts 

try to:
```
sudo apt install libc6 libdb1-compat tzdata initscripts
```
Followed with:
```
sudo apt -f install
```

---

### Post by #&amp;thj^% on 2017-11-08
Sorry I did not see where you enabled "architecture i386" first.
Anyway I just installed it with this method:
```
sudo dpkg --add-architecture i386 && sudo apt-get update
``` 

Now install dependencies for TeamViewer.

```
sudo apt-get install libdbus-1-3:i386 libasound2:i386 libexpat1:i386 libfontconfig1:i386 libfreetype6:i386 libjpeg62:i386 libpng12-0:i386 libsm6:i386 libxdamage1:i386 libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxrandr2:i386 libxrender1:i386 libxtst6:i386 zlib1g:i386 libc6:i386
```

Then install TeamViewer from the path it is downloaded.

```
sudo dpkg -i teamviewer*.deb
```

And this is the result:

```
apt policy teamviewer
teamviewer:i386:
  Installed: 12.0.85001
  Candidate: 12.0.85001
  Version table:
 *** 12.0.85001 100
        100 /var/lib/dpkg/status
```

```
lsb_release -a && echo $DESKTOP_SESSION
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial
ubuntu

```

---

### Post by martijn12 on 2017-11-09
Thanks a lot for your reply! it sounds like we're on the same path, but I'm just getting different results. Specifically I can't satisfy the i386 dependencies.

```
sudo apt-get install libc6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libc6 libdb1-compat tzdata initscripts


E: Package 'libc6:i386' has no installation candidate
```

Meanwhile libc6 is installed from the amd64 repo.

```

sudo apt show libc6 
Package: libc6
Version: 2.23-0ubuntu9
Priority: required
Section: libs
Source: glibc
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 11,2 MB
Depends: libgcc1
Suggests: glibc-doc, debconf | debconf-2.0, locales
Breaks: hurd (<< 1:0.5.git20140203-1), libtirpc1 (<< 0.2.3), locales (<< 2.23), locales-all (<< 2.23), lsb-core (<= 3.2-27), nscd (<< 2.23)
Replaces: libc6-amd64
Homepage: http://www.gnu.org/software/libc/libc.html
Task: minimal
Supported: 5y
Download-Size: 2586 kB
APT-Manual-Installed: yes
APT-Sources: http://nl.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
Description: GNU C Library: Shared libraries
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C library
 and the standard math library, as well as many others.


N: There is 1 additional record. Please use the '-a' switch to see it

```

So that's why I'm wondering if the problem is with the repositories. Which made sense to me, I restricted some of them to amd64 because I messed around with crosscompliling to arm64 and that throws errors for repositories not found. I could see how that could mess things up. So I took out all the [arch=amd64] specifications in my sources.list and ran an apt update. (I figured if this worked I could just change it to [arch=amd64,i386], best to keep it clean until it works).

```

sudo apt update
Get:1 file:/var/cuda-repo-8-0-local  InRelease
Ign:1 file:/var/cuda-repo-8-0-local  InRelease
Get:2 file:/var/libopencv4tegra-repo  InRelease
Ign:2 file:/var/libopencv4tegra-repo  InRelease
Get:3 file:/var/visionworks-repo  InRelease
Ign:3 file:/var/visionworks-repo  InRelease
Get:4 file:/var/visionworks-sfm-repo  InRelease
Ign:4 file:/var/visionworks-sfm-repo  InRelease
Get:5 file:/var/visionworks-tracking-repo  InRelease
Ign:5 file:/var/visionworks-tracking-repo  InRelease
Get:6 file:/var/cuda-repo-8-0-local  Release [574 B]
Get:7 file:/var/libopencv4tegra-repo  Release [347 B]
Get:8 file:/var/visionworks-repo  Release [1999 B]                                                                                                                                                    
Get:9 file:/var/visionworks-sfm-repo  Release [2003 B]
Get:6 file:/var/cuda-repo-8-0-local  Release [574 B]
Get:10 file:/var/visionworks-tracking-repo  Release [2008 B]
Get:7 file:/var/libopencv4tegra-repo  Release [347 B]
Get:8 file:/var/visionworks-repo  Release [1999 B]
Get:9 file:/var/visionworks-sfm-repo  Release [2003 B]
Get:10 file:/var/visionworks-tracking-repo  Release [2008 B]
Hit:11 http://nl.archive.ubuntu.com/ubuntu xenial InRelease
Hit:12 http://ppa.launchpad.net/gns3/ppa/ubuntu xenial InRelease
Hit:13 http://nl.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:14 http://nl.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:16 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease
Get:20 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:21 http://archive.canonical.com/ubuntu xenial InRelease                                                                                                         
Hit:22 http://repo.steampowered.com/steam precise InRelease                                                                                                         
Ign:24 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                   
Ign:25 http://linux.dropbox.com/ubuntu wily InRelease                                                      
Get:26 http://linux.dropbox.com/ubuntu wily Release [6596 B]                         
Get:27 http://nl.archive.ubuntu.com/ubuntu xenial/main i386 Packages [1196 kB]                                     
Ign:28 http://nl.archive.ubuntu.com/ubuntu xenial/main arm64 Packages                                                                                                     
Get:29 http://nl.archive.ubuntu.com/ubuntu xenial/restricted i386 Packages [8684 B]                                                                                       
Get:30 http://nl.archive.ubuntu.com/ubuntu xenial/universe i386 Packages [7512 kB]                                                                                       
Ign:31 http://nl.archive.ubuntu.com/ubuntu xenial/universe arm64 Packages                                                                                                 
Get:32 http://nl.archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages [140 kB]                                                                                       
Ign:33 http://nl.archive.ubuntu.com/ubuntu xenial/multiverse arm64 Packages                                                                                                   
Ign:28 http://nl.archive.ubuntu.com/ubuntu xenial/main arm64 Packages                                                                                                         
Get:34 http://nl.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [617 kB]                                                       
Ign:35 http://nl.archive.ubuntu.com/ubuntu xenial-updates/main arm64 Packages                                                              
Get:36 http://nl.archive.ubuntu.com/ubuntu xenial-updates/restricted i386 Packages [8072 B]                                                
Get:37 http://nl.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [517 kB]                                                  
Ign:38 http://nl.archive.ubuntu.com/ubuntu xenial-updates/universe arm64 Packages                                                          
Get:39 http://nl.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [15,3 kB]        
Ign:40 http://nl.archive.ubuntu.com/ubuntu xenial-updates/multiverse arm64 Packages                                                       
Get:41 http://nl.archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages [4852 B]                                                   
Ign:42 http://nl.archive.ubuntu.com/ubuntu xenial-backports/main arm64 Packages                                                           
Get:43 http://nl.archive.ubuntu.com/ubuntu xenial-backports/universe i386 Packages [5896 B]                                               
Ign:45 http://nl.archive.ubuntu.com/ubuntu xenial-backports/universe arm64 Packages                                                       
Ign:31 http://nl.archive.ubuntu.com/ubuntu xenial/universe arm64 Packages                            
Ign:33 http://nl.archive.ubuntu.com/ubuntu xenial/multiverse arm64 Packages    
Ign:28 http://nl.archive.ubuntu.com/ubuntu xenial/main arm64 Packages          
Ign:35 http://nl.archive.ubuntu.com/ubuntu xenial-updates/main arm64 Packages  
Ign:38 http://nl.archive.ubuntu.com/ubuntu xenial-updates/universe arm64 Packages
Ign:40 http://nl.archive.ubuntu.com/ubuntu xenial-updates/multiverse arm64 Packages
Ign:42 http://nl.archive.ubuntu.com/ubuntu xenial-backports/main arm64 Packages
Ign:45 http://nl.archive.ubuntu.com/ubuntu xenial-backports/universe arm64 Packages                             
Ign:31 http://nl.archive.ubuntu.com/ubuntu xenial/universe arm64 Packages                                       
Ign:33 http://nl.archive.ubuntu.com/ubuntu xenial/multiverse arm64 Packages
Err:28 http://nl.archive.ubuntu.com/ubuntu xenial/main arm64 Packages     
  404  Not Found [IP: 2001:7b8:3:37::21:3 80]
Ign:35 http://nl.archive.ubuntu.com/ubuntu xenial-updates/main arm64 Packages
Ign:38 http://nl.archive.ubuntu.com/ubuntu xenial-updates/universe arm64 Packages
Ign:40 http://nl.archive.ubuntu.com/ubuntu xenial-updates/multiverse arm64 Packages
Ign:42 http://nl.archive.ubuntu.com/ubuntu xenial-backports/main arm64 Packages
Ign:45 http://nl.archive.ubuntu.com/ubuntu xenial-backports/universe arm64 Packages
Ign:31 http://nl.archive.ubuntu.com/ubuntu xenial/universe arm64 Packages 
Ign:33 http://nl.archive.ubuntu.com/ubuntu xenial/multiverse arm64 Packages
Err:35 http://nl.archive.ubuntu.com/ubuntu xenial-updates/main arm64 Packages
  404  Not Found [IP: 2001:7b8:3:37::21:3 80]
Ign:38 http://nl.archive.ubuntu.com/ubuntu xenial-updates/universe arm64 Packages
Ign:40 http://nl.archive.ubuntu.com/ubuntu xenial-updates/multiverse arm64 Packages
Err:42 http://nl.archive.ubuntu.com/ubuntu xenial-backports/main arm64 Packages
  404  Not Found [IP: 2001:7b8:3:37::21:3 80]
Get:46 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [353 kB]
Ign:45 http://nl.archive.ubuntu.com/ubuntu xenial-backports/universe arm64 Packages                        
Ign:47 http://security.ubuntu.com/ubuntu xenial-security/main arm64 Packages
Get:48 http://security.ubuntu.com/ubuntu xenial-security/restricted i386 Packages [7472 B]
Get:49 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [153 kB]
Ign:50 http://security.ubuntu.com/ubuntu xenial-security/universe arm64 Packages     
Ign:47 http://security.ubuntu.com/ubuntu xenial-security/main arm64 Packages         
Ign:50 http://security.ubuntu.com/ubuntu xenial-security/universe arm64 Packages
Ign:47 http://security.ubuntu.com/ubuntu xenial-security/main arm64 Packages
Ign:50 http://security.ubuntu.com/ubuntu xenial-security/universe arm64 Packages
Hit:51 http://dl.google.com/linux/chrome/deb stable Release
Err:47 http://security.ubuntu.com/ubuntu xenial-security/main arm64 Packages   
  404  Not Found [IP: 2001:67c:1562::16 80]
Ign:50 http://security.ubuntu.com/ubuntu xenial-security/universe arm64 Packages
Fetched 109 kB in 1s (89,7 kB/s)
Reading package lists... Done
W: file:///var/cuda-repo-8-0-local/Release.gpg: Signature by key 889BEE522DA690103C4B085ED88C3D385C37D3BE uses weak digest algorithm (SHA1)
W: Invalid 'Date' entry in Release file /var/lib/apt/lists/_var_cuda-repo-8-0-local_Release
W: Invalid 'Date' entry in Release file /var/lib/apt/lists/_var_libopencv4tegra-repo_Release
E: Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/xenial/main/binary-arm64/Packages  404  Not Found [IP: 2001:7b8:3:37::21:3 80]
E: Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-arm64/Packages  404  Not Found [IP: 2001:7b8:3:37::21:3 80]
E: Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/xenial-backports/main/binary-arm64/Packages  404  Not Found [IP: 2001:7b8:3:37::21:3 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/main/binary-arm64/Packages  404  Not Found [IP: 2001:67c:1562::16 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

```


But I still can't get libc6:i386

```

sudo apt-get install libc6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libc6 libdb1-compat tzdata initscripts


E: Package 'libc6:i386' has no installation candidate

```

I feel like I'm close, but I'm just missing that last step.

---

### Post by martijn12 on 2017-11-09
Update: Adding[COLOR=#000000] [/COLOR][arch=amd64,i386] everywhere worked! Just removing the arch specifier completely doesn't have the same effect as specifying amd64 and i386 apparently. Maybe because the arm64 architecture resulted in 404 errors?

Thanks a lot for the assistance fallen, I was rather lost and you showed me I was on the right path.

---

### Post by #&amp;thj^% on 2017-11-09
Thanks for posting your fix for your usage.
It would be helpful if you marked this as solved, And with changing the Title of your thread adding this to already stated:"[arch=amd64,i386] "
Thanks Cheers

---

