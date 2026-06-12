---
title: "trying to compile GOPchop..help...."
date: 2005-05-02
forum: General Help
---

### Post by luna6 on 2005-05-02
Hello finally found a linux gui program that can losslessly cut/edit mpeg files ([http://gopchop.org/)...I](http://gopchop.org/)...I) use a windows computer to record tv shows in mpeg2 format and would like to edit out commercials etc....
anyways i download the latest one...the ./configure command would stop on various things being missing and I would try to sudo apt-get the appropriate files when it stopped on an error..the last one I cannot seem to get around....which says..I did install mpeg2dec via sudo apt-get install mpeg2dec as well (and when I could not get the program to compile tried to install the .deb package with dpkg --install but it would fail as well and had to remove i)...  :

checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... no
checking for XShmCreateImage in -lXext... yes
checking for XvShmCreateImage in -lXv... no
checking ddraw.h usability... no
checking ddraw.h presence... no
checking for ddraw.h... no
checking for sdl-config... no
checking mpeg2dec/mpeg2.h usability... no
checking mpeg2dec/mpeg2.h presence... no
checking for mpeg2dec/mpeg2.h... no
configure: error: Couldn't find header mpeg2dec/mpeg2.h!

---

### Post by luna6 on 2005-05-02
just posting this reply if anybody else comes across the problem...i was just missing dev files for mpeg2dec, which was libmpeg2-4-dev. From their webpage saw that GOPchop had a irc channel, so decided to give it a shot, and the developer was friendly and helpful enough to help me solve my problems in a few minutes. The program is slick and would recommend it to anybody that needs a lossless mpeg editing program (like womble's mpeg2vcr on the windows side)...

---

