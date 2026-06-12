---
title: "Target package is configured multiple times"
date: 2019-03-22
forum: General Help
---

### Post by embcen on 2019-03-22
I installed Opera browser as suggested by [linuxconfig]("https://linuxconfig.org/how-to-install-opera-browser-on-ubuntu-18-04-bionic-beaver-linux").
Then I installed Atom editor, following instructions at [atom.io]("https://flight-manual.atom.io/getting-started/sections/installing-atom/#platform-linux"). During this latter operation, I ran sudo apt-get update and got the following output:

```
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11-icons-small (non-free/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target CNF (non-free/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target CNF (non-free/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11-icons-small (non-free/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target CNF (non-free/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
W: Target CNF (non-free/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/opera-stable.list:4
```

The output of the command cat /etc/apt/sources.list is:

```
# deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://it.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://it.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://it.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://it.archive.ubuntu.com/ubuntu/ bionic universe
deb http://it.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://it.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://it.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

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
deb [arch=amd64,i386] https://deb.opera.com/opera-stable/ stable non-free
# deb-src [arch=amd64,i386] https://deb.opera.com/opera-stable/ stable non-free
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
```

Line 51 is the commented line ```
# deb-src [arch=amd64,i386] [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free
```
The output of cat /etc/apt/sources.list.d/opera-stable.list is:

```
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/opera-stable.list (END)
```



However I do not see duplicates, so I do not understand the warnings.
Any help would be appreciated.

---

### Post by deadflowr on 2019-03-22
Yes you do.
Look at the line in sources.list above the deb-src line you commented out.
```
deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
**deb [arch=amd64,i386] https://deb.opera.com/opera-stable/ stable non-free**
# deb-src [arch=amd64,i386] https://deb.opera.com/opera-stable/ stable non-free
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
```
Just try commenting out that line.

Edit:
Somewhere it looks like it's not counting a line, which is why it's showing the deb line as line 51 instead of the deb-src line.
Odd.

---

### Post by embcen on 2019-03-22
@deadflowr you are right: line 51 is the line:[B] deb [arch=amd64,i386] [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free
[/B]My mistake.
I noticed that in /etc/apt/sources.list the lines come in couples, such is:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted

So why not accept the couple associated to Opera?

deb [arch=amd64,i386] [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free
# deb-src [arch=amd64,i386] [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free

In other words: where is the duplicate?
P.S. Can I run sudo apt-get update another time?

---

### Post by deadflowr on 2019-03-22
The duplicates are the line I bolded and the line in the opera-stable.list file.
The [Arch= line]  doesn't matter.
What matters i that both are trying to connect to the same archive.

---

### Post by embcen on 2019-03-22
It works, I commented out that line as you suggested and now apt-get update does not show any warnings.
Thanks!

---

### Post by Frogs Hair on 2019-03-22
Installing the applicable .deb from Opera's web site is all that is needed. The installer offers the option ad the software source during the installation.

---

