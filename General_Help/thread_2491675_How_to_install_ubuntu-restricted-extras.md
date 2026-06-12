---
title: "How to install ubuntu-restricted-extras"
date: 2023-10-17
forum: General Help
---

### Post by satimis on 2023-10-17
Hi all,

**[COLOR="#FF0000"]Ubuntu 22.04 desktop[/COLOR]**

Performed following steps on Terminal;

$ sudo add-apt-repository multiverse

$ sudo update

$ sudo apt info ubuntu-restricted-extras```

N: Unable to locate package ubuntu-restricted-extras
N: Unable to locate package ubuntu-restricted-extras
E: No packages found

```

The package is not found.  How to fix it?

Thanks

Regards

---

### Post by ActionParsnip on 2023-10-17
What is the output of:
```

sudo lsb_release -a; uname -a; sudo apt update

```

---

### Post by satimis on 2023-10-17
The output is ubuntu-restricted-extras not found

---

### Post by Impavidus on 2023-10-17
It's supposed to be there, on every supported release of Ubuntu, every architecture. On 22.04:```
$ apt info ubuntu-restricted-extras
Package: ubuntu-restricted-extras
Version: 67
Priority: optional
Section: multiverse/metapackages
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 14,3 kB
Depends: ubuntu-restricted-addons
Recommends: libavcodec-extra, ttf-mscorefonts-installer, unrar
Download-Size: 3.200 B
APT-Sources: http://nl.archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages
Description: Commonly used media codecs and fonts for Ubuntu
 This collection of packages includes:
  - MP3 and other audio codec software to play various audio formats
    (GStreamer plugins)
  - software to install the Microsoft Web fonts
  - the Adobe Flash plugin
  - LAME, software to create compressed audio files.
 .
 This software does not include libdvdcss2, and will not let you play
 encrypted DVDs. For more information, see
 https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs
 .
 These software packages are from the Multiverse channel, restricted by
 copyright or legal issues in some countries. For more information, see
 http://www.ubuntu.com/ubuntu/licensing


```BTW, that description is outdated. There's no Adobe Flash plugin anymore.

What's in your software sources?```
cat /etc/apt/sources.list
```

Note that this is a meta-package. It's only there for convenience, to install a bunch of popular restricted software. You can install its dependencies separately, giving you less bloat if you don't need all of it.

---

### Post by MAFoElffen on 2023-10-17
@satimis -- 

Reread Post #2. Your response in Post #3 does not match what was asked, nor have you answered that. You were asked something specific to get information he needed to go on with supporting you. I remember you. I remember what you have... You have your way that you usually do things. You do have multiple installs of things that do the same things, but differently. 

To keep this short and focused in the right direction, let me ask you in a different way... If you do not follow directions, and respond accordingly, you will not get a response back from me. Understood?

Please post the output of these within CODE Tags:
```

apt-cache show ubuntu-restricted-extras | grep -E 'Package|Arch|Section'
apt list ubuntu-restricted-extras
grep 'multiverse' /etc/apt/sources.list

```
Patiently waiting your answer.

Also "mentioned" in Impavidus'es last post, is that this package used have a use, which is not the case any more. People do not currently install this package these days. So what he said about that package, the what and why this package is used for, implies that you have something in mind, in why you think you need to install this package for... He didn't ask you directly, but I will:
--> Why do you think you need to install this package? (What is your current plan?)

---

### Post by satimis on 2023-10-17
> **ActionParsnip said:**
> What is the output of:
```

sudo lsb_release -a; uname -a; sudo apt update

```
$ sudo lsb_release -a; uname -a; sudo apt update > lsb_release.txt```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:        22.04
Codename:       jammy
Linux 2TBPCIeSSD 6.2.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Jul 13 16:27:29 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

E: The repository 'https://ppa.launchpadcontent.net/videolan/stable-daily/ubuntu jammy Release' does not have a Release file.

```

 lsb_release.txt is attached here

Regards

---

### Post by satimis on 2023-10-17
> **Impavidus said:**
> It's supposed to be there, on every supported release of Ubuntu, every architecture. On 22.04:```
$ apt info ubuntu-restricted-extras
Package: ubuntu-restricted-extras
Version: 67
Priority: optional
Section: multiverse/metapackages
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 14,3 kB
Depends: ubuntu-restricted-addons
Recommends: libavcodec-extra, ttf-mscorefonts-installer, unrar
Download-Size: 3.200 B
APT-Sources: http://nl.archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages
Description: Commonly used media codecs and fonts for Ubuntu
 This collection of packages includes:
  - MP3 and other audio codec software to play various audio formats
    (GStreamer plugins)
  - software to install the Microsoft Web fonts
  - the Adobe Flash plugin
  - LAME, software to create compressed audio files.
 .
 This software does not include libdvdcss2, and will not let you play
 encrypted DVDs. For more information, see
 https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs
 .
 These software packages are from the Multiverse channel, restricted by
 copyright or legal issues in some countries. For more information, see
 http://www.ubuntu.com/ubuntu/licensing


```BTW, that description is outdated. There's no Adobe Flash plugin anymore.
$ apt info ubuntu-restricted-extras```

N: Unable to locate package ubuntu-restricted-extras
N: Unable to locate package ubuntu-restricted-extras
E: No packages found

```

> 
What's in your software sources?```
cat /etc/apt/sources.list
```

cat /etc/apt/sources.list > sources_list.txt

sources_list.txt is attached here

Regards

---

### Post by MAFoElffen on 2023-10-17
Thank you for answering the others. I see you are catching up, and you have remembered how to use CODE Tags...

The last question I asked in my last post seems to point to your error:
> **satimis said:**
> 
E: The repository 'https://ppa.launchpadcontent.net/videolan/stable-daily/ubuntu jammy Release' does not have a Release file.
[/code]

That is an outdated PPA for VLC, which does not have a build since 20.04... Please remove that PPA from your sources.list. It is not going to help you, in whatever your plans are. You seem to be repeating history, and reading old outdated instructions to do something, which no longer works for 22.04...

So that begs answers to what you are trying to do... Please answer the questions from my last post. Installing "this package" noted in this thread title, may not be what you really need to do.

---

### Post by satimis on 2023-10-17
> **MAFoElffen said:**
> @satimis -- 

Reread Post #2. Your response in Post #3 does not match what was asked, nor have you answered that. You were asked something specific to get information he needed to go on with supporting you. I remember you. I remember what you have... You have your way that you usually do things. You do have multiple installs of things that do the same things, but differently. 

Already done as advised

> 
Please post the output of these within CODE Tags:
```

apt-cache show ubuntu-restricted-extras | grep -E 'Package|Arch|Section'
apt list ubuntu-restricted-extras
grep 'multiverse' /etc/apt/sources.list

```
Patiently waiting your answer.

```

: No packages found
Listing... Done
## multiverse WILL NOT receive any review or updates from the Ubuntu
###deb http://hk.mirrors.thegigabit.com/ubuntu/ jammy multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy multiverse
###deb http://hk.mirrors.thegigabit.com/ubuntu/ jammy-updates multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
###deb http://hk.mirrors.thegigabit.com/ubuntu/ jammy-backports main restricted universe multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
deb http://hk.mirrors.thegigabit.com/ubuntu/ jammy-security multiverse main restricted
###deb http://hk.mirrors.thegigabit.com/ubuntu/ jammy-security multiverse
deb-src http://security.ubuntu.com/ubuntu jammy-security multiverse

```

> 
Also "mentioned" in Impavidus'es last post, is that this package used have a use, which is not the case any more. People do not currently install this package these days. So what he said about that package, the what and why this package is used for, implies that you have something in mind, in why you think you need to install this package for... He didn't ask you directly, but I will:
--> Why do you think you need to install this package? (What is your current plan?)
I tried to view .mov file running "Videos".  It popup following warning (pls see attahced file)

Regards

---

### Post by MAFoElffen on 2023-10-17
You broke your main default sources.list:
```

deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy-updates main restricted


deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy-updates universe

deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy-updates multiverse

deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse

deb http://hk.mirrors.thegigabit.com/ubuntu/ jammy-security multiverse main restricted
deb-src http://security.ubuntu.com/ubuntu jammy-security universe
deb-src http://security.ubuntu.com/ubuntu jammy-security multiverse

```
Those are 'all' source code repositiories with no debian package repo's. That is why your machine does not see any debian packages.

You cannot even do any normal updates with that list.

Go back to Software & Updates > Ubuntu Software tab > and check the first 4 checkboxes... Uncheck the fifth, which is the source code checkbox...

EDIT: While there, after that > select the Other Software tab, and uncheck that PPA: videolan

Then read this: [https://hackernoon.com/how-to-fix-vlc-media-player-not-playing-mp4-videos](https://hackernoon.com/how-to-fix-vlc-media-player-not-playing-mp4-videos)
These are instructions from 2023 to fix that problem...

I don't know how long the problem with your sources.list has existed, so you may want to refresh your APT cache after that, and apply updates.

---

### Post by satimis on 2023-10-18
> **MAFoElffen said:**
> You broke your main default sources.list:
```

deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy-updates main restricted


deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy-updates universe

deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy-updates multiverse

deb-src http://hk.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse

deb http://hk.mirrors.thegigabit.com/ubuntu/ jammy-security multiverse main restricted
deb-src http://security.ubuntu.com/ubuntu jammy-security universe
deb-src http://security.ubuntu.com/ubuntu jammy-security multiverse

```
Those are 'all' source code repositiories with no debian package repo's. That is why your machine does not see any debian packages.

You cannot even do any normal updates with that list.

Go back to Software & Updates > Ubuntu Software tab > and check the first 4 checkboxes... Uncheck the fifth, which is the source code checkbox...

EDIT: While there, after that > select the Other Software tab, and uncheck that PPA: videolan

Thanks for your advice.

Performed steps according to your advice and rebooted PC.  Please see screenshots attached

> 
Then read this: [https://hackernoon.com/how-to-fix-vlc-media-player-not-playing-mp4-videos](https://hackernoon.com/how-to-fix-vlc-media-player-not-playing-mp4-videos)
These are instructions from 2023 to fix that problem...

I don't know how long the problem with your sources.list has existed, so you may want to refresh your APT cache after that, and apply updates.
VLC is/was working without problem right from the beginning.  Only -> "Open with Videos" has problem.  I'm trying to fix it.

Regards

---

