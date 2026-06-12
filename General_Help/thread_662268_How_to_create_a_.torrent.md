---
title: "How to create a .torrent?"
date: 2008-01-08
forum: General Help
---

### Post by foug on 2008-01-08
I downloaded "createtorrent" but it will not install. ./configure gives me an error saying the "compiler cannot create executables, see config.log for more details" Is there any good program I can download through apt-get that'll allow me to create a .torrent?

---

### Post by PinkFloyd102489 on 2008-01-08
rTorrent has the ability to make torrents as well as being a CLI torrent program.

---

### Post by foug on 2008-01-08
Hmm, cool, but does it have a GUI?

---

### Post by Lostincyberspace on 2008-01-08
deluge has a torrent creator I haven't used it but every thing else in it is nice.

---

### Post by ChadMMc on 2008-01-08
KTorrent also has a torrent creation facility built into it.

---

### Post by foug on 2008-01-08
just figured out how to make them with bittornado. The simple command "btmaketorrentgui" works

---

### Post by vishzilla on 2008-01-08
Deluge has a torrent creator, you have to enable the plugin. Download it from [http://deluge-torrent.org](http://deluge-torrent.org)

---

### Post by oldos2er on 2008-01-08
> **foug said:**
> I downloaded "createtorrent" but it will not install. ./configure gives me an error saying the "compiler cannot create executables, see config.log for more details" Is there any good program I can download through apt-get that'll allow me to create a .torrent?

 Run "sudo aptitude install build-essential" in a terminal.

---

### Post by bodhi.zazen on 2008-01-09
> **PinkFloyd102489 said:**
> rTorrent has the ability to make torrents as well as being a CLI torrent program.

Alas, no it can not :

> Ticket #656 (closed enhancement: wontfix)

 Description

You should add a simple program for creating torrent files as now i have to use an other client. I mean nothing special just a console based thing which gets the torrent name, tracker and the directory or file and creates the .torrent from it.

I think it's not much work for you, but very useful function for us. Thanks in advance! 

Reply :

11/14/06 17:24:37 changed by rakshasa

    * status changed from new to closed.
    * resolution set to wontfix.

Other people have made stand-alone programs for this, no need for me to spend time on that.

[http://libtorrent.rakshasa.no/ticket/656](http://libtorrent.rakshasa.no/ticket/656)

---

