---
title: "Cant Install anything an Kubuntu Laptop"
date: 2008-01-03
forum: General Help
---

### Post by lexen on 2008-01-03
Hello, I installed kubuntu 7.10 on a 333Mhz laptop and I cant install anything using Add/Remove Programs, Adept or apt-get.  When I use Add/Remove Programs it will show programs that aren't install, but they are gray and I cannot install them.  When I use Adept it simply won't show anything to install, except a few programs.  When I use apt-get it won't install anything, I get an output like this:

sudo apt-get install firefox

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate

I am able to install .deb files, but I run into so many dependency problems I don't get very far.

When I try to update I get a lot of lines like this:

Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
  Could not resolve 'laneqwertyuiop'
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy ReleaseFailed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz)  Could not resolve 'laneqwertyuiop'

Any advice would be greatly appreciated.


Thanks,
Lexen

---

### Post by aysiu on 2008-01-03
Try [getting a fresh set of repositories](http://www.psychocats.net/ubuntu/sources#key) and then pasting these commands in ```
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by lexen on 2008-01-03
I already tried that, which is when I got those errors.  Is there anyway I don't have permission to install programs?  I can't figure out how to login as root, but I would love to try that.

I have an image in this post that should show you what I mean.

---

### Post by aysiu on 2008-01-03
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by lexen on 2008-01-03
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha i386 (20071221.1)]/ hardy main restricted



I put the last two lines on after the problem started, but it didn't help.

I tried a little experiment to see the nature of the problem.  I uninstalled two programs I didn't need to see if I could re-install them and I can.  I have attached a screenshot where you can see that some of the programs are gray, but two are not.  Why would it not be able to download new programs?  I also added an ubuntu CD, but that also didn't help.


Thanks,
Lexen

---

