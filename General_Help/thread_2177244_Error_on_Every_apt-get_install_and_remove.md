---
title: "Error on Every apt-get install and remove"
date: 2013-09-27
forum: General Help
---

### Post by seethru on 2013-09-27
Getting this whenever I run an apt-get install or remove. It doesn't appear to affect anything, but it's very annoying.


```
E: Sub-process returned an error code
```

This started when I ran into a problem with python and pkg_configure. I've since fixed that but this issue remains. This is an ubuntu server so no GUI for me to use to fix it, all command line. Any help would be appreciated.

---

### Post by Kirk Schnable on 2013-09-27
Unfortunately, I don't think you've posted enough information for us to help you. We need to determine which sub-process is returning the error code.

Could you post the entire output of a sample apt command which generates the error?

---

### Post by seethru on 2013-09-27
```
sudo apt-get update
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise-backports Release.gpg
Hit http://us.archive.ubuntu.com precise Release
Get:2 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]
Hit http://us.archive.ubuntu.com precise-backports Release
Hit http://us.archive.ubuntu.com precise/main Sources
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main amd64 Packages
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:3 http://us.archive.ubuntu.com precise-updates/main Sources [419 kB]
Get:4 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]
Get:6 http://us.archive.ubuntu.com precise-updates/restricted Sources [7,006 B]
Get:7 http://us.archive.ubuntu.com precise-updates/universe Sources [96.2 kB]
Get:8 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,343 B]
Get:9 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [694 kB]
Hit http://nginx.org precise Release.gpg
Get:10 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [11.5 kB]
Hit http://nginx.org precise Release
Get:11 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [216 kB]
Get:12 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.9 kB]
Get:13 http://us.archive.ubuntu.com precise-updates/main i386 Packages [714 kB]
Hit http://nginx.org precise/nginx amd64 Packages
Get:14 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [11.4 kB]
Get:15 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [221 kB]
Get:16 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [14.0 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://nginx.org precise/nginx i386 Packages
Ign http://nginx.org precise/nginx TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Get:17 http://security.ubuntu.com precise-security/main Sources [88.5 kB]
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Get:18 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:19 http://security.ubuntu.com precise-security/universe Sources [28.1 kB]
Get:20 http://security.ubuntu.com precise-security/multiverse Sources [1,804 B]
Get:21 http://security.ubuntu.com precise-security/main amd64 Packages [322 kB]
Ign http://nginx.org precise/nginx Translation-en_US
Ign http://nginx.org precise/nginx Translation-en
Get:22 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:23 http://security.ubuntu.com precise-security/universe amd64 Packages [82.4 kB]
Get:24 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,449 B]
Get:25 http://security.ubuntu.com precise-security/main i386 Packages [342 kB]
Get:26 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:27 http://security.ubuntu.com precise-security/universe i386 Packages [86.0 kB]
Get:28 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,640 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 3,493 kB in 2s (1,329 kB/s)
E: Sub-process returned an error code
```

It's unfortunately very vague :/ It just spits that out after every apt-get command.

---

### Post by Bashing-om on 2013-09-28
seethru; Hi !

Here is a thought .. As the output halts after the "security repos run; recon that the "partner repositories" are not enabled in the "/etc/apt/sources.list" file while there are 3rd party PPAs enabled ?

check:
```

cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d

```

[INDENT][INDENT]good place to start
[/INDENT][/INDENT]

---

### Post by seethru on 2013-09-28
Return from those commands

```
cat -n /etc/apt/sources.list
     1  #
     2
     3  # deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/main/binary-i386/
     4  # deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/restricted/binary-i386/
     5  # deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ precise main restricted
     6
     7  #deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/main/binary-i386/
     8  #deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/restricted/binary-i386/
     9  #deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ precise main restricted
    10
    11  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    12  # newer versions of the distribution.
    13  deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    14  deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    15
    16  ## Major bug fix updates produced after the final release of the
    17  ## distribution.
    18  deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    19  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    20
    21  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    22  ## team. Also, please note that software in universe WILL NOT receive any
    23  ## review or updates from the Ubuntu security team.
    24  deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    25  deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    26  deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    27  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    28
    29  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    30  ## team, and may not be under a free licence. Please satisfy yourself as to
    31  ## your rights to use the software. Also, please note that software in
    32  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    33  ## security team.
    34  deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    35  deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    36  deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    37  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    38
    39  ## N.B. software from this repository may not have been tested as
    40  ## extensively as that contained in the main release, although it includes
    41  ## newer versions of some applications which may provide useful features.
    42  ## Also, please note that software in backports WILL NOT receive any review
    43  ## or updates from the Ubuntu security team.
    44  deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    45  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    46
    47  deb http://security.ubuntu.com/ubuntu precise-security main restricted
    48  deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    49  deb http://security.ubuntu.com/ubuntu precise-security universe
    50  deb-src http://security.ubuntu.com/ubuntu precise-security universe
    51  deb http://security.ubuntu.com/ubuntu precise-security multiverse
    52  deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    53
    54  ## Uncomment the following two lines to add software from Canonical's
    55  ## 'partner' repository.
    56  ## This software is not part of Ubuntu, but is offered by Canonical and the
    57  ## respective vendors as a service to Ubuntu users.
    58  # deb http://archive.canonical.com/ubuntu precise partner
    59  # deb-src http://archive.canonical.com/ubuntu precise partner
    60
    61  ## Uncomment the following two lines to add software from Ubuntu's
    62  ## 'extras' repository.
    63  ## This software is not part of Ubuntu, but is offered by third-party
    64  ## developers who want to ship their latest software.
    65  # deb http://extras.ubuntu.com/ubuntu precise main
    66  # deb-src http://extras.ubuntu.com/ubuntu precise main
    67
    68  deb http://nginx.org/packages/ubuntu/ precise nginx

ls -la /etc/apt/sources.list.d
total 8
drwxr-xr-x 2 root root 4096 Apr 20  2012 .
drwxr-xr-x 6 root root 4096 Sep 26 21:29 ..


```

---

### Post by Bashing-om on 2013-09-28
seethru; Maybe,

> 
  68  deb [http://nginx.org/packages/ubuntu/](http://nginx.org/packages/ubuntu/) precise nginx

is not a part of ubuntu's software repository and the 
> 
58  # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
59  # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

are not enabled and as well,
> 
61  ## Uncomment the following two lines to add software from Ubuntu's
    62  ## 'extras' repository.
    63  ## This software is not part of Ubuntu, but is offered by third-party
    64  ## developers who want to ship their latest software.
    65  # deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    66  # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
 are also not enabled.

enable these repositories and let's see what happens then.
To enable them just delete the "#" character at the start of the respective lines - with your favorite text editor.
Remember: always make a backup of any file prior to editing.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-bac

```

[INDENT][INDENT]looks plausible to me
[/INDENT][/INDENT]

---

### Post by sandyd on 2013-09-28
> **seethru said:**
> Getting this whenever I run an apt-get install or remove. It doesn't appear to affect anything, but it's very annoying.


```
E: Sub-process returned an error code
```

This started when I ran into a problem with python and pkg_configure. I've since fixed that but this issue remains. This is an ubuntu server so no GUI for me to use to fix it, all command line. Any help would be appreciated.

can you post the output of
```

cat /var/lib/dpkg/status
``` - thanks

---

### Post by seethru on 2013-09-28
This mysteriously fixed itself...

---

