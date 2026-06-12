---
title: "Torrent Software for internal network and external"
date: 2008-01-27
forum: General Help
---

### Post by GodsDead on 2008-01-27
hey all, i ahve used Utorrent for windows, and use it still, i have a small home server with ubuntu installed, and was wondering whats the best programme and best method of being able to manage torrent downloads useing this machine via my internal network, and also with a web gui, say if im out somewhere, and want to que something up for download =]

This would be ausom =]

does anybody have a good solution?

---

### Post by mali2297 on 2008-01-27
[rTorrent]("http://libtorrent.rakshasa.no/"), see especially the [list of frontends]("http://libtorrent.rakshasa.no/wiki/UtilsList").

---

### Post by GodsDead on 2008-01-28
oh right, cheers, where is the best install guide for this.. since that i have no experiance compileling or building code on ubutu..

---

### Post by mali2297 on 2008-01-28
> **GodsDead said:**
> oh right, cheers, where is the best install guide for this.. since that i have no experiance compileling or building code on ubutu..

It is in the universe respository, enable it if you haven't already. See
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Then just type
```

sudo apt-get install rtorrent

```

You might also be interested in these howtos:
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)
[http://polishlinux.org/apps/p2p/rtorrent-console-p2p/](http://polishlinux.org/apps/p2p/rtorrent-console-p2p/)

---

### Post by Cadmus on 2008-01-28
I've not tried rtorrent, but myself and a few others use uTorrent through wine (a program that lets you run some windows programs in ubuntu).

---

### Post by nemilar on 2008-01-28
Deluge is pretty nice.  Has a web plugin, too.

---

### Post by PinkFloyd102489 on 2008-01-28
TorrentFlux is the best. It sets up as a subdir of your website, ie mysite.com/torrentflux. I use it on a daily basis and it's simple to install and use.


```

sudo apt-get install torrentflux

```

Continues torrenting even when you exit out of the web GUI, unlike rtorrent which is command line based.

---

### Post by freymann on 2008-01-28
> **PinkFloyd102489 said:**
> TorrentFlux is the best. It sets up as a subdir of your website, ie mysite.com/torrentflux. I use it on a daily basis and it's simple to install and use.

 I had tried TorrentFlux and I very much liked the concept... but none of the search engine results download anything! It just complains download.asp didn't find anything, maybe it's a bad link. The PirateBay search engine errors out completely with a syntax error.

 TorrentFlux does work if I manually save the *.torrent file somewhere, then upload it into torrentflux, but that seems to defeat the purpose of having all the embedded search engine stuff readily available...

---

### Post by SOULRiDER on 2008-01-28
> **PinkFloyd102489 said:**
> TorrentFlux is the best. It sets up as a subdir of your website, ie mysite.com/torrentflux. I use it on a daily basis and it's simple to install and use.

```

sudo apt-get install torrentflux

```

Continues torrenting even when you exit out of the web GUI, unlike rtorrent which is command line based.

Theres a nice tutorial on the Tutorials forums on how to set it up.

---

