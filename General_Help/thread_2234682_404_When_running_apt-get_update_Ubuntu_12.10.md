---
title: "404 When running apt-get update Ubuntu 12.10"
date: 2014-07-16
forum: General Help
---

### Post by damnedkrt on 2014-07-16
Hi!

I seem to get, correct, 404 error when I try to run apt-get update. 

I get multiple rows similiar to:

```

W: Failed to fetch http://se.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages  404  Not Found [IP: 130.239.18.163 80]

```

Visiting that page in my browser clearly tells me that [http://se.archive.ubuntu.com/ubuntu/dists/](http://se.archive.ubuntu.com/ubuntu/dists/)**quantal-updates/** does not exist!

Can you please tell me why I cannot do an update, and how I make sure I can?

My sources.list

```

#


# deb cdrom:[Ubuntu-Server 12.10 _Quantal Quetzal_ - Release amd64 (20121017.2)]/ quantal main restricted


# deb cdrom:[Ubuntu-Server 12.10 _Quantal Quetzal_ - Release amd64 (20121017.2)]/ quantal main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://se.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ quantal main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ quantal-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://se.archive.ubuntu.com/ubuntu/ quantal universe
deb http://se.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://se.archive.ubuntu.com/ubuntu/ quantal-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://se.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://se.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ quantal-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu quantal main
# deb-src http://extras.ubuntu.com/ubuntu quantal main


## Webmin debs
deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib
deb http://download.webmin.com/download/repository sarge contrib


## PLEX MEDIA
deb http://www.plexapp.com/repo lucid main

```

EDIT:

I also get error for apt-get install firefox (for example)

```
 WARNING: The following packages cannot be authenticated! 
Install these packages without verification [y/N]?

```
And then I get more 404-messages

---

### Post by Impavidus on 2014-07-16
Ubuntu 12.10 is end-of-live and has been so since last April. Maybe they left the packages on the server for a while, but they are gone now. The best thing to do is installing a supported release of Ubuntu, which means 14.04. It will be supported until April 2019.

---

### Post by damnedkrt on 2014-07-16
> **Impavidus said:**
> Ubuntu 12.10 is end-of-live and has been so since last April. Maybe they left the packages on the server for a while, but they are gone now. The best thing to do is installing a supported release of Ubuntu, which means 14.04. It will be supported until April 2019.

I see, I was suspecting something like this. 

Is there a way for me to upgrade anyway, rather than doing a clean install and manually restore from backup? I can't seem to find a guide to help me with this, those that look promising, requires my apt-get to work.

I have so much set up on this box, and it would probably take me weeks (I'm not really that familiar with Linux) to get it all up and running again. I don't have any files I care particularly much about. Only services, such as samba, deluge, plex, phpvirtualbox, apache, teamspeak, CS-server.

---

### Post by slickymaster on 2014-07-16
Ubuntu only supports upgrading from one version to the next version, or from one LTS version to the next LTS version.

Because 12.10 isn't an LTS (long term supported) version, the only way you can upgrade is 12.10 -> 13.04 -> 13.10 -> 14.04.

---

### Post by hamishmb on 2014-07-16
Okay, you change all instances of 'quantal' to 'trusty', in your /etc/apt/sources.list, and then do:

sudo apt-get update && sudo apt-get dist-upgrade

However, that's not a supported upgrade path, and it may not work at all, so you should backup your files and expect to wait for several hours to complete the upgrade depending on the speed of your system.
In all honesty, it's probably easier to do a clean install.

Hamish

---

### Post by damnedkrt on 2014-07-16
> **slickymaster said:**
> Ubuntu only supports upgrading from one version to the next version, or from one LTS version to the next LTS version.

Because 12.10 isn't an LTS (long term supported) version, the only way you can upgrade is 12.10 -> 13.04 -> 13.10 -> 14.04.

Yeah I tried that

```

johan@esset:~$ sudo do-release-upgrade
[sudo] password for johan:
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife


Err Upgrade tool signature
  404  Not Found [IP: 91.189.91.13 80]
Err Upgrade tool
  404  Not Found [IP: 91.189.91.13 80]
Fetched 0 B in 0s (0 B/s)
WARNING:root:file 'raring.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem.

```

> **hamishmb said:**
> Okay, you change all instances of 'quantal' to 'trusty', in your /etc/apt/sources.list, and then do:

sudo apt-get update && sudo apt-get dist-upgrade

However, that's not a supported upgrade path, and it may not work at all, so you should backup your files and expect to wait for several hours to complete the upgrade depending on the speed of your system.
In all honesty, it's probably easier to do a clean install.

Hamish

I think I will give this a shot anyway, thanks for the tip. Otherwise I'll just make a clean install, and make sure to use the LTS-versions and keep them updated. 

Anyway. Thank you for your replies. I have an explanation to my problem and will set the post to SOLVED.

---

### Post by Impavidus on 2014-07-16
> **damnedkrt said:**
> Yeah I tried that

```

johan@esset:~$ sudo do-release-upgrade
[sudo] password for johan:
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife


Err Upgrade tool signature
  404  Not Found [IP: 91.189.91.13 80]
Err Upgrade tool
  404  Not Found [IP: 91.189.91.13 80]
Fetched 0 B in 0s (0 B/s)
WARNING:root:file 'raring.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem.

```
That is because 13.04 is end-of-live too.

---

### Post by LastDino on 2014-07-16
If you took a look at certain threads in ''upgrade and installation'' section you will know that even though upgrade is officially viable option, it can be full of headache. And on top of that you're planning to do that at least 4 (?) times. Even for a moment you did consider it a likely success, it will take you almost whole day.

Compare that to clean install.
Taking backup: 15 Min max
Installation: 20-30 Min
Getting all your preferred stuff/software back on running: Another 40 to 60 Min. Depending on your net connection.

You will be good for next 5 years if you install 14.04 LTS.

---

### Post by damnedkrt on 2014-07-17
> **LastDino said:**
> If you took a look at certain threads in ''upgrade and installation'' section you will know that even though upgrade is officially viable option, it can be full of headache. And on top of that you're planning to do that at least 4 (?) times. Even for a moment you did consider it a likely success, it will take you almost whole day.

Compare that to clean install.
Taking backup: 15 Min max
Installation: 20-30 Min
Getting all your preferred stuff/software back on running: Another 40 to 60 Min. Depending on your net connection.

You will be good for next 5 years if you install 14.04 LTS.

Yeah, upgrade did fail. Or well, seems to be inconclusive.

I doubt configuring will take me 40/60min. It's atleast a weekend job for me :D. But yeah, I think I will do a clean install instead and be set for the next 5 years.
Thanks!

---

### Post by josem2 on 2014-12-23
Add these lines in "sources.list" worked for me and now I'm upgrading to 13.04 using the update manager

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) quantal main
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) quantal main


J

---

### Post by Elfy on 2014-12-23
and then you'll need to upgrade to yet another EOL release and THEN upgrade to one that's supported.

Closed

---

