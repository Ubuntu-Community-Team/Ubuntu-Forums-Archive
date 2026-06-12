---
title: "Tracker: [Couldn't connect to server]"
date: 2008-05-01
forum: General Help
---

### Post by Craxx on 2008-05-01
Hy,

i installed rTorrent 0.8.1.
But i have a problem. Hope somebody can help me.
On the first view everything works great (also with wtorrent). But every torrent i load i get this error message:
Tracker: [Couldn't connect to server]
All necessary ports are open.
...???
Please give me a little tip:)))

best regards
Craxx;)

---

### Post by tamoneya on 2008-05-01
if you are getting all the torrents from the same site they may all be using the same tracker and that tracker may be down.  Try downloading one of the ubuntu torrents.  I am currently seeding them and I can confirm that the tracker is up.  Sometimes it also helps if you give it a minute or two.  Torrents do not run at full speed immediately.

[http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-i386.iso.torrent)

---

### Post by Craxx on 2008-05-01
Hy tamoneya,

thx for answer. But your torrent has the same message...
There must be something wrong...???

best regards
Craxx;)

---

### Post by tamoneya on 2008-05-01
who is your ISP.  It could be something on their end where they are dropping your packets and preventing you from connecting with the server.

---

### Post by Craxx on 2008-05-02
I solved the problem !!

It was a missing "/" in .rtorrent.rc

THX and best regards
Craxx;)

---

### Post by Xubuntnoob on 2009-08-22
> **tamoneya said:**
> who is your ISP.  It could be something on their end where they are dropping your packets and preventing you from connecting with the server.

my ISP is "Charter -we spy on you- Communications".

How can I find out if this is the case? Is there a way to fix this if it is the case?

rtorrent is working fine, but I get Tracker: [Couldn't connect to server] errors. It's not all the time, but every 15 - 20 seconds or so it says it, and goes away. 

Is this something I should even worry about if my torrents all fully download?

---

