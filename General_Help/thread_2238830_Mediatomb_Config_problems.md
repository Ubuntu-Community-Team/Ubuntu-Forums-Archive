---
title: "Mediatomb Config problems"
date: 2014-08-10
forum: General Help
---

### Post by iclestu on 2014-08-10
Hi there,

I have recently got Mediatomb up and running but am struggling a little with a couple of issues - in order of importance:

1. I cannot rewind/fastforward from my tv (a pretty new LG smart tv)
2. There are no thumbnails on any files (either jpgs or movies)
3. music album art doesn't show

All these features works if I stream media from my windows box so I am assuming this isnt a limitation for the TV but has something to do with my config file but despite googling I am not really sure where to start?

Of the 3 I'm not sure I care too much about the latter 2 but #1 is a real pia.

Any help (even if it is of the form: read this post/blog/help file!) would be most gratefully received :-)

---

### Post by iclestu on 2014-08-12
<shameless bump>

Anyone got any ideas?

---

### Post by tgalati4 on 2014-08-12
What program are you using to stream media from your Window's box?

I don't think mediatomb supports rewind or fast-forward--just play, pause, and stop.  Mediatomb is a UPnP server not a DNLA server, but it supports some DNLA functions and appears on some devices as a DNLA service, even though it is not a real DNLA service.  [http://wiki.gentoo.org/wiki/MediaTomb](http://wiki.gentoo.org/wiki/MediaTomb) and [http://mediatomb.cc/dokuwiki/faq:faq#dlna_tvs](http://mediatomb.cc/dokuwiki/faq:faq#dlna_tvs)

What version of mediatomb are you using?

Album art can either be in separate directories or embedded in the actual music file.  It's possible that thumbnail support is not automatically built-in:  [http://forum.xbmc.org/showthread.php?tid=99096](http://forum.xbmc.org/showthread.php?tid=99096)

> I remember I used both MiniDLNA and Mediatomb and I recall XBMC displaying thumbnails for both (though with Mediatomb you have to build thumbnail support from source via ffmpegthumnailer depending on the version installed).

---

### Post by iclestu on 2014-08-13
Hi there,

Thanks very much for taking the time to reply.

i am just using the version from the repos: 0.12.1

If MediaTomb isn't a DNLA server and doesn't support fastforward etc. is there an alternative you'd recommend? uShare? Rygel? (I just googled but haven't heard of either of them! ;-) )

I didn't install any separate programs for windows. It just works 'out of the box' when just sharing the libraries on Windows 8.1. I had to turn on network sharing (I forget the precise steps but was quite straightforward) & share the libraries but thereafter it just shows up on my TV as a DNLA server with my windows machine name.

---

