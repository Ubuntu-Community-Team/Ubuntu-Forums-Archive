---
title: "apt-get timing out"
date: 2006-12-12
forum: General Help
---

### Post by phlite on 2006-12-12
Hi,

I'm trying to install xmms among other things.  I try:

sudo apt-get install xmms

I time out on all of the mirrors.  I do have a valid internet connection.  How can I choose different mirrors?  Or is there something else wrong?

also,

sudo apt-get update

fails on all mirrors..

I hope somone can help me, thanks.

---

### Post by Zelut on 2006-12-12
can you post the contents of your /etc/apt/sources.list file?  Also, do you say normal browsing works fine?  (that could rule out a DNS issue).

Thanks

---

### Post by neemz on 2006-12-12
By valid internet connection do you mean that there is no firewall installed that may be blocking apt?

Out of interest what happens if you type this command in the console?

ping security.ubuntu.com

---

### Post by phlite on 2006-12-12
kuyaedz:


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted univer
se multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted un
iverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


neemz:

ping works ... i do have a firewall, but i believe that apt-get works on port 80 eh? ... 80 not blocked, thx.

---

### Post by Zelut on 2006-12-12
well you could try the main server vs the us-based.  perhaps replace [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) with [http://archive.ubuntu.com](http://archive.ubuntu.com)..

also, I'm not sure if it matters but I do not have a trailing slash on any of my repositories, which it appears you do on many.

Also, did you notice your security, universe & multiverse repositories are not enabled?  Might want to uncomment those other lines :)

---

### Post by phlite on 2006-12-12
hmm, apt-get update worked this time, guess just server traffic, now i'm set with installing xmms, thx guys

---

