---
title: "Update Manager; Authentication error on libterm-readkey-perl"
date: 2013-06-02
forum: General Help
---

### Post by jsgarvin on 2013-06-02
I'm getting this error in Update Manager on libterm-readkey-perl.  Even when I unselect that package from the list of updates, it still gives the error.  Any ideas?

[IMG]http://s16.postimg.org/umjasnlit/Screenshot_from_2013_06_02_17_14_55.png[/IMG]

---

### Post by hansdown on 2013-06-02
Hi jsgarvin.
 
10.04 reached end of life may 9th.

Trying to update may have problems.

---

### Post by jsgarvin on 2013-06-02
> **hansdown said:**
> Hi jsgarvin.
 
10.04 reached end of life may 9th.

Trying to update may have problems.

Sorry.  Profile is out of date.   I'm on 12.04.  I guess that would be useful information to include.  Going to update my profile now.

---

### Post by hansdown on 2013-06-02
Haha!

That's cool.

I've been researching 

> libterm-readkey-perl

Some of the files are in german.

The maintainer is Joerg Jaspert.

This package covers 13 archetectures, and oodles of apps.

I would guess, that you have at least 6 or more apps, that depend on this.

I'll go out on a limb, and say it's a safe update

---

### Post by hansdown on 2013-06-02
Haha!

That's cool.

I've been researching 

> libterm-readkey-perl

Some of the files are in german.

The maintainer is Joerg Jaspert.

This package covers 13 archetectures, and oodles of apps.

I would guess, that you have at least 6 or more apps, that depend on this.

I'll go out on a limb, and say it's a safe update.

---

### Post by jsgarvin on 2013-06-03
> **hansdown said:**
> I'll go out on a limb, and say it's a safe update.

Except that it won't let me.  I get the error dialog I posted above, and when I close that it just goes back to update manager, without updating anything.  It's blocking me from updating other applications.  Like I said, even if I unselect libterm-readkey-perl from the update list, I get the same error and it refuses to update anything.

---

### Post by hansdown on 2013-06-03
My bad.

Open a terminal, and type

> sudo apt-get update -f

If that doesn't work, we'll need to look at your sources list.

>  sudo gedit /etc/apt/sources.list

---

### Post by jsgarvin on 2013-06-03
Thanks for the help...

sudo apt-get update -f ends with the following...

```
W: GPG error: http://us.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

/etc/apt/sources.list is...

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by hansdown on 2013-06-04
That GPG error has been around for a while.

The last number needs to go.

> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B

To rebuild your software cache,

> cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update

---

### Post by jsgarvin on 2013-06-06
Thanks. The first command gives another error.

```
gpg: "40976EAF437D05B" not a key ID: skipping
```

Update:  Did a little googling with the new info and found that the key needed an extra 5 on the end, so this...

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 
```

That, along with the other commands to rebuild the cache, and all seems good now.

Thanks a bunch, hansdown.

---

### Post by hansdown on 2013-06-06
Wow, good job,jsgarvin!

Sorry for the mixup.

---

