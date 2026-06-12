---
title: "apt conflicts with libc6 to install bootsplash"
date: 2005-04-29
forum: General Help
---

### Post by neokod on 2005-04-29
Hi,

I try to install bootsplash from the repositories :
deb [http://www.bootsplash.de/files/debian](http://www.bootsplash.de/files/debian) unstable main
deb-src [http://www.bootsplash.de/files/debian](http://www.bootsplash.de/files/debian) unstable main

But when I do my apt-get install bootsplash i have this dependencies error :
bootsplash: 
 Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

What can I do please ?

---

### Post by rwabel on 2005-05-04
I've the same problem for the amule cvs repository. They also depend on a newer libc6 package

Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

I hope ubuntu will update sooner or later that package. Or is there an official way to ask the developpres for a newer package?

thanks

---

### Post by neokod on 2005-05-21
Nobody used the bootsplash under Ubuntu ?

No idea for the libc6 dependency problem please ?

---

### Post by rwabel on 2005-05-21
[QUOTE=neokod]Nobody used the bootsplash under Ubuntu ?

No idea for the libc6 dependency problem please ?[/QUOTE]
 there is a solution to the libc6 problem. search again in the forum and you'll find it :-) Can't remember the threads!

---

### Post by neokod on 2005-05-21
On this thread :
[http://ubuntuforums.org/showthread.php?t=33406&highlight=2.3.2.ds1-20ubuntu13](http://ubuntuforums.org/showthread.php?t=33406&highlight=2.3.2.ds1-20ubuntu13)
the solution is to comment marillat repository, i have try, but after my apt-get update the problem is still here.

I have also try to install with apt-get install -t hoary bootsplash

In the repository I see a libc6.1 package but when it's virtual packages for :
  libdb2 libdb1-compat initscripts
So, I have installed libdb2 libdb1-compat initscripts

And the most interesting post is here :
[http://ubuntuforums.org/showthread.php?t=548&page=3](http://ubuntuforums.org/showthread.php?t=548&page=3)

I have try to download the libc6-i686 from :
[http://www.gotom.jp/~gotom/debian/glibc/2.3.2.ds1-21_i386.sched/](http://www.gotom.jp/~gotom/debian/glibc/2.3.2.ds1-21_i386.sched/)

 and install it but apt-get return me :
# di libc6-i686_2.3.2.ds1-21_i386.deb
dpkg : concernant libc6-i686_2.3.2.ds1-21_i386.deb contenant libc6-i686, problème de pré-dépendance :
 libc6-i686 pré-dépend de libc6 (= 2.3.2.ds1-21)
  libc6 est installé, mais sa version est 2.3.2.ds1-20ubuntu13.
dpkg : erreur de traitement de libc6-i686_2.3.2.ds1-21_i386.deb (--install) :
 problème de pré-dépendance - libc6-i686 non installé
Des erreurs ont été rencontrées pendant l'exécution :
 libc6-i686_2.3.2.ds1-21_i386.deb

(do you know a tricks to switch the console message in english for a better reports ?)

Is anybody have already installed the bootsplash package on Ubuntu ?

---

### Post by rwabel on 2005-05-22
The one from gotom.jp are working fine.
you need more than only
[http://www.gotom.jp/~gotom/debian/glibc/2.3.2.ds1-21_i386.sched/libc6-i686_2.3.2.ds1-21_i386.deb]("http://www.gotom.jp/%7Egotom/debian/glibc/2.3.2.ds1-21_i386.sched/libc6_2.3.2.ds1-21_i386.deb")

as stated in his post
 ```
 You need to do libc6_2.3.2.ds1-21 first, then the dev, and i686 packages
``` 
[ http://www.gotom.jp/~gotom/debian/glibc/2.3.2.ds1-21_i386.sched/libc6_2.3.2.ds1-21_i386.deb]("http://www.gotom.jp/%7Egotom/debian/glibc/2.3.2.ds1-21_i386.sched/libc6_2.3.2.ds1-21_i386.deb")
[http://www.gotom.jp/~gotom/debian/glibc/2.3.2.ds1-21_i386.sched/libc6-dev_2.3.2.ds1-21_i386.deb]("http://www.gotom.jp/%7Egotom/debian/glibc/2.3.2.ds1-21_i386.sched/libc6_2.3.2.ds1-21_i386.deb")

and you can even take the locale one.

I hope the problem is solved now :-)
for chaning the message to english you need to change the language from french to english

[QUOTE=neokod]On this thread :
[http://ubuntuforums.org/showthread.php?t=33406&highlight=2.3.2.ds1-20ubuntu13]("http://ubuntuforums.org/showthread.php?t=33406&highlight=2.3.2.ds1-20ubuntu13")
the solution is to comment marillat repository, i have try, but after my apt-get update the problem is still here.

I have also try to install with apt-get install -t hoary bootsplash

In the repository I see a libc6.1 package but when it's virtual packages for :
  libdb2 libdb1-compat initscripts
So, I have installed libdb2 libdb1-compat initscripts

And the most interesting post is here :
[http://ubuntuforums.org/showthread.php?t=548&page=3]("http://ubuntuforums.org/showthread.php?t=548&page=3")

I have try to download the libc6-i686 from :
[http://www.gotom.jp/~gotom/debian/glibc/2.3.2.ds1-21_i386.sched/]("http://www.gotom.jp/%7Egotom/debian/glibc/2.3.2.ds1-21_i386.sched/")

 and install it but apt-get return me :
# di libc6-i686_2.3.2.ds1-21_i386.deb
dpkg : concernant libc6-i686_2.3.2.ds1-21_i386.deb contenant libc6-i686, problème de pré-dépendance :
 libc6-i686 pré-dépend de libc6 (= 2.3.2.ds1-21)
  libc6 est installé, mais sa version est 2.3.2.ds1-20ubuntu13.
dpkg : erreur de traitement de libc6-i686_2.3.2.ds1-21_i386.deb (--install) :
 problème de pré-dépendance - libc6-i686 non installé
Des erreurs ont été rencontrées pendant l'exécution :
 libc6-i686_2.3.2.ds1-21_i386.deb

(do you know a tricks to switch the console message in english for a better reports ?)

Is anybody have already installed the bootsplash package on Ubuntu ?[/QUOTE]

---

