---
title: "Help with apt-get install in Amazon EC2"
date: 2013-03-12
forum: General Help
---

### Post by guilhermeveras on 2013-03-12
Hello,

I am with the following problem:
[COLOR=#b22222]
[/COLOR][COLOR=#b22222]
apt-get install gitolite
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  git-daemon-run gitweb
The following NEW packages will be installed:
  gitolite
0 upgraded, 1 newly installed, 0 to remove and 42 not upgraded.
Need to get 242 kB of archives.
After this operation, 541 kB of additional disk space will be used.
Err [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise/universe gitolite all 2.2-1
  Could not resolve 'sa-east-1b.clouds.archive.ubuntu.com'
Failed to fetch [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/pool/universe/g/gitolite/gitolite_2.2-1_all.deb](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/pool/universe/g/gitolite/gitolite_2.2-1_all.deb)  Could not resolve 'sa-east-1b.clouds.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

[/COLOR]
I tried using the update command and also searched on google.
But found nothing.
It seems to me that the repository is out of air.
Could someone help me.
thank you

---

### Post by cortman on 2013-03-12
Did you add that repository yourself? I'm not very familiar with Ubuntu Cloud, but it doesn't seem like you need a repository for it.
Please post the output of

```
cat /etc/apt/sources.list
```

---

### Post by guilhermeveras on 2013-03-12
Hello,

Thanks for your quick reply.
See the file:

## Note, this file is written by cloud-init on first boot of an instance
## modifications made here will not survive a re-bundle.
## if you wish to make changes you can:
## a.) add 'apt_preserve_sources_list: true' to /etc/cloud/cloud.cfg
##     or do the same in user-data
## b.) add sources in /etc/apt/sources.list.d
## c.) make changes to template file /etc/cloud/templates/sources.list.tmpl
#

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise main
deb-src [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise main

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise-updates main
deb-src [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

deb [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise universe
deb [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise multiverse
# deb-src [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise multiverse
# deb [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise-updates multiverse
# deb-src [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
# deb-src [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

---

### Post by Habitual on 2013-03-13
[COLOR=#b22222]Could not resolve 'sa-east-1b.clouds.archive.ubuntu.com' should be temporary.

from us-west-1 it resolves.
What zone are you "in"?[/COLOR][COLOR=#b22222]
[/COLOR]

---

### Post by cortman on 2013-03-13
I guess I'm in over my head here, because it seems hard to find much info about Ubuntu cloud or troubleshooting it.
I was able to resolve "http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/" here without any problem.
Perhaps as Habitual implied you need to change mirrors?

---

### Post by Habitual on 2013-03-13
I wouldn't change mirrors.

from the sources, you appear to in the east zone.
I have several servers at AWS in the east zone of the US, but I don't see those entries anywhere in cat /etc/apt/sources.list on those hosts.

Ping works. :)
ping -c 2 sa-east-1b.clouds.archive.ubuntu.com
PING sa-east-1b.archive.ubuntu.com (91.189.92.202) 56(84) bytes of data.
64 bytes from sudice.canonical.com (91.189.92.202): icmp_req=1 ttl=48 time=159 ms
64 bytes from sudice.canonical.com (91.189.92.202): icmp_req=2 ttl=48 time=159 ms

apt-cache search gitolite
**gitolite - SSH-based gatekeeper for git repositories**
so, why you feel the need to add a repo for  [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) is curious when apt  shows it as available?
```
apt-cache show  gitolite

Package: gitolite
Priority: optional
Section: universe/vcs
Installed-Size: 528
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Gerfried Fuchs <rhonda@debian.org>
Architecture: all
Version: 2.2-1
Depends: git (>= 1:1.7.0.4) | git-core (>= 1:1.6.2), perl (>= 5.6.0-16), openssh-server, debconf (>= 0.5) | debconf-2.0, adduser
Suggests: git-daemon-run, gitweb
Filename: pool/universe/g/gitolite/gitolite_2.2-1_all.deb
Size: 242400
MD5sum: 234a4e8160ca9fe76cbe878e3684a9db
SHA1: 4695036d5b0ae49555bbff5438d4108a08dd5620
SHA256: 404a9c60a29b908f7354be7581933f69c7e87cd16e6927a8d8557f8a172aca1f
Description-en: SSH-based gatekeeper for git repositories
 Gitolite is an SSH-based gatekeeper providing access control for a server that
 hosts many git repositories. Without gitolite,
 each developer needing to push to one of the repositories hosted would need a
 user account on that server; gitolite lets you do that just using
 SSH public keys tied to a single, common, user that hosts all the
 repositories.
 .
 Gitolite can restrict who can read (clone/fetch) from or write
 (push) to a repository, and who can push to what branch or tag - an
 important issue in corporate environments. Other features include:
   * access control by branch-name or by modified file/directory;
   * per-developer "personal namespace" prefixes;
   * simple but powerful configuration file syntax (with validation);
   * config files (and authority for maintaining them) can be split;
   * easy integration with gitweb;
   * comprehensive logging;
   * easy migration from gitosis.
Homepage: http://github.com/sitaramc/gitolite
Description-md5: a2c2eed3b30135c8676c4f96d91073b5
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

What version of Ubuntu is this?

I'd make a backup of cat /etc/apt/sources.list and then comment out the [http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/](http://sa-east-1b.clouds.archive.ubuntu.com/ubuntu/) stuff and try a plain-jane vanilla install from what Ubuntu has cached already using
```
apt-get install gitolite
```

---

