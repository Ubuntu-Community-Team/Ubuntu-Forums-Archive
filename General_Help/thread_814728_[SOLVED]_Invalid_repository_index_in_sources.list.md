---
title: "[SOLVED] Invalid repository index in sources.list"
date: 2008-06-01
forum: General Help
---

### Post by cnolanAU on 2008-06-01
Just a note here, I've had a problem with my software (apt) sources for about the last week.  When attempting to update, I was receiving the error:

Could not download all repository indexes
Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/hardy/Release](http://ftp.iinet.net.au/pub/ubuntu/dists/hardy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/hardy-updates/Release](http://ftp.iinet.net.au/pub/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Looking at the my sources.list (/etc/apt/sources.list) I found the repository sources:

[FONT="Courier New"]deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) hardy main universe restricted multiverse web
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted web
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) hardy-updates universe main multiverse restricted web[/FONT]

I'm not entirely sure if the word "web" was added and this created the problem, or if "web" has in fact been in my sources.list since I upgraded to Hardy and some repository configuration has changed, but removing the web on all these lines did fix the issue.

Does anyone know what "web" is, if anything?

---

### Post by tamoneya on 2008-06-01
just change your mirror.  Go into synaptic and select the preferences menu and then repositories.  There is a drop down menu to select different mirrors.

---

### Post by cnolanAU on 2008-06-01
I've tried a couple of different mirrors with the same result.  Removing "web" did get rid of the error, I was just wondering what software I'm losing as a result of not having it there.

---

### Post by tamoneya on 2008-06-01
those are pretty important updates.  Especially hardy-security. I have attached my sources.list for reference.  Mine seem to work fine.```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta amd64 (20080319)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.media.mit.edu/ubuntu/ hardy main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.media.mit.edu/ubuntu/ hardy-updates main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ubuntu.media.mit.edu/ubuntu/ hardy universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ hardy universe
deb http://ubuntu.media.mit.edu/ubuntu/ hardy-updates universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.media.mit.edu/ubuntu/ hardy multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ hardy multiverse
deb http://ubuntu.media.mit.edu/ubuntu/ hardy-updates multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://ubuntu.media.mit.edu/ubuntu/ hardy-security main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ hardy-security main restricted
deb http://ubuntu.media.mit.edu/ubuntu/ hardy-security universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ hardy-security universe
deb http://ubuntu.media.mit.edu/ubuntu/ hardy-security multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ hardy-security multiverse
```

---

### Post by quelx on 2008-06-01
> **cnolanAU said:**
> I've tried a couple of different mirrors with the same result.  Removing "web" did get rid of the error, I was just wondering what software I'm losing as a result of not having it there.

Did you install any packages through FireFox?

[https://answers.launchpad.net/ubuntu/+question/22021](https://answers.launchpad.net/ubuntu/+question/22021)

---

### Post by drs305 on 2008-06-01
> **cnolanAU said:**
> 
Does anyone know what "web" is, if anything?

A mistake? :lol:

As far as I know the repositories have never ended with 'web' but the error has been around for several versions of ubuntu. It shouldn't be on there and that's why it says the repository list is malformed.

---

### Post by cnolanAU on 2008-06-01
Ahh, thanks for that link, it and the linked [bug #202170]("https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/202170") did suggest firefox and totem-mozilla were the culprits.

---

