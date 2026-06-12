---
title: "Best Torrent Client?"
date: 2007-02-16
forum: General Help
---

### Post by CocoAUS on 2007-02-16
I use Gnome, so I'd rather not install KTorrent, and Azureus (as always) has NAT problems and eats WAY too much memory.  What's the best non-KTorrent and non-Azureus client for me to use?

---

### Post by gwk on 2007-02-16
I don't have an answer, but I would be very interested in hearing people's thoughts on this.  Azureus is a great client except for the crazy memory usage.  uTorrent - Windows only unfortunately - has been the best one I've ever found.  Great features and super low memory usage.  A Linux client similar to uTorrent would be awesome.

---

### Post by true_friend on 2007-02-16
Then install bit torrent official torrent client.

---

### Post by Frostmourne on 2007-02-16
Try [Deluge]("http://deluge-torrent.org/"). It uses GTK.

---

### Post by CocoAUS on 2007-02-16
Ah, thanks!  Deluge looks great, and from what I can tell, it's pretty full-featured.  Will give it a shot, perhaps report back here with my findings.

---

### Post by pissedoffdude on 2007-02-16
> **gwk said:**
> I don't have an answer, but I would be very interested in hearing people's thoughts on this.  Azureus is a great client except for the crazy memory usage.  uTorrent - Windows only unfortunately - has been the best one I've ever found.  Great features and super low memory usage.  A Linux client similar to uTorrent would be awesome.

utorrent runs flawlessly under wine

---

### Post by kircher on 2007-02-16
> **pissedoffdude said:**
> utorrent runs flawlessly under wine

I run utorrent under wine, but in my experience it's not flawless. If I minimise it, and maximise again it doesn't display. I have to reopen it with the utorrent icon in the toolbar. That's my experience. It doesn't stop me using it though. Here are some pics attached for what I mean by it not drawing the application properly after minimising it. It works though, and I prefer it to azureus. I shall try deluge.

---

### Post by Arup on 2007-02-16
Deluge is good, wish it had IP filering like K Torrent but K Torrent doen't run good under Gnome sadly, same for Kopete.

---

### Post by kircher on 2007-02-17
I do like deluge a lot. I just installed it from the .deb, and I already like it. Azureus was way too complicated and clumsy. I like a simple easy to use interface. I won't be needing utorrent any more.

---

### Post by TheDigitalNinja on 2007-02-17
Wow thanks guys. Iv been trying to get a good bit torrent client for a while for linux. Bit tornado and azerus were all giving me problems. Deluge rocks! im actually seeing all the peers now.

---

### Post by CocoAUS on 2007-02-17
I've been running Deluge for about a day now, and while it definitely needs some work, it's already one of my favorite clients.  The interface is (IMHO) better than Azureus', and it's got really solid functionality.

Solid app for anyone looking for a good Gnome client.

---

### Post by maddog39 on 2007-02-17
I personally prefer Dluge over the others on GNOME. For KDE, I'd prolly choose KTorrent.

---

### Post by olavjunior on 2007-02-18
Ok: Anybody else having problems installing this deluge???

First I get the message I needed a lib-something-package, and when I tried to install that one after some googling, I got an error that I needed some boost date-time-library. And when I tried to install that one, I realized that this turned into waay to much work for one stupid torrent-client!

Is it really that difficult??

---

### Post by jake3988 on 2007-02-18
I like rtorrent because its an interactive console-only torrent client.  Therefore it doesn't suck up memory like azureus and its interactive (that is, you can launch it into your console like cmus or lynx and browse around the interface using your keyboard and not just issuing a verbose line like mplayer)

Azureus doesn't have a nat problem if you switch your port.  and then port forward.  I port forwarded something like 45536 on my router then used that port in azureus and got great speeds.

But yeah, the memory usage made firefox seem like a console program.  It was outrageous.  So that's why I switched to rtorrent.

---

### Post by kircher on 2007-02-18
> **olavjunior said:**
> Ok: Anybody else having problems installing this deluge???

First I get the message I needed a lib-something-package, and when I tried to install that one after some googling, I got an error that I needed some boost date-time-library. And when I tried to install that one, I realized that this turned into waay to much work for one stupid torrent-client!

Is it really that difficult??

Go to [http://packages.debian.org/unstable/net/deluge-torrent](http://packages.debian.org/unstable/net/deluge-torrent) and download the right .deb for your system. When I installed from the deb it mentioned that some dependencies weren't met, but it listed the dependencies, and they were all available in the repositories, so after installing the dependencies I installed it.

---

