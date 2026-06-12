---
title: "Dapper repos down?"
date: 2007-03-08
forum: General Help
---

### Post by ankursethi on 2007-03-08
I've just done a fresh re-install of Dapper after struggling with OpenSuSe for a month. I tried to enable all the extra repos but it seems that no repos other than the default ones are working. Does anybody else have the same problem?

---

### Post by ankursethi on 2007-03-08
Okay, these seem to be the keys which are not downloading -> 
[http://in.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)
[http://in.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)
[http://in.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)

What now? I have absolutely no idea what to do, and I can't install build-essential, rar and other important stuff. HELP!

---

### Post by ankursethi on 2007-03-08
Here's my sources.list if you want. I'm getting the same errors for Edgy as well : 

> 
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


---

### Post by ankursethi on 2007-03-09
Bump.

For Christ's sake, at least point me to some mirrors...:(

---

### Post by Ramses de Norre on 2007-03-09
Try removing the "in." from the url's.

---

### Post by ankursethi on 2007-03-09
No help there. Tried accessing archive.ubuntu.com in Windows as well. It doesn't work.

---

