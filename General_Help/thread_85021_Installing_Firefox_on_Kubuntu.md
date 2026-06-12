---
title: "Installing Firefox on Kubuntu"
date: 2005-11-01
forum: General Help
---

### Post by duffmckagan on 2005-11-01
I have upgraded from Hoary to Breezy.

What sources do I need to add to /etc/apt/sources.list file to install firefox?

Here is my current sources.list

```

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://in.archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://in.archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://in.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://in.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe


```

---

### Post by lorenco on 2005-11-01
I would just add: 

# deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy main restricted
# deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary universe
Be carefull here it still reads hoary ?? should be breezy...

Obviously (or not) remove the # ;-)

---

### Post by duffmckagan on 2005-11-01
[quote=lorenco]I would just add: 

# deb [http://in.archive.ubuntu.com/ubuntu]("http://in.archive.ubuntu.com/ubuntu") breezy main restricted
# deb [http://in.archive.ubuntu.com/ubuntu]("http://in.archive.ubuntu.com/ubuntu") breezy-updates main restricted
# deb [http://in.archive.ubuntu.com/ubuntu]("http://in.archive.ubuntu.com/ubuntu") hoary universe
Be carefull here it still reads hoary ?? should be breezy...

Obviously (or not) remove the # ;-)[/quote]


Oh yeah! 
I will try that. But doesn't actually matter cuz that was commented out.  :)
I will change it.

---

