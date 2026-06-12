---
title: "apt-get problems in edgy"
date: 2006-11-06
forum: General Help
---

### Post by Thought_Criminal on 2006-11-06
Hello, I just upgraded to Ubuntu 6.10 - Edgy and for some reason when I run apt-get update it has connection issues.  I will post a file with the output from running apt-get update.
> 
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy Release.gpg
  Could not connect to amaranth.selfip.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://ubuntu.compiz.net](http://ubuntu.compiz.net) edgy Release.gpg
  Could not connect to ubuntu.compiz.net:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://compiz-mirror.lupine.me.uk](http://compiz-mirror.lupine.me.uk) edgy Release.gpg
  Could not connect to compiz-mirror.lupine.me.uk:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US
  Could not connect to archive.canonical.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy/lrm Translation-en_US
  Could not connect to amaranth.selfip.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://ubuntu.compiz.net](http://ubuntu.compiz.net) edgy/main-edgy Translation-en_US
  Could not connect to ubuntu.compiz.net:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://compiz-mirror.lupine.me.uk](http://compiz-mirror.lupine.me.uk) edgy/main-edgy Translation-en_US
  Could not connect to compiz-mirror.lupine.me.uk:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)

But at first I had bad connection problems after the install, firefox was really weird and failed to go to most webistes but worked sometimes, for instance I could not get to [www.google.com](www.google.com) but could get to a few .org websites, so I came here and found a thread with a similar problem and blacklisted IPv6 and that fixed that problem.

Anyways is there some kind of firewall thing or something in edgy that makes these kinds of problems?

Oh yeah also when I try to use the Add/Remove program from the applications list is can get a list of apps so there is some communication but then it fails to download anything. I think that usually gives wget unable to connect error messages.

Anyways any help would be greatly appreciated.

---

### Post by taurus on 2006-11-06
What does your /etc/apt/sources.list look like?  Also, those servers that you are using could be down!

---

### Post by TheRingmaster on 2006-11-06
some of your sources are for dapper and some are for edgy!

---

### Post by Thought_Criminal on 2006-11-06
Here is my /etc/apt/sources.list file

> 
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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://beerorkid.com/compiz](http://beerorkid.com/compiz) edgy main-edgy
deb [http://media.bluntkind.org/xgl/](http://media.bluntkind.org/xgl/) edgy main-edgy
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy
deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy .

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy .
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy-dev .


The one dapper repo wasn't commented out in the original posting, I have since commented it out. Thanks for pointing that out **theringmaster**

I thought that some server may just be down or over their bandwidth limits or something but I have been having this problem for a few days now.

---

### Post by Joe_CoT on 2006-11-07
Could you try this?
```
ping archive.canonical.com
```

I don't think your dns is working correctly.

---

### Post by TheRingmaster on 2006-11-07
> **Thought_Criminal said:**
> Here is my /etc/apt/sources.list file



The one dapper repo wasn't commented out in the original posting, I have since commented it out. Thanks for pointing that out **theringmaster**

I thought that some server may just be down or over their bandwidth limits or something but I have been having this problem for a few days now.
can't you just change that to edgy too

---

### Post by Ramses de Norre on 2006-11-07
He uses 1.0.0.0 as IP for all servers, that's a little odd.. I think I've seen this before, a forum search may bring you to a solution.

---

### Post by Joe_CoT on 2006-11-07
> He uses 1.0.0.0 as IP for all servers, that's a little odd.. I think I've seen this before, a forum search may bring you to a solution.

correct ;) His dns isn't working. That's why I want him to try to ping the domain, because he'll see the IP is resolving to 1.0.0.0 and his dns is screwed up. Probably something added to the /etc/hosts file.

---

