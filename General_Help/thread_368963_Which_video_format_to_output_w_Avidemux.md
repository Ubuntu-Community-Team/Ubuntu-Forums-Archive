---
title: "Which video format to output w/ Avidemux?"
date: 2007-02-23
forum: General Help
---

### Post by billdotson on 2007-02-23
I know how to transcode a file to normal avi and ogm using Avidemux but I don't know how to output to any other format other than avi or ogm. How do I if I can.. transcode to mpeg, xvid, divx, DVD mpeg (pretty much all of the most popular formats)

Also what is the best format to put video files in? I want to be able to play them without issues in Ubuntu and Windows and I want to be able to burn them with a program like dvdauthor to a DVD later on. Should I keep them in mpeg so I can just burn them to the DVD when I want to?

Also, say I wasn't going to burn them to a DVD. Which format is the most compatible, highest quality, and lowest file size (obviously one format won't have all 3 but the best mix of the 3) Using that "best" format would I lose that much quality transcoding into mpeg at a later time?

---

### Post by majoridiot on 2007-02-24
read the docs, man... 

[http://avidemux.sourceforge.net/doc/en/index.html](http://avidemux.sourceforge.net/doc/en/index.html)

there is no one-size fits all answer for video/audio compression.  however...

if you think you will want to burn something to dvd, keep it in mpeg and you won't lose quality
re-re-rencoding.

xvid is a good cross-platform format... i think even mac has caught up with decent codecs.  a 90
minute dvd can be compressed down to 700MB with no real loss of quality (unless you're fussy).

---

### Post by billdotson on 2007-02-24
can avidemux output to xvid or divx? it looks like it cannot output to anything other than ogm, avi or different mpeg types

---

### Post by Maestro23 on 2007-02-24
.

---

### Post by majoridiot on 2007-02-24
> **billdotson said:**
> can avidemux output to xvid or divx? it looks like it cannot output to anything other than ogm, avi or different mpeg types

you might not have all of the codecs you need.  the easiest way is:

```
sudo apt-get install automatix2
```

when installed, it will be under Applications-->System Tools-->Automatix... 
the extra codecs you want are listed under multimedia.  once installed, 
you will have axx to them through avidemux, etc.

(automatix will help you install a ton of other great things you might
want, too)

---

### Post by billdotson on 2007-02-24
I still don't know how to encode into the formats like xvid or divx w/ an avi container

---

### Post by majoridiot on 2007-02-24
again... read the documentation.  surprisingly, it tells you how. ;)

[http://avidemux.sourceforge.net/doc/en/guitour.xml.html](http://avidemux.sourceforge.net/doc/en/guitour.xml.html)

scroll down to "2. Left Toolbar" and go from there.

---

