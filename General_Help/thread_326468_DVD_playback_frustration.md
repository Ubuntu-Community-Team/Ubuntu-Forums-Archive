---
title: "DVD playback frustration"
date: 2006-12-27
forum: General Help
---

### Post by unrepper on 2006-12-27
I'm getting frustrated with all 3 of my media players (gxine, VLC, and
totem). The most reliabe is gxine. However, it works when it wants to.
I have ony been able to get Totem to work once that's because the DVD started playing
automatically when I put it in. VLC works occasionally but the volume is weak.

Gxine has a bug I can't seem to find or fix. The program starts fine there are no errors.
Once you select File then DVD you get an xine engine error saying the engine failed to start, no plug in found then you close that pop up message and there is another one saying error from xine engine, read error from, /dev/dvd. I have to restart a few times (3 or 4) and gxine will
work fine, sometimes I just boot up and it works fine. There are some DVD's I can't play at all
like Shrek and Spy Kids they're both retail versions and work in other devices.

Ubuntu is a new OS for me and I'm trying to get used to manipulating it.

Any help would be great.

---

### Post by Lord Illidan on 2006-12-27
Did you read this : [RestrictedFormats - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9")

---

### Post by ahaslam on 2006-12-27
Have you got libdvdcss2 installed? You need it for encrypted DVD's

I also recommend the use of Totem-xine instead of the gstreamer varient.

Tony.

PS. The links mentioned above are very useful, so much so one made it in my sig ;)

---

### Post by JohnBortion on 2006-12-27
Add multiverse to /etc/apt/sources.list.  It will look something like this:


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Go into synaptic, reload, and look for mplayer.  Install it.  This will solve your problems.

---

