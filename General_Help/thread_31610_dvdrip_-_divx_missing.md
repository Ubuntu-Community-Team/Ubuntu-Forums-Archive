---
title: "dvd::rip - divx missing?"
date: 2005-05-03
forum: General Help
---

### Post by jiyuu0 on 2005-05-03
ok... i've added this
[http://ubuntuguide.org/#dvdrip](http://ubuntuguide.org/#dvdrip)

it can be installed and is able to rip dvd to xvid

now... how do i rip dvd to divx
i think something is missing? anybody know what is missing?

for the output of xvid... i noticed there's like lines... is it normal? or is it gotta do with the settings...

---

### Post by mrbass on 2005-05-04
[http://forum.doom9.org/showthread.php?&threadid=91894](http://forum.doom9.org/showthread.php?&threadid=91894)

---

### Post by arman.haghi on 2008-02-10
> **jiyuu0 said:**
> ok... i've added this
[http://ubuntuguide.org/#dvdrip](http://ubuntuguide.org/#dvdrip)

it can be installed and is able to rip dvd to xvid

now... how do i rip dvd to divx
i think something is missing? anybody know what is missing?

for the output of xvid... i noticed there's like lines... is it normal? or is it gotta do with the settings...
Hey mate,

I know this is from an old post, but I thought you'd find this interesting:

A. Here's some quality comparisons between the two(3):

[http://nerds.palmdrive.net/video/Jan2006/index.html](http://nerds.palmdrive.net/video/Jan2006/index.html)

---

B. Also, here are a few points from some "DivX Vs Xvid" forum debates(2):

1. Both DivX and XviD support each other
2. Playing quality is pretty much the same
3. Xvid [is] less obtrusive and lighter
4. DivX(tm) includes spyware and crap which you probably don't want
5. XviD on the otherhand doesn't but the filter isn't really optimized and has some backwards compatibility issues
6. "ffdshow" is worth a look also
7. "XviD encoded files can be ... played in a DivX compatible DVD player, as long as they are not ... using features unsupported by DivX (e.g. three warppoints instead of one), since such features are not considered "MPEG-4 compliant" by DivX."(1.5)

IMHO, the basic thing is to use two-pass and you're probably going to get a very good, very similar result from either.

---

C. DivX 6 Installation

I'm running 64bit Kubuntu 7.10 and its "working" for me, but my DVD::rip doesn't know about it...

[http://labs.divx.com/DivXLinuxCodec](http://labs.divx.com/DivXLinuxCodec)

to download the DivX for Linux package

[http://download.divx.com/labs/divx611-20060201-gcc4.0.1.tar.gz](http://download.divx.com/labs/divx611-20060201-gcc4.0.1.tar.gz)

Then extract it all to a folder, go to that folder and open a terminal, type:

sudo ./install.sh

and enter your password

you'll see the terms and conditions, scroll down and at the bottom hit q to quit the license nonesense, and then you'll be asked if you agree.

if you agree type "yes" (not just "y") and hit enter.

---

Sources:
1.  [http://en.wikipedia.org/wiki/XviD](http://en.wikipedia.org/wiki/XviD)
1.5 [http://www.velocityreviews.com/forums/t373273-divx-vs-xvid.html](http://www.velocityreviews.com/forums/t373273-divx-vs-xvid.html)
2.  [http://club.cdfreaks.com/f3/divx-vs-xvid-128001/](http://club.cdfreaks.com/f3/divx-vs-xvid-128001/)
3.  [http://nerds.palmdrive.net/video/Jan2006/index.html](http://nerds.palmdrive.net/video/Jan2006/index.html)

---

