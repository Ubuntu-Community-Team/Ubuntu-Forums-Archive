---
title: "Opera and WMA/WMV"
date: 2005-09-14
forum: General Help
---

### Post by shyguy on 2005-09-14
Installed Opera as per the HOWTO. All plugins are working (Java, Realplayer, Flash, etc.) I have the proper codecs installed and working in Firefox but cannot seem to play .wma or .wmv in Opera.

Can someone please explain how to get this working. TIA.

shyguy   :smile:

---

### Post by evilghost on 2005-09-15
Make sure you have the Win32 codecs installed and then install Kaffeine.

```

sudo apt-get install kaffeine
sudo apt-get install kaffeine-mozilla
sudo apt-get install wget
sudo wget http://homepage.ntlworld.com/fowlerc/kaffeine_0.6-1_i386.deb
sudo dpkg -i kaffeine_0.6-1_i386.deb

```

Once installed go into Opera plugins and have it redetect them.

The kaffeine_0.6-1_i386.deb package downloaded from ntlworld.com is a fix to a known 100% CPU consumption bug when exiting Kaffeine.  I **highly** recommend it.

Anyway, I'm using Opera and this is the setup I use.  There are known issues getting mmplayer to work with Opera.

---

### Post by shyguy on 2005-09-17
That worked great.  :) 

Thanks alot.

---

### Post by evilghost on 2005-09-17
No problem, glad I could help :)

---

### Post by jonathanku on 2007-02-24
Installed this (after already having the Win32 codecs, but the video space just says Kaffeine Starter Plugin...

Then this error pops up...
> xine: cannot find input plugin for MRL [rtsp://rmgeo.bbc.net.uk/news/media_acl/mps/fix/news/video/80000/bb/80054_16x9_bb.rm?title="BBC"&author="BBC"&copyright="(C) British Broadcasting Corporation"]
xine: input plugin cannot open MRL [rtsp://rmgeo.bbc.net.uk/news/media_acl/mps/fix/news/video/80000/bb/80054_16x9_bb.rm?title="BBC"&author="BBC"&copyright="(C) British Broadcasting Corporation"]
xine: found input plugin : rtsp streaming input plugin

Any thoughts on how to fix this?

---

