---
title: "problems with dependencies"
date: 2007-01-22
forum: General Help
---

### Post by Isoss on 2007-01-22
Hello community

I am having a problem with synaptic, which is basically an apt-get problem with the dependencies thing ... this happened many times with many different applications. I would be trying to install something and because of a dependency problem my installation fails! 

for example, I am trying to install postfix-mysql and I have postfix already installed and it gives this when I check the candidate in synaptic :
postfix-mysql:
  Depends: postfix (=2.3.3-1) but 1:2.1.5-1warp.es is to be installed

This happenes a lot!!! and it really bugs me for two reasons!
1. I don't know what's wrong!
2. I am not able to install many apps because of that!

I'd like to know what's going on and how to fix that!

Thanks

---

### Post by Nik_Doof on 2007-01-22
Sounds like the dependancies for the postfix-mysql package are refering to a different version than whats available in the repository. 

Have you got any custom repositories setup?

---

### Post by atoponce on 2007-01-22
Wait a minute.  Synaptic is complaining that you don't have the proper dependencies installed?  This can only mean 1 of 2 things:

1) You installed the dependency from source, rather than using apt-get.
2) You are trying to install a new application from source rather than using apt-get.

Synaptic and apt-get don't have problems with dependencies.  That's what makes Debian/Ubuntu so great.

So, I guess my questions would be these:

1) Please paste your /etc/apt/sources.list file.
2) How did you install postfix?
3) How are you trying to install postfix-mysql?

Thanks.

---

### Post by Isoss on 2007-01-22
alright, I never install from source! (if you mean using /configure make and make install)
This is my sources.list :


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://debian.meebey.net/](http://debian.meebey.net/) ./
deb [http://archive.ichthux.com/ichthux](http://archive.ichthux.com/ichthux) grace main
deb-src [http://archive.ichthux.com/ichthux](http://archive.ichthux.com/ichthux) grace main

#Beryl
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

I actually found postfix already installed and I am trying to install postfix using synaptic.

Thanks

---

### Post by Isoss on 2007-01-22
I also have this problem, after installing anything synaptic would nag saying: 
E: libgnomevfs2-common: subprocess post-installation script returned error exit status 127
E: amavisd-new: subprocess post-installation script returned error exit status 1

why is taht? what does it mean? does have anything to do with dependencies?

---

### Post by Isoss on 2007-01-22
ok, I'll make another post concerning the last problem and hope you can help me solve the dependencies problem.

---

### Post by atoponce on 2007-01-23
No wonder you're having issues.  First off, I would disable and completely remove all 3rd party repositories.  You're just asking for trouble there.  There is no **need** to install 3rd party repositories.  Ubuntu has over 20,000 packages in the main, restricted, universe and multiverse repositories.  You don't **need** any others.  After removing the repositories from your /etc/apt/sources.list:

```
sudo aptitude update
sudo aptitude upgrade
```Then try installing the software you need.  Because you have all those 3rd party repositories enabled, you are probably having several conflicts.

---

### Post by konst88 on 2007-01-23
And install them with aptitude, not with apt-get, because aptitude has better dependency problems resolver.

---

### Post by Isoss on 2007-01-23
ok guys, thanks, I'll update my sources.list now and check if this error can be resolved.

But I have a question here, since synaptic uses apt-get, isn't there a graphical interface for aptitude?

Thanks

---

