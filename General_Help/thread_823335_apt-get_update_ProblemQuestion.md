---
title: "apt-get update Problem/Question"
date: 2008-06-09
forum: General Help
---

### Post by matey3 on 2008-06-09
Hello:

I have a server that needs to be updated but every time I run the apt-get update, it returns a lot of errors.
I believe the links are the problem. So I wonder where apt-get looks into in order to get the updates from and how I could edit that file to correct the problem.

I have noticed a lot of times when you try to get an update it looks in links that don't exist or have been changed or the address has spaces in it??!! (which if course then it become %2 instead etc. etc...).

Thanks a lot in advance!

---

### Post by kpkeerthi on 2008-06-09
It looks in /etc/apt/sources.list where the repositories are configured.

---

### Post by geirha on 2008-06-09
/etc/apt/sources.list and /etc/apt/sources.list.d/*.list

---

### Post by dburnett77 on 2008-06-09
> **matey3 said:**
> Hello:

I have a server that needs to be updated but every time I run the apt-get update, it returns a lot of errors.
I believe the links are the problem. So I wonder where apt-get looks into in order to get the updates from and how I could edit that file to correct the problem.

I have noticed a lot of times when you try to get an update it looks in links that don't exist or have been changed or the address has spaces in it??!! (which if course then it become %2 instead etc. etc...).

Thanks a lot in advance!

Try running it as su, or sudo.  If you're not already.

You could also try the GUI of Synaptic, and in the settings menu update repositories.

Barring all that, use binding within iptables to list the given ip addresses of the main servers, then enter:

apt-get update xxx.xxx.xxx.xxx

---

### Post by zvacet on 2008-06-09
```
cat /etc/apt/sources.list
```

Post it here.

---

### Post by matey3 on 2008-06-10
THANKS For replies.
Sorry for late reply...lol my machine froze (fire fox did something as usual?) and I reset the machine then it would not boot any more lol the same grub problem... it keeps changing my darn config to hd0,0 hell its hd0,2 why does it keep changing beats me...
any ways this machine i am sshing to is old >I know but its not mine;
HERE are the errors;

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]





THIS IS THE FILE:

cat: sources.lst: No such file or directory
root@fox:/etc/apt# cat sources.list
##deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
#[http://security.ubuntu.com/ubuntu/indices/](http://security.ubuntu.com/ubuntu/indices/)
#[http://security.ubuntu.com/ubuntu/indices/override.breezy-security.extra.main](http://security.ubuntu.com/ubuntu/indices/override.breezy-security.extra.main)

deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by geirha on 2008-06-10
Are you using breezy? what does the following command in a terminal say:
```
lsb_release -a
```

---

### Post by matey3 on 2008-06-11
oh thanks.. been looking for that command for a while.. uname -a doesnt give u the right info cat /proc/version doesnt either I wanted to know whats running on that damm server and this is what I got;

root@fox:/etc/apt# lsb_release -a
LSB Version:    n/a
Distributor ID: Ubuntu
Description:    Ubuntu (The Breezy Badger Release)
Release:        5.10
Codename:       breezy
root@fox:/etc/apt# 


any way there is No breezy files on ubuntu.com at all. (I also used the GUI update mgr to no avail. same errors. I think this is the only server here which can even run GUI lol), since the sources.list file looks for those locations which apparently dont exist any more I guess I have to upgrade this server. I was (still am) reluctant since it is running Xend and xm list gives me a virtual domain with a couple of virtual servers running god knows what??  But I do appreciate all your help. Everyone here has been great and I am grateful to have learned more stuff.

Thanks a lot!

---

### Post by geirha on 2008-06-11
Ubuntu Breezy support ended april 2007. That's probably why the breezy repositories are gone now. You should've upgraded to Dapper over a year ago. Dapper is supported till 2009 for the desktop edition, and 2011 for the server edition. 

There's probably a way to get it upgraded to Dapper still though, but I'm not sure how.

---

