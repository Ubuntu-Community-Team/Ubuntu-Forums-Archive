---
title: "updated to 18.10 freecad-daily has stuck me into not being able to fix or upgrade"
date: 2019-05-12
forum: General Help
---

### Post by deathguppie on 2019-05-12
Preamble:  So I use an older laptop for work (I'm blue collar and use it for doing CNC drawings and the like)  I use Freecad for most of that because it works and my employer doesn't have the kind of money that could afford $3k per year for the few jobs I use it on.  I'm self taught so all of that just helps me get more useful and increases my pay, but before I do a complete rewipe and install on this machine I thought I'd ask.

Problem:  I've upgraded to 18.10 (Kubuntu, but the underlying apt system should be the same, I'm using command line).  After going through 18.04 to 18.10 I decided to install the freecad-daily repository and get the newest version.  It seems there is a conflict and the libraries cannot be installed so I tried an " apt --fix-broken install" .  It errored out with stuff like ```
dpkg: error processing archive /tmp/apt-dpkg-install-Sx8Zi2/5-libocct-data-exchange-7.3_7.3.0+dfsg1-3_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libTKBinXCAF.so.7', which is also in package libopencascade-data-exchange-7.1.0:amd64 7.1.0-0ppa1~ubuntu17.04.1

``` .. A bunch of these.

I tried removing freecad-daily, doesn't work.  Tried removing the sources and updating then upgrading, still wants me to fix the packages which wont fix.  

Any help would be appreciated, I know this isn't an easy problem because I'm pretty experienced with Linux but if anyone has a fix to this "kills my system" loop issue I'd be more than happy to put some golden stars on my fridge with your name and post a picture on reddit to prove it.

system: Dell Vostro laptop Intel core I5, GPU Nvidia 240M.  Software, Kubuntu 18.10 uname -a 4.15.0-48-generic #51-Ubuntu SMP Wed Apr 3 08:28:49 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by him610 on 2019-05-13
If it were me, when using any application for work, I would stick to a LTS release. One needs stability with work-related programs. The interim releases - 18.10, 19.04, 19.10, etc all come with instability and the need to upgrade every six months or so.
Recommend you back up all of your data then reinstall LTS 18.04.
I hope your employer appreciates your dedication and perseverance in getting the job done.

---

