---
title: "Problems with Bittorrent clients... all of them (no, seriously)"
date: 2007-07-29
forum: General Help
---

### Post by Not So Smart Guy on 2007-07-29
In the hail mary of a kick to the balls, Deluge, Azureus, and Bittornado have all decided that approixmately two or three minutes after I start downloading a file, they will cause the entire system to freeze. Now in most cases I wouldn't make a statement like "all bittorrent clients aren't working" but the three I've tried thus far all fail the exact same way in almost the exact same manner. Beyond that, however, it seems I have very little to go on. 

Anybody else ever had this problem? Any help? 

Thanks.

---

### Post by raul_ on 2007-07-29
I really don't know any fix, but try using uTorrent with Wine. If it works, there must something wrong with your libtorrent

---

### Post by Not So Smart Guy on 2007-07-29
I've never actually used wine, and while that would be one solution, I would like to get one of these torrent clients to run as they should normally.

---

### Post by AlexThomson_NZ on 2007-07-30
I'd be pretty surprised if Azeurus caused the whole system to freeze, as that would be a pretty serious bug with the jave JRE.   And I don't think Azeurus uses libtorrent either, so I can't really see any connection between the three apps mentioned.

How hard does the system crash (can you Ctrl+Alt+F1 to a console screen?)

Is this repeatable every time, and do any other applications behave like this?  Deluge is a fairly simple GTK app, not doing anything tricky using just normal Gnome widgets, so I suspect something else is going on.

Try running from the console to see if it spits out any errors...

---

### Post by raul_ on 2007-07-30
It wasn't a solution, it was more of a debugging method. If uTorrent runs fine, the problem is in your libs possibly. 

You can't debug from the terminal if your system freezes

---

### Post by AlexThomson_NZ on 2007-07-30
> **raul_ said:**
> You can't debug from the terminal if your system freezes

But obviously you want to see if there's any errors or warnings, right?

I think we can discount the libs, as Azeurus doesn't use it, and besides that is run in a container (like uTorrent in Wine).

I would love to know how repeatable this is...

Other options (equally unlikely): broken network hardware (unlikely if you can browse HTTP), broken network card driver (unlikely, again especially if you can access port 80- but maybe dies on a buffer overrun or something streaming torrents), broken firewall (pretty small chance of that).

Can you telnet to the tracker on port 6969 without it freezing?

Can you recover with the magic sys req key? ([http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key))

---

### Post by raul_ on 2007-07-30
Indeed. What you can do is start from the terminal and pipe the output to a log file like this:

azureus > log.txt

(i think it works)

This way, if the programs prints something right before the system freezes, it will be stored in the file

---

### Post by keithacole on 2007-08-01
ok, i have the same issue, Miro(democracyplayer) stopped downloading my torrents, then i tried freedownloader and nothing, my miro log told me that i can not connect to the tracker.

ive reinstalled everything that came up with "torrent" as a search term in synaptic, ive restarted the system, ive reinstalled miro, ive built  miro from source.

ubuntu studio
7.04 fiesty 
REALTIME kernel
kde library
gnome as main window manager with compiz-fusion(if that even matters)

im using comcast for ISP(how would i see if its my ISP, even though i can get to torrent sites?)

edit:

synaptic showed i never had libtorrent9 installed. but my torrents worked fine

---

### Post by keithacole on 2007-08-02
ok, ive tried

bittornado client
bittorrent
freeloader
ktorrent

each one of them tell me that they cannot connect to the tracker

here is some info

keith@keith-desktop:~$ ip route
192.168.0.0/24 dev ath0  proto kernel  scope link  src 192.168.0.100 *i #my wifi*
169.254.0.0/16 dev eth1  proto kernel  scope link  src 169.254.4.175  *#onboard lan not plugged in, but has an IP. hmm why does it have an IP*
169.254.0.0/16 dev eth0  proto kernel  scope link  src 169.254.4.170  *#onboard lan not plugged in, but has an IP. hmm why does it have an IP*
169.254.0.0/16 dev ath0  scope link  metric 1000 *#dont know what this means* 
default via 192.168.0.2 dev ath0 
default dev eth1  scope link  metric 1000 *#explain this to me someone?*


EDIT:
uTorrent via wine.. works!, now i know its DEF this os

---

### Post by Hr7376 on 2008-03-05
:( i have the exact same problem , im running ubuntu studio 7.10 and after starting a download with any torrent manager , give 10 - 25 min and the whole system is frozen had to power off.  I have an atheros wireless card in my laptop and am using ndiswrapper.

---

