---
title: "Wireless on startup"
date: 2008-04-23
forum: General Help
---

### Post by upthelum on 2008-04-23
Tried posting this in Networking but no reponse. I managed to get wireless working on my latitude using a how to in here so consider myself fortunate. The thing is, when i boot i have to start wlassistant to connect to a network access point, even at home if i power down or restart i have to do this every time. It's not annoying but is there a way to get the hardware/software to start scanning and connect automatically on startup?
This would be really helpful and thanks for any help.

---

### Post by upthelum on 2008-04-23
Infamous bump...

---

### Post by Uruz on 2008-04-23
I too shall bump this thread.

Such a thing would be useful to me as well.

---

### Post by upthelum on 2008-04-23
> **Uruz said:**
> I too shall bump this thread.

Such a thing would be useful to me as well.

So you have the same issue? (bump)

---

### Post by Miljet on 2008-04-23
What worked for me was to edit a file called /etc/network/interfaces.

There should only be two lines in it:

auto lo
iface lo inet loopback

Delete anything else, save the file and reboot.

---

### Post by upthelum on 2008-04-23
> **Miljet said:**
> What worked for me was to edit a file called /etc/network/interfaces.

There should only be two lines in it:

auto lo
iface lo inet loopback

Delete anything else, save the file and reboot.

I have 9 other entries.

---

### Post by Miljet on 2008-04-23
There was an excellent post here before titled "Solution to Many Wireless Problems." It was posted by gilf. It should be in the archives somewhere.

---

### Post by upthelum on 2008-04-23
Didn't work so just restored file to original and keep trying.

---

### Post by Miljet on 2008-04-23
Maybe someone else will jump in here. I've about exhausted my meager knowledge.

---

### Post by ryanhaigh on 2008-04-24
You could try deactivating roaming mode in system>admin>network which should create the required info in /etc/network/interfaces

---

### Post by upthelum on 2008-04-24
> **ryanhaigh said:**
> You could try deactivating roaming mode in system>admin>network which should create the required info in /etc/network/interfaces

Yes it's already disabled.

---

### Post by upthelum on 2008-04-24
I get the feeling it's one of these things we just have to do. I didn't expect to get wireless working at all so having it connect on startup may be wishful thinking but it would certainly make for a much happier bunny.

---

