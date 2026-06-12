---
title: "quicktime plugins not working"
date: 2006-12-30
forum: General Help
---

### Post by miki90 on 2006-12-30
Most sites work fine with firefox plugins like gmplayer and totem, however when I go to [www.americafreetv.com](www.americafreetv.com) and try to open one of the video streams I can't get anything with totem, mplayer or vlc despite having all of these plugins working on other sites. I'm using the media player connectivity plugin under firefox to configure which plugin should open the content.  Please advise if you are able to open these video streams.
Thanks,

---

### Post by pay on 2006-12-30
You might need open quicktime. [http://www.openquicktime.org/](http://www.openquicktime.org/) 
Using the instructions from their site do```
sudo aptitude install build-essential cvs checkinstall autoconf automake libtool
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/openquicktime login
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/openquicktime co OpenQuicktime
cd OpenQuicktime
./bootstrap
 ./configure
 make
sudo checkinstall
```You **_might_** now need to recompile mplayer with support.

---

### Post by miki90 on 2006-12-30
Anybody else able to open those streams?
Thanks

---

### Post by fragos on 2006-12-30
Perhaps its the version of quicktime that's the issue.  I've foun d that there are times when videos won't play in a browser plugin but work just fine with mplayer if you download them first.

---

### Post by miki90 on 2006-12-30
Thanks for the replies.  They're streaming videos so I don't think I&#314;l be able to download the files.  Just curious if anyone else has a problem when accessing [www.americafreetv.com](www.americafreetv.com)

---

### Post by fragos on 2006-12-30
I couldn't get these streams to play.  I did however go to the site link for Buffalo Hearts and was able to dounload  a Teaser which was in MP4 format and it played with mplayer.

---

### Post by miki90 on 2006-12-31
Thank you. Happy New Year to all

---

