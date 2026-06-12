---
title: "making linpal... curl issues?"
date: 2005-10-18
forum: General Help
---

### Post by nowxisxforever on 2005-10-18
Alright, so.  I'm pretty new to all this, and I am at a loss as to what to do.
I'm trying to install [linpal]("http://www.ruinedsoft.com/linpal/"), and it's not working.  It says to make, and I run make, and this is what it spits at me:

kandace@Sister:~/Desktop/linpal-0.5-binary$ make
g++ -Wall -pedantic -ansi gtkmain.o palnet.o palcallback.o gtkbubble.o palbubble.o palclient.o gtkasset.o gtkbigpage.o -o linpal `curl-config --libs` `pkg-config --libs gtk+-2.0 libglade-2.0 glib-2.0 gthread-2.0`
/bin/sh: curl-config: command not found
gtkbigpage.o(.text+0x53e0): In function `MyGet(void*)':
: undefined reference to `curl_easy_init'
gtkbigpage.o(.text+0x5545): In function `MyGet(void*)':
: undefined reference to `curl_easy_setopt'
gtkbigpage.o(.text+0x5560): In function `MyGet(void*)':
: undefined reference to `curl_easy_setopt'
gtkbigpage.o(.text+0x557b): In function `MyGet(void*)':
: undefined reference to `curl_easy_setopt'
gtkbigpage.o(.text+0x5596): In function `MyGet(void*)':
: undefined reference to `curl_easy_setopt'
gtkbigpage.o(.text+0x55b0): In function `MyGet(void*)':
: undefined reference to `curl_easy_setopt'
gtkbigpage.o(.text+0x55cd): more undefined references to `curl_easy_setopt' follow
gtkbigpage.o(.text+0x55d8): In function `MyGet(void*)':
: undefined reference to `curl_easy_perform'
gtkbigpage.o(.text+0x55f4): In function `MyGet(void*)':
: undefined reference to `curl_easy_cleanup'
collect2: ld returned 1 exit status
make: *** [default] Error 1

Now, I went in and selected random things from apt-get, like curl and libcurl3 and I already have these, and it's not working.  Like I said, I have no clue what I'm doing really and would appreciate some help.  I'm sure there's some really obvious solution, but I don't know what it is.  Help?   ](*,)

---

### Post by nowxisxforever on 2005-10-19
Any help at all?  This is really aggrivating...

---

