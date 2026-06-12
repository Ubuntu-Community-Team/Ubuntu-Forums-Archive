---
title: "Gimp 2.9 or 2.10 beta"
date: 2013-05-12
forum: General Help
---

### Post by william_nbg on 2013-05-12
I'm a huge Gimp fan, and have been using it professionally for several years. I'd like to get my hands on a beta of the upcoming 2.10, but after several searches I haven't been able to find any deb, ppa, or working instructions how to compile it on 13.04.

Surprisingly, I found a earlier build for Windows and Mac. I always thought Gimp was made for Linux and then ported to Windows/Mac.

If anyone can point me in the right direction, I'd really appreciate it.

Thanks :D

---

### Post by zombifier25 on 2013-05-12
[http://www.gimpusers.com/forums/gimp-developer/15280-compile-gimpv2-9-1-for-debian-wheezy-sid](http://www.gimpusers.com/forums/gimp-developer/15280-compile-gimpv2-9-1-for-debian-wheezy-sid)

May or may not work on Ubuntu. Try at your own risk (then again, you want to use GIMP 2.9 :D )

---

### Post by william_nbg on 2013-05-12
> **zombifier25 said:**
> [http://www.gimpusers.com/forums/gimp-developer/15280-compile-gimpv2-9-1-for-debian-wheezy-sid](http://www.gimpusers.com/forums/gimp-developer/15280-compile-gimpv2-9-1-for-debian-wheezy-sid)

May or may not work on Ubuntu. Try at your own risk (then again, you want to use GIMP 2.9 :D )

Thanks for the tip.

Although it sounds like a possibility, I'm afraid of screwing up my current Gimp which I need for work on occasion. According to the the above website, 2.10  could be released by the end of the year - hooray! :P

Maybe, I'll give it a go, maybe I'd better wait for a beta ppa or deb?

But thanks.

---

### Post by n0yd on 2013-05-28
> **william_nbg said:**
> Thanks for the tip.

Although it sounds like a possibility, I'm afraid of screwing up my current Gimp which I need for work on occasion. According to the the above website, 2.10  could be released by the end of the year - hooray! :P

Maybe, I'll give it a go, maybe I'd better wait for a beta ppa or deb?

But thanks.

I know [this guide]("http://www.zanshine.com/blog/stephane-richard/software/2011-10-05/cutting-edge-gimp-in-latest-ubuntu/") was originally written quite some time ago, but it was updated September 2012.  I just used it on 13.04 (raring) and it worked fine.  And it will not wipe out gimp stable from the repository, so don't worry about that.  So far 2.9 is working fine for me. Though do not be surprised if you encounter bugs, these are straight from their git,so things can change ALL the time.  It isn't like a git build snapshot that was taken for the sole purpose of making semi-stable and tested, so people could have a usuable uptodate(ish) build of gimp 2.9. I'm not saying 2.9 won't work fine for you, it's just that there is no testing done to ensure everything works.

EDIT: BTW, it's actually good for people like me and you to try out 2.9 (gimp dev) and report bugs as we come across them in our normal use of the application.  This way the developers will have an easier time tracking and fixing bugs.  So if you do find a bug, please be sure to report it on gimps bug tracker. :)

Here is the howto on reporting bugs: [http://www.gimp.org/bugs/howtos/bugzilla.html](http://www.gimp.org/bugs/howtos/bugzilla.html)

---

### Post by william_nbg on 2013-05-28
> **n0yd said:**
> I know [this guide]("http://www.zanshine.com/blog/stephane-richard/software/2011-10-05/cutting-edge-gimp-in-latest-ubuntu/") was originally written quite some time ago, but it was updated September 2012.  I just used it on 13.04 (raring) and it worked fine.  And it will not wipe out gimp stable from the repository, so don't worry about that.  So far 2.9 is working fine for me. Though do not be surprised if you encounter bugs, these are straight from their git,so things can change ALL the time.  It isn't like a git build snapshot that was taken for the sole purpose of making semi-stable and tested, so people could have a usuable uptodate(ish) build of gimp 2.9. I'm not saying 2.9 won't work fine for you, it's just that there is no testing done to ensure everything works.

EDIT: BTW, it's actually good for people like me and you to try out 2.9 (gimp dev) and report bugs as we come across them in our normal use of the application.  This way the developers will have an easier time tracking and fixing bugs.  So if you do find a bug, please be sure to report it on gimps bug tracker. :)

Here is the howto on reporting bugs: [http://www.gimp.org/bugs/howtos/bugzilla.html](http://www.gimp.org/bugs/howtos/bugzilla.html)


Thanks a lot.

I'll give it a try as soon as I can.

And, I'll try and figure out how to report bugs.;)

---

