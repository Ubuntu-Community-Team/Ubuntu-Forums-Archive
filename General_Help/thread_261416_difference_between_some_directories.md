---
title: "difference between some directories"
date: 2006-09-20
forum: General Help
---

### Post by jethro10 on 2006-09-20
I've been using Ubuntu (linux) for 6 month now and all is well.
I'm starting to dig deeper and am struggling with understanding the filesystem. Lots of sites & articles state /blabla is for x,y or z, but not why...

I'm stuck on why we have 3 directories :-

/usr/bin
/bin
/sbin

It sorta looks like they are similar. Can someone explain or point me to an explination of the subtleties between them?

Also are the directory structures of all linuxes identical?

Ta
J

---

### Post by monktbd on 2006-09-20
> **jethro10 said:**
> 
/usr/bin
/bin
/sbin


these all are historically grown.

/sbin contains usually programs only root is allowed to execute.

/bin contains most of the lowlevel commandline tools like grep, chown, pwd, dd, etc... so the essential commandline programs. most of these programs have been on linux for ages and also on unix.

/usr/bin (usr = unix system ressources) contains most user commands. there are a lot of links to the actual programs in there.


you can download a pdf from
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)
where it explains all the common directories and their files.

---

### Post by jethro10 on 2006-09-20
Thanks for the link. Downloading now.

J

---

