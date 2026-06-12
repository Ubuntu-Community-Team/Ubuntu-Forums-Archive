---
title: "How to revert spontaneously installed newer packages to stock version?"
date: 2016-09-22
forum: General Help
---

### Post by &amp;KyT$0P# on 2016-09-22
What is the best way to revert a "locally-installed" newer package to the repository version, when uninstalling the package would uninstall most of the system?


In auditing my package list on my 14.04 system, I discovered that all Python 2.7 related packages had been upgraded to a version 2.7.12.  These packages were not part of any repository or PPA - Synaptic listed them as "Installed (local or obsolete)" - and I didn't manually install them.
I do not know how this happened.

In order to revert to the stock Python 2.7 from Ubuntu repositories, I ended up doing this rather horrible hack -
```
sudo add-apt-repository ppa:fkrull/deadsnakes-python2.7
sudo apt-get update
sudo ppa-purge ppa:fkrull/deadsnakes-python2.7
```
and then deleted the deadsnakes-python2.7 from software sources settings.  Which seemed to work, and I hope was fine for this case, because I already trust fkrull in that I have various Python versions installed from his "deadsnakes" PPA.

But since I don't know how this conflict happened in the first place, I cannot rely on there being a PPA I can use to rescue the situation should it arise with some other package.

Any suggestions for a better method would be appreciated, because I would suspect this isn't the only affected machine I'll have to deal with.

---

### Post by mc4man on 2016-09-23
> In auditing my package list on my 14.04 system, I discovered that all Python 2.7 related packages had been upgraded to a version 2.7.12. These packages were not part of any repository or PPA - Synaptic listed them as "Installed (local or obsolete)" - and I didn't manually install them.
I do not know how this happened.
Well they didn't come out of thin air, had to have been from some repo or ppa. Ubuntu itself didn't get 2.7.12 until xenial-updates. If you could retrieve/remember a full package name then where they came from wouldn't be hard to discern.
So it's unlikely to occur again without some input from you (that you could reverse

If upgrades come from proposed (not the case here),  then probably a few methods to reverse, one shown here - 
[http://askubuntu.com/questions/768849/how-to-reverse-proposed-channel-package-upgrade](http://askubuntu.com/questions/768849/how-to-reverse-proposed-channel-package-upgrade)

---

### Post by &amp;KyT$0P# on 2016-09-23
Here's the history.log entry for the (successful) ppa-purge -
```
Commandline: apt-get install libpython2.7:amd64/trusty libpython2.7-dev:amd64/trusty libpython2.7-minimal:amd64/trusty libpython2.7-stdlib:amd64/trusty python2.7/trusty python2.7-dev/trusty python2.7-minimal/trusty
Downgrade: libpython2.7-stdlib:amd64 (2.7.12-1~trusty1, 2.7.6-8ubuntu0.2), python2.7:amd64 (2.7.12-1~trusty1, 2.7.6-8ubuntu0.2), libpython2.7-dev:amd64 (2.7.12-1~trusty1, 2.7.6-8ubuntu0.2), libpython2.7:amd64 (2.7.12-1~trusty1, 2.7.6-8ubuntu0.2), python2.7-dev:amd64 (2.7.12-1~trusty1, 2.7.6-8ubuntu0.2), python2.7-minimal:amd64 (2.7.12-1~trusty1, 2.7.6-8ubuntu0.2), libpython2.7-minimal:amd64 (2.7.12-1~trusty1, 2.7.6-8ubuntu0.2)

```

---

### Post by mc4man on 2016-09-23
python2.7:amd64 (2.7.12-1~trusty1) is a ppa package, quite likely from the aforementioned ppa  (or from a ppa that had copied those python packages..
If that was the package you had seen originally  then you must have used that ppa at some point

---

### Post by &amp;KyT$0P# on 2016-09-23
These are the only PPAs (and, for that matter, any other external sources).  No PPAs had ever been removed when I first noticed the issue.
If a PPA is the culprit it'd have to be one of these.
```
deb http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu trusty main
deb http://ppa.launchpad.net/git-core/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/git-core/ppa/ubuntu trusty main
deb http://ppa.launchpad.net/hda-me/qt5ct/ubuntu trusty main
# deb-src http://ppa.launchpad.net/hda-me/qt5ct/ubuntu trusty main
deb http://ppa.launchpad.net/marian.kadanka/vlc/ubuntu trusty main
# deb-src http://ppa.launchpad.net/marian.kadanka/vlc/ubuntu trusty main
deb http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu trusty main

```

sources.list
```
# deb cdrom:[Lubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main multiverse universe restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main multiverse universe restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse #Added by software-properties

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main multiverse universe restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

---

### Post by &amp;KyT$0P# on 2016-09-30
> **halogen2 said:**
> What is the best way to revert a "locally-installed" newer package to the repository version, when uninstalling the package would uninstall most of the system?
Looked through the [FONT=Courier New]ppa-purge[/FONT] script, and conclude that the "magic" we're interested in is all in the apt-get command shown in that history.log entry.  Looked through the man page of apt-get, eventually found this -
```

           A specific version of a package can be selected for installation by
           following the package name with an equals and the version of the
           package to select. This will cause that version to be located and
           selected for install. [COLOR="#FF0000"][B]Alternatively a specific distribution can be
           selected by following the package name with a slash and the version
           of the distribution or the Archive name (stable, testing,
           unstable).

           Both of the version selection mechanisms can downgrade packages and
           must be used with care.[/B][/COLOR]

           This is also the target to use if you want to upgrade one or more
           already-installed packages without upgrading every package you have
           on your system. Unlike the "upgrade" target, which installs the
           newest version of all currently installed packages, "install" will
           install the newest version of only the package(s) specified. Simply
           provide the name of the package(s) you wish to upgrade, and if a
           newer version is available, it (and its dependencies, as described
           above) will be downloaded and installed.

```

What is a "specific distribution" here?
How do we know that the "specific distribution" for the stock repositories is the Ubuntu release codename?

---

### Post by &amp;KyT$0P# on 2016-10-30
I finally had time to deliberately recreate the problem in a disposable VM that doesn't have [FONT=Courier New]ppa-purge[/FONT], and try to fix it.

> **halogen2 said:**
> What is a "specific distribution" here?
How do we know that the "specific distribution" for the stock repositories is the Ubuntu release codename?
Answering my own question... I think that comes from the sources.list line.

But there's another issue - finding a workable [FONT=Courier New]apt-get install[/FONT] command is tricky.  First tried with only python2.7/trusty, and apt-get wanted to uninstall everything KDE and Qt plus a few other tidbits.  Then threw in python2.7-dev/trusty, and apt-get said I had requested an impossible situation.  Anyway, in the end, the following command successfully restored stock Python -
```
$ sudo apt-get install python2.7/trusty python2.7-dev/trusty libpython2.7/trusty libpython2.7-dev/trusty
```

---

