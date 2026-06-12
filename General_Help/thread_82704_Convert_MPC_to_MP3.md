---
title: "Convert MPC to MP3"
date: 2005-10-27
forum: General Help
---

### Post by Koybe on 2005-10-27
Hello, 

I'd like to convert some MPC file to MP3. I get [on this thread](http://www.ubuntuforums.org/showthread.php?t=48007)  and get this script. It seems ok but once i selected de files and call for conversion, i'm prompted with flac, ogg or wav files.

I installed all these packages : lame, flac, vorbis-tools, libid3, zenity... what else can i do?

---

### Post by nudd on 2005-10-27
Is there any problem with using something like this:

```

mppdec <mpcfilename> - | lame --preset-standard - <newfilename>

```

---

### Post by Koybe on 2005-10-27
I do not have this command : mppdec.

libmpcdec3 and gstremaer0.8-musepack are installed.

---

### Post by aer on 2006-11-21
you should install mppdec program
you can get it from [http://www.musepack.net/index.php?pg=lin](http://www.musepack.net/index.php?pg=lin)

---

### Post by adamkane on 2006-11-21
You can get a .deb from rarewares.org.

mppdec/mppenc are just binaries, so you can just download the source and move the files to /usr/bin.

---

### Post by musicfan on 2007-08-05
Softe Audio Converter
[http://www.softe.net](http://www.softe.net)

---

### Post by phreadom on 2007-09-04
> **musicfan said:**
> Softe Audio Converter
[http://www.softe.net](http://www.softe.net)

Why would we care about a Windows only $30 piece of software?

---

### Post by wavesound on 2008-02-02
Hi 
I to lost some time looking at that!!

Won't run on Linux then!!!


Cheers
Bob

---

