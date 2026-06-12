---
title: "Can not add Community maintained (Universe) channel in software preferences"
date: 2006-12-10
forum: General Help
---

### Post by zmr on 2006-12-10
I am trying to add the the "Community Maintained (Universe)" channel in the Software Preferences window in Dapper. After checking the option to add the Universe channel and clicking "close" in the Software Preferences window, I receive a prompt to reload the channels. After clicking the reload button and downloading the new up-to-date package information, I get the following error:

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

As a result, the Universe channel is not added. Any idea of what the problem could be?

---

### Post by aysiu on 2006-12-10
FreeContrib has nothing to do with Universe.

Can you post the output of this terminal command? ```
cat /etc/apt/sources.list
```

---

### Post by zmr on 2006-12-11
Hello Aysiu, 

Here's the output of the command cat /etc/apt/sources.list. 

```
## Uncomment the following two lines to fetch updated software from the network
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper mai n restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe m ultiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free

```

---

### Post by aysiu on 2006-12-11
Looks to me as if universe is in there.

If you want, you can comment out or delete the freecontrib lines--those have nothing to do with the universe repositories.

```
sudo nano -B /etc/apt/sources.list
``` Delete the last two lines, save (Control-X, Y, Enter), and update: ```
sudo aptitude update
```

---

