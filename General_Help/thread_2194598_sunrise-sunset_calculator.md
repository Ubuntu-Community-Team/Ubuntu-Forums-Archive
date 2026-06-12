---
title: "sunrise-sunset calculator"
date: 2013-12-19
forum: General Help
---

### Post by Dan Z on 2013-12-19
When I used 10.40, I had a sunrise sunset calculator displacing on my desktop. It was a very small window, all it showed was the 2 times.

It was something available in 10.40, that I found just browsing the software center.

Now I  am using 12.04, and I can't find anything close, have done many searches of Software center, synaptic and internet.

can anyone suggest how to set this up once again?

Thanks Dan

---

### Post by tgalati4 on 2013-12-19
Any of these?

tgalati4@Mint14-Extensa ~ $ apt-cache search sunrise sunset
libdatetime-astro-sunrise-perl - module for computing the time of sunrise and sunset
libdatetime-event-sunrise-perl - Calculate sunrise and sunset for a given time and place
remind - sophisticated calendar and alarm program
stellarium - real-time photo-realistic sky generator
tkremind - Tk GUI interface to remind
wyrd - text-based calendar application

---

### Post by Dan Z on 2013-12-20
Thanks for the reply-
RE:
libdatetime-astro-sunrise-perl - module for computing the time of sunrise and sunset
libdatetime-event-sunrise-perl - Calculate sunrise and sunset for a given time and place

 I cannot figure out how to run either of these, if I put in to terminal "libdatetime-astro-sunrise-perl" 
 or "libdatetime-event-sunrise-perl" both come back as command not found.

in I do LOCATE- 
dan@acer-ub:~$ locate libdatetime-astro-sunrise-perl
/home/dan/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,reviews,filter,en,any,any,any,libdatetime-astro-sunrise-perl,page,1,helpful,02b1b52880609d2e775c1f421b138a25
/home/dan/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,reviews,filter,en,ubuntu,oneiric,any,libdatetime-astro-sunrise-perl,page,1,,b97eb13bd9760e31955c040e98f9e885
/home/dan/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,reviews,filter,en,ubuntu,precise,any,libdatetime-astro-sunrise-perl,page,1,,4251210667f8df860cfbbd0848acb2fc
/usr/share/doc/libdatetime-astro-sunrise-perl
/usr/share/doc/libdatetime-astro-sunrise-perl/changelog.Debian.gz
/usr/share/doc/libdatetime-astro-sunrise-perl/changelog.gz
/usr/share/doc/libdatetime-astro-sunrise-perl/copyright
/var/lib/dpkg/info/libdatetime-astro-sunrise-perl.list
/var/lib/dpkg/info/libdatetime-astro-sunrise-perl.md5sums

RE: remind- man says it will give sunrise, sunset, needs setup
RE: tkremind - Tk GUI interface to remind --- output display for remind

RE: wyrd- no mention of sunrise -sunset in man

RE: stelarium -- nice program for stargazer

In summary- wha tI wanted not here, but I may be able to get remind to do what I want.

ALso I recall that there is a repository of 10.4 programs somewhere. anyone know where it is?

thanks Dan

---

### Post by oldfred on 2013-12-20
Some info on old repositories.
 Old Releases past support
 [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I searched with google for python & sunrise sunset and found several python programs also. One or two looked interesting, but do not know otherwise.

---

### Post by steeldriver on 2013-12-20
... just found this, it can be configured to show sunrise/sunset times along the bottom, possibly you can set an empty map if you don't want that as well

```

$ apt-cache show sunclock
Package: sunclock
Priority: optional
Section: universe/x11
.
.
.
Description-en: fancy clock showing time and geographical data
 sunclock is an X11 application that displays a map of the Earth and
 indicates the illuminated portion of the globe by drawing sunlit
 areas dark on light, night areas as light on dark.  In addition to
 providing local time for the default timezone, it also displays GMT
 time, legal and solar time of major cities, their latitude and
 longitude, and the mutual distances of arbitrary locations on Earth.
 Sunclock can display meridians, parallels, tropics and arctic
 circles.  It has builtin functions that accelerate the speed of time
 and show the evolution of seasons.
Homepage: http://www.arvernes.com/wiki/index.php/Sunclock
Description-md5: a16bc3d9b67da7b8449d4f6f9d1b1982
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

[ATTACH=CONFIG]248763[/ATTACH]

---

### Post by tgalati4 on 2013-12-20
Show me a round rock. 
Too shiny.  Too dull. Too sharp.
Don't know what I want.

You can't run library files.  They are part of other programs to calculate or use sunset/sunrise information.

tgalati4@Mint14-Extensa ~ $ apt-cache depends libdatetime-event-sunrise-perl
libdatetime-event-sunrise-perl
  Depends: perl
  Depends: libdatetime-perl
  Depends: libdatetime-set-perl

Perhaps there is a perl script that uses the library to display sunrise and sunset.

And there are several:  [http://realworldnumbers.com/the-days-are-getting-shorter-perl-script-to-calculate-sunrise-and-sunset/](http://realworldnumbers.com/the-days-are-getting-shorter-perl-script-to-calculate-sunrise-and-sunset/)

---

### Post by Dan Z on 2013-12-28
The winner is:

Sunclock!

Thanks all for the help, Dan

---

