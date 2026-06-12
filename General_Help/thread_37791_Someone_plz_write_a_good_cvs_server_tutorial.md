---
title: "Someone plz write a good cvs server tutorial"
date: 2005-05-28
forum: General Help
---

### Post by Gehaktbal on 2005-05-28
Could someone plz write a good basic cvs tutorial for debian or ubuntu. I have read a lot of sites but there is just to much info and not enough good basic sites that explain the setup for debian/ubuntu and how to work with it.

The idea of a code managing system really appeals me beceause c programming for embedded systems and assembly is a big chapter of my study.(electrotechnics) We also need to work in projectgroeps of like 4 to 5 persons so it could come in handy but we never got any info from school on the matter. What in my opinion is a total shame.

For now the most basic thing that i found was this info:

```
sudo apt-get install cvsd

In confgure screen delete defaults and type ‘/cvsroot’

mkdir /var/lib/cvsd/cvsroot

sudo cvs -d /var/lib/cvsd/cvsroot init

sudo cvsd-passwd /var/lib/cvsd/cvsroot USERNAME

Now change to the directory containg the code you wish to be added to the server.

export CVSROOT=:pserver:USERNAME@localhost:/cvsroot

cvs login

cvs import -m ‘PROJECT’ PROJECT VENDOR start
```

But i still cant login and it still says i have no repositories.

Furthermore the idea of repositories. Do u need a repos for everysingle project? And what is the typical structure of repostories?

i have something now like /var/lib/cvsd/cvsroot/school/CVSROOT

And i really dont think that is any good.

I configured cvsd with dpkg-reconfigure and gave for
```
chroot: /cvsroot
repositories:    /school : /test
```
Do i have to give the repositories the full lengt addres? like /var/lib/cvsroot/school?

How does it works? 

My setup is

1 ubuntu desktop + 1 ubuntu server

Plz some basic help this humble n00b

BTW, what about subversion? is it better to work with and is cvs outdated? or should i stick with cvs. Iam not gonna do any hard project coding but i would like to try code managment out.

---

### Post by Gehaktbal on 2005-05-30
Kick

---

### Post by fng on 2005-05-31
i would recommend subversion over cvs

Subversion has everything cvs has, but some more features like :
- Atomic commits
- Directory versioning
- Efficient branching and tagging
- ...

[http://svnbook.red-bean.com/en/1.1/ch01s03.html](http://svnbook.red-bean.com/en/1.1/ch01s03.html)

---

