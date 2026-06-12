---
title: "dvdrip / transcode / dvdbackup / dvdshrink"
date: 2005-04-23
forum: General Help
---

### Post by brickbat on 2005-04-23
Hi,  Does anyone have a working solution for all the dependency / installation problems?  If they could post a howto that would be great.  I've been struggling to   resize a dvd for the last 3 days.  I know about dvdshrink.  It kept crashing on me when I tried to deselct some audio streams.

Also, does anyone know if it is possible to use dvdbackup to strip audio streams or to use dvdbackup from a directory rather than dvd.

ciao
bb

---

### Post by doclivingston on 2005-04-23
After seeing everyone say that they can't get it to work, I'm going to have to figure out why mine works. I just `apt-get install`ed everything and it worked; maybe I was lucky with the versions that happened to be there at the time or something (this was back at the start of March, with pre-Hoary).


The versions of various of things that I have installed from the Marillat repository are:

dvdrip   0.52.2-0.0
transcode   0.6.14-sarge0.0
mjpegtools & libmjpegtools-   1.6.2-0.8
libavcodecs   20050304-sarge0.0
libdivxdecore0 & libdivxencore0   5.0.1-1
xvidcore   1.1.0-beta1-0.0
xvid4conf   1.12-0.0
libfame-0.9   0.9.0-0.1
liblame0   3.96.1-1

I think that everything else is the standard Hoary version.

---

