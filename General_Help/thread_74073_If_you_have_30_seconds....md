---
title: "If you have 30 seconds..."
date: 2005-10-10
forum: General Help
---

### Post by nerdman on 2005-10-10
Open up synaptic and find the package **gaim-themes**.

if you can find it, post your sources.list file, please.

the smileys on GAIM are driving me insane x_x I just wanna swap 'em out and evidently this is the package I need.

thanks!

---

### Post by aysiu on 2005-10-10
I don't see it in [any of the Ubuntu repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gaim&searchon=names&subword=1&version=all&release=all)

---

### Post by macgyver2 on 2005-10-10
[QUOTE=aysiu]I don't see it in [any of the Ubuntu repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gaim&searchon=names&subword=1&version=all&release=all)[/QUOTE]
Bottom of the page.  It's in universe...but just in breezy.  I installed it to confirm, too.

---

### Post by nerdman on 2005-10-10
V.V Bummer. I'm really not in the mood to test unreleased software atm >.o

---

### Post by macgyver2 on 2005-10-10
[QUOTE=nerdman]V.V Bummer. I'm really not in the mood to test unreleased software atm >.o[/QUOTE]
The good news is you haven't much longer to wait for breezy to be final!

---

### Post by bored2k on 2005-10-10
```
aptraf@baka:~$ apt-cache search gaim themes **gaim-themes** - Smiley themes collection for gaim
``` ```
aptraf@baka:~$ cat /etc/apt/sources.list
```
 ```
#deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release Candidate i386 (20051006)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse



```

---

