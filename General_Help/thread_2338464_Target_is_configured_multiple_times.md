---
title: "Target is configured multiple times"
date: 2016-09-28
forum: General Help
---

### Post by GrouchyGaijin on 2016-09-28
Hi Guys,

This started last week.  I am not sure why, but now when I run ```
sudo apt update
``` I get the following waring.
Can I just safely delete the offending line (45, I believe) from etc/apt/sources.list?

```

W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4

```

---

### Post by ajgreeny on 2016-09-28
Let's have a look at the output of ```
cat /etc/apt/sources.list
``` and we may be able to give you a better idea of what to do.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by GrouchyGaijin on 2016-09-28
Here is the output:

```
 $ cat /etc/apt/sources.list# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu xenial main restricted
# deb-src http://se.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
# deb-src http://se.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu xenial universe
# deb-src http://se.archive.ubuntu.com/ubuntu/ xenial universe
deb http://archive.ubuntu.com/ubuntu xenial-updates universe
# deb-src http://se.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu xenial multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://archive.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://archive.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
deb http://apt.insynchq.com/ubuntu xenial non-free contrib



```

---

### Post by ajgreeny on 2016-09-28
Odd!

Line 45 is empty so far as I can see, so I am a bit lost about that, and there is nothing out of the ordinary as far as I can see in that file.

You do, however, have a file /etc/apt/sources.list.d/xenial-partner.list which is showing the  same as a line in your sources.list for some reason, though not line 45.

Let's see the output of ```
cat /etc/apt/sources.list.d/xenial-partner.list
``` and we may be able to see exactly what is the problem.
I suspect it will include the line ```
deb http://archive.canonical.com/ubuntu xenial partner
```which is already in your sources.list file.

---

### Post by CantankRus on 2016-09-29
I think line 45 is "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner".... line numbers out of sync because of the way it was pasted by GrouchyGaijin.

**/etc/apt/sources.list** looks fine with the partner repo in this file as normal.
Strange that you also have a "xenial-partner.list" file.
If you look in software sources you should see two occurrences of the partner repository enabled.
The default entry plus another custom entry.
```
software-properties-gtk --open-tab=1
```

As ajgreeny said, I would look at the contents of **/etc/apt/sources.list.d/xenial-partner.list** and possibly delete.

---

### Post by GrouchyGaijin on 2016-09-29
Thank you for the help guys.  I appreciate it.

```

cat /etc/apt/sources.list.d/xenial-partner.list
# channel for the xenial (16.04) partner channel
# 
#:description:This channel contains the partner software for xenial
deb http://archive.canonical.com/ubuntu xenial partner



```

---

### Post by CantankRus on 2016-09-29
Delete the file /etc/apt/sources.list.d/xenial-partner.list
or 
remove using GUI ....
```
software-properties-gtk --open-tab=1
```

Accomplishes the same thing.

Update sources...
```
sudo apt update
```

---

### Post by GrouchyGaijin on 2016-09-29
I misread your post.  Thank you that stopped the error.

---

### Post by CantankRus on 2016-09-29
**[COLOR="#FF0000"]Edit:[/COLOR]** Ok looks like you got it.

You have to highlight and remove the offending source entry.
[ATTACH=CONFIG]271413[/ATTACH]

or 
just remove via terminal...
```
sudo rm -i /etc/apt/sources.list.d/xenial-partner.list
```

---

