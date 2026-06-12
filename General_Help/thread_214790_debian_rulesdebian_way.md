---
title: "debian rules?/debian way?"
date: 2006-07-13
forum: General Help
---

### Post by lex1 on 2006-07-13
here is a reply from a friend how runs debian on some packages.
how do debian rules apply to dapper packages and can i do what my friend says.and what's the "debian way"?
in dapper> see below


> 2) the source files that need to be installed you have mentioned but
> what about when you ./configure shuold they they be sent to a particular
> directory
> in the case of all the source packages.

Doing it the Debian way, you will not do a ./configure. "fakeroot
debian/rules binary" command compiles and creates the .deb packages.

> 3) mixmaster needs some deps to run? which source packages and again on
> runing
> ./configure which directorydo they go to?

Installing mixmaster on Debian will automatically install the deps.
"apt-get build-dep mixmaster" will install all of the packages
required to compile mixmaster. Again, there is no need to do a
./configure if you compile the packages the Debian way. But after you
build and install mixmaster, the files can be found in /etc/mixmaster
and /var/lib/mixmaster.

lex1:)

---

### Post by caserio on 2006-07-13
Hi,

Another example here: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by lex1 on 2006-07-13
not talking about kernels

---

### Post by RAOF on 2006-07-13
What your friend is talking about is building debian packages from deb-src.  You can see the Ubuntu packaging guide - it's a part of the help included in Ubuntu.  System->Help->?system, or something like that?->Packaging guide.

In general, any time you could do **fakeroot debian/rules binary** you're better off doing **dpkg-buildpackage -rfakeroot**.  And most of the time that you can get the deb-src, you could also get a binary .deb, so you wouldn't need to do **any of this** :).  

This only really applies when you want to build something from source.  There are a couple of reasons why you might want to do this, in order of likelyhood:
1) You want to run a more recent version than is in the repositories.  (Like, for example FFmpeg.  The FFmpeg devs don't want to hear from you if you're not running the very latest ffmpeg-svn)
2) You want something from Debian that's not in an Ubuntu repository, and the Debian binary package has some crazy dependencies not in Ubuntu
3) You want something that's not available as a .deb **anywhere**.

Of these, the method above will only work for 2).  For 1) & 3), you either need to see the packaging guide, or you can just ./configure, make, sudo make install like you normally would.

---

### Post by lex1 on 2006-07-13
many thanks for your clear explination

lex1

---

