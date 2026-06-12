---
title: "sudo apt get error"
date: 2020-04-26
forum: General Help
---

### Post by pegasusp on 2020-04-26
I am trying to solve errors to install MariaDB but i am getting new errors :/

```

Get:1 [http://mirror.mephi.ru/mariadb/repo/5.5/ubuntu](http://mirror.mephi.ru/mariadb/repo/5.5/ubuntu) trusty InRelease [3,234 B]
Ign:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise InRelease
Get:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise Release [8,180 B]
Ign:4 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise InRelease
Err:1 [http://mirror.mephi.ru/mariadb/repo/5.5/ubuntu](http://mirror.mephi.ru/mariadb/repo/5.5/ubuntu) trusty InRelease
  The following signatures were invalid: 199369E5404BD5FC7D2FE43BCBCB082A1BB943DB
Get:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise Release.gpg [181 B]
Get:6 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise Release [11.9 kB]
Get:7 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise Release.gpg [72 B]
Ign:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise Release.gpg
Ign:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign:7 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise Release.gpg
Ign:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security InRelease
Get:8 [http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu](http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu) precise InRelease [2,489 B]
Hit:11 [http://mariadb.mirror.liquidtelecom.com/repo/10.4/ubuntu](http://mariadb.mirror.liquidtelecom.com/repo/10.4/ubuntu) bionic InRelease
Err:8 [http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu](http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu) precise InRelease
  The following signatures were invalid: 199369E5404BD5FC7D2FE43BCBCB082A1BB943DB
Ign:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
Hit:13 [http://ftp.utexas.edu/mariadb/repo/10.3/ubuntu](http://ftp.utexas.edu/mariadb/repo/10.3/ubuntu) bionic InRelease
Ign:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease
Err:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release
  404  Not Found [IP: 91.189.91.38 80]
Err:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release
  404  Not Found [IP: 91.189.91.38 80]
Err:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release
  404  Not Found [IP: 91.189.91.38 80]
Err:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release
  404  Not Found [IP: 91.189.91.38 80]
Reading package lists... Done
W: GPG error: [http://mirror.mephi.ru/mariadb/repo/5.5/ubuntu](http://mirror.mephi.ru/mariadb/repo/5.5/ubuntu) trusty InRelease: The following signatures were invalid:                                                   199369E5404BD5FC7D2FE43BCBCB082A1BB943DB
E: The repository 'http://mirror.mephi.ru/mariadb/repo/5.5/ubuntu trusty InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
E: The repository 'http://archive.canonical.com/ubuntu precise Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
E: The repository 'http://extras.ubuntu.com/ubuntu precise Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu](http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu) precise InRelease: The following signatures were invalid: 199369E5404BD5FC7D2FE43BCBCB082A1BB943DB
E: The repository 'http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu precise InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com precise Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com precise-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com precise-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com precise-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by guiverc on 2020-04-26
Ubuntu 12.04 LTS reached EOL (*end-of-life*) years ago.

[https://fridge.ubuntu.com/2017/03/15/ubuntu-12-04-precise-pangolin-reaches-end-of-life-on-april-28-2017/](https://fridge.ubuntu.com/2017/03/15/ubuntu-12-04-precise-pangolin-reaches-end-of-life-on-april-28-2017/)

After a releases reaches EOL, country mirrors can drop it (thus errors are to be expected, the date on which those errors occur is any day after EOL), and main archive moves to old-releases.  For LTS releases that get extended support through ESM this is more complex (the drop & moves I mentioned just occur later, but still eventually occur).

I'll provide [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) and suggest you upgrade to a supported release of Ubuntu, or use your ESM support ([https://ubuntu.com/esm](https://ubuntu.com/esm))

---

### Post by pegasusp on 2020-04-26
I don't have any idea how to upgrade.
in [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) 
[B]
Update sources.list[/B]

do i need to put only that code there or just add it to end?
[B]
Dependencies[/B]

my ubuntu version probably don't have "*aptitude*"

---

### Post by wildmanne39 on 2020-04-26
Please see my post in your other thread located here:

[https://ubuntuforums.org/showthread.php?t=2441787](https://ubuntuforums.org/showthread.php?t=2441787)

You should do a fresh install from scratch, it will take a long time to upgrade using the method mentioned above if it is possible at all and you will most likely have issues that can not be solved or are very time consuming to do so, back up all important data first.

If you need help installing a new version of Ubuntu you can start a new thread for that topic as this thread is about a long dead OS, I am closing it and your other thread.

---

### Post by guiverc on 2020-04-26
Ubuntu 12.04 LTS is EOL as I said in prior reply.  It had two intended upgrade paths, one was to the next release (12.10 or *off* the LTS path), or to the next LTS release which was Ubuntu 14.04 LTS.

Given Ubuntu 14.04 LTS is now also EOL (it's in extended support only), whilst it maybe possible to `do-release-upgrade` to move to 14.04, given it's EOL or ESM status you should then restart the machine, and *release-upgrade* again to get to 16.04 LTS or the oldest currently supported release (it reaches EOL in 2021-April anyway so you'll need to move again rather soon).

For notes on upgrading, I'd always turn to the release notes for the release you're going to, ie. from 12.04 to 14.04 it'll be 14.04's release notes or [https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes) (in the *Upgrading from Ubuntu 12.04 LTS or Ubuntu 13.10* section)

A far easier option would be to backup, and clean install say Ubuntu 18.04 LTS (or 20.04 LTS though I'd likely test that first before I moved to it, given how new it is).

As for `aptitude`, I've been using it for years and can't imagine any not being available for any release (Aptitude is older than Ubuntu is)

---

