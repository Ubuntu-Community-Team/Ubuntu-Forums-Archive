---
title: "the official way to install java sdk for ubuntu ?"
date: 2004-10-14
forum: General Help
---

### Post by kixvn on 2004-10-14
i checked on the official FAQ from ubuntulinux.org
they mentioned this link [http://z42.de/debian/](http://z42.de/debian/) but it said not to support java sdk anymore since it was moved to unstable branch of debian ..

another way is in this link [http://wiki.osuosl.org/display/DEV/Java+on+Debian](http://wiki.osuosl.org/display/DEV/Java+on+Debian)

but it needs some package from the pure debian

i don't know if doing like that would mess my ubunto installation or not

is there any offical package for ubuntu only to solve this ?

thanks

---

### Post by cseg on 2004-10-14
I find it exremely easy to download the jdk from Sun's site and just install it into /usr/local/jdk5whatever.  What is the benefit of doing it the Debian way?  Ok, you end up with java in /usr/java.  Is that really a benefit?  Java is its own universe, and doing it the Debian way puts things in unexpected places.

I use Java on a number of different platforms, and I prefer that things show up where they are "supposed" to be.

---

