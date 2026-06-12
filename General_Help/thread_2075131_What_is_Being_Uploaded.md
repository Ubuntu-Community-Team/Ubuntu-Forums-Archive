---
title: "What is Being Uploaded?"
date: 2012-10-23
forum: General Help
---

### Post by Quarkrad on 2012-10-23
Newbie running 12.04.  I've recently installed Conkyon my Desktop and interested to note that the Download and Upload network numbers seem to constantly changing.  It intrigues me, if Conky is actually picking up real traffic going out from my PC, what is it and where it is going.  Is it possible for me to find out what this data is and where it is going?

---

### Post by SlugSlug on 2012-10-23
There will always be some network traffic on an idle machine but this should be only a few B/s.

I use iftop quite a lot to see whats connected where its very simple to look at.

nethogs is another very simple tool.

For a bit more in-depth look then iptraf or wireshark would be needed.

---

### Post by 3rdalbum on 2012-10-23
In some instances, routers or network cards can be quite "chatty" and continually send or receive meaningless data. The good news is that this isn't going onto the internet, only travelling on your local network, and it's probably around 500 bytes per second.

Take a look in System Monitor. Ignore the graph and just look at the numbers of how much is being transmitted per second. If it's a small number, and it still gets transmitted when your modem is unplugged from the phone line, then it's not anything malicious and not worth worrying about.

From your description it seems like the kind of innocent chatty traffic I've seen before. Anything malicious will either push through large amounts of data or transmit infrequently to avoid suspicion.

---

