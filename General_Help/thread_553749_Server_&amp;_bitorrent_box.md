---
title: "Server &amp; bitorrent box"
date: 2007-09-18
forum: General Help
---

### Post by MJSOnline on 2007-09-18
Hi all. I need to know if it s possible to install Ubuntu 6.06 LTS LAMP server edition or 7.04, and have the same box download torrents using torrentflux?

The specs are:
Dell Optiplex GX1 500MHz, 256ram, 6.4 & 10.2 GB hard drives and CD-Rom.

I want to access the box remotly for my own web pages, pictures, music etc.

Also linking the pictures, music to a mysql database as well as using the box to download from bittorrent to the 2nd hard drive (10.2GB)

How can this be done?

I have looked on the net for howto's but can't seem to find a howto to suit my needs.

Any help or a howto would be great. Thanks

---

### Post by tisse on 2007-09-18
I have a LAMP server as well, running 7.04 and I also use it to download bittorrent-files. But I use MLdonkey-server instead of torrentflux and it works great. To control MLdonkey I login to its webserver (that uses another port than 80) or I use MLdonkey-gui. I have never tried torrentflux but hope this info helps a bit.

---

### Post by MJSOnline on 2007-09-18
Is that the server version of 7.04? Thats good to know.  Any tips?  I will try MLDonkey this evening.Thanks.

---

### Post by tisse on 2007-09-23
Yes, the server is running 7.04. I've no special tips, I installed everything from packages and I don't use any gui, only html-access on default port (which is locked by my router so I can't access it from the outside). The only thing I changed from default is the save locations, otherwise the files will end up somewhere in your home-area.

---

