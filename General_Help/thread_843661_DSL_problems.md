---
title: "DSL problems"
date: 2008-06-28
forum: General Help
---

### Post by Tangstah on 2008-06-28
My DSL connects to my XP computer fine, but I need it to work on my Hardy Heron Ubuntu computer.
I don't have a router.
I use the terminal and type in: sudo pppoeconf
that connects me to the internet fine- I enter my user name and pw but I open firefox and I'm directed to the AT&T help site that eventually tells me my modem isn't configured properly.  They give me steps to configure it: [http://192.168.0.1](http://192.168.0.1)
That doesn't work because the moment I open another window and put that link in, it circles me back to the AT&T help site.
Yes, I turned the modem off and unplugged/replugged everything. No luck.
Help!  and thank you.

---

### Post by fragos on 2008-06-28
Since you gave us a "local" IP address you must be behind a router. The router may be built into your modem. Does it have multiple RJ45 Ethernet jacks?

---

### Post by Miljet on 2008-06-28
> **fragos said:**
> Since you gave us a "local" IP address you must be behind a router. The router may be built into your modem. Does it have multiple RJ45 Ethernet jacks?

192.168.0.1 is the IP address for the modem to enter setup mode. I have the exact same modem.

---

### Post by CEB2nd on 2008-06-28
Open terminal and enter /sbin/ifconfig
Post the results.

---

### Post by fragos on 2008-06-28
How are both PC's cabled to the DSL modem?

---

