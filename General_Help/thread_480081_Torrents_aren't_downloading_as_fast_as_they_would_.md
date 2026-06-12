---
title: "Torrents aren't downloading as fast as they would on XP"
date: 2007-06-21
forum: General Help
---

### Post by Tekee on 2007-06-21
Just to test the BitTorrent app already installed on Ubuntu, I went to a site I visit often and attempted to torrent a 170 mb video (legal, mind you). 

I used to use the BitLord program on Windows and the files would be done relatively quickly - within 30 - 45 minutes.
 
Right now however, I've been stuck at 0% at .0X%
I'm not sure how going to a new OS would change how I torrent something, but is this a common problem?

---

### Post by Motoxrdude on 2007-06-21
Did you forward the port bitlord uses?

---

### Post by fdrake on 2007-06-21
try freeloader
sudo apt-get install freeloader

---

### Post by Tekee on 2007-06-21
> **Motoxrdude said:**
> Did you forward the port bitlord uses?

Nope, how would I do that?

---

### Post by jackmc on 2007-06-21
> **Tekee said:**
> Nope, how would I do that?

Probably in modem/router settings - try typing 192.168.1.1 into firefox/any browser. I know this is assuming a lot (this address varies between manufacturers). Otherwise, if you know how, access your modem/router, assign yourself a static IP, then enable port forwarding on your bittorrent port. 

If your router is on [http://portforward.com/](http://portforward.com/), there are instructions there to help you set it up.

Sorry I cant be more helpful, I'm fairly new myself :)

---

