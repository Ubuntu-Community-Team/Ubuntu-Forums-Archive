---
title: "Is it Me or is it Apt?"
date: 2006-12-15
forum: General Help
---

### Post by BitTorrentBuddha on 2006-12-15
It seems as though no matter what I do, nor how many times I've installed Ubuntu on different computers, on each install apt never does apt-get update right. I have errors each time about not resolving the url. I would assume this is my fault usually, but it's never the same repositories that are unresolved, it's continuously different. Pinging the urls resolves them just fine. Do others have this problem? Is it my internet connection (wired, never seems to fail otherwise)? Is it the computers I've installed Ubuntu onto? Is it actually apt? I thank you for any help you provide, this proves a constant frustration for me in Ubuntu.

---

### Post by taurus on 2006-12-15
Why not post your /etc/apt/sources.list here and let's see what's wrong with it!

```
cat /etc/apt/sources.list
```

---

### Post by hikaricore on 2006-12-15
Alot of my sources do this from time to time, but I think it's just my ISP, an hour later or so they're all fine.

---

### Post by BitTorrentBuddha on 2006-12-15
Here's my sources.list, there are a lot of unofficial repos, but even the official ones sometimes fail to be resolved.```
$ cat /etc/apt/sources.list

## gpg --keyserver subkeys.pgp.net --recv KEY
## gpg --export --armor KEY | sudo apt-key add -

### Official Repositories ###
#############################

## Edgy Final Release Repository
deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

## Edgy Security Updates
deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## Edgy Bugfix Updates
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## Edgy Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## Ubuntu Commercial
# deb http://archive.canonical.com/ubuntu dapper-commercial main

#### Unofficial Repositories ####
##################################

## Automatix
deb http://www.getautomatix.com/apt edgy main

## NVIDIA Beta Drivers
deb http://SeerOfSouls.com/ edgy contrib
deb-src http://SeerOfSouls.com/ edgy contrib

## Listen
deb http://theli.free.fr/packages dapper listen listen-unstable
deb http://users.musicbrainz.org/~luks/ubuntu dapper main

## Beerorkid
# deb http://www.beerorkid.com/beryl edgy main-edgy
# deb-src http://www.beerorkid.com/beryl edgy main-edgy

## Treviño's Beryl-SVN Repo
# GPG key: 81836EBF
# deb http://3v1n0.tuxfamily.org dapper beryl-svn
# deb http://3v1n0.tuxfamily.org edgy beryl-svn

## Gaim beta stuff
deb http://www.elisanet.fi/mlind/ubuntu edgy main

## Deluge
deb http://espergreen.com/apt dapper main
```

EDIT: Wow, that looks really bad in non-monospaced font lol.

---

### Post by BitTorrentBuddha on 2007-02-22
This problem keeps coming up, is there any way to fix it? It is consistently a headache when I want to install something. I have a feeling it's my ISP, but I could definitely be wrong, I am, by no means, an apt guru.

---

