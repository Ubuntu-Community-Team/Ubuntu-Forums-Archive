---
title: "Internet Access"
date: 2007-12-13
forum: General Help
---

### Post by coolslaw on 2007-12-13
I am having trouble accessing the internet on my Ubuntu machine.  The last time I turned it on (about 2 months ago) it worked fine.  Nothing should have changed externally.  I tried deactivating and reactivating the ehternet connection.  Since I haven't used it in so long, there are probably some updates I need to install, but without internet access I don't know how to get them to install them.  If that's the problem, then I'm stuck in a catch 22.  Any ideas?

---

### Post by Pumalite on 2007-12-13
Post:
ip addr

---

### Post by coolslaw on 2007-12-13
How do I find my ip address?

---

### Post by Pumalite on 2007-12-13
Type:
ip addr
In your Applications>Accessories>Terminal

---

### Post by coolslaw on 2007-12-13
Ok,, here's what I get:

...
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
     link/either 00:a0:cc:d3:dc:dd brd ff:ff:ff:ff:ff:ff
     inet8 fe80::2a0:ccff:fed3:dccc/64 scope link 
          valid_lft forever perferred_lft forever
3: sit0: <NOARP> mtu 1480 qdisc noop
     link/sit 0.0.0.0 brd 0.0.0.0

I didn't retype the first part, I hope that wasn't the important stuff.

---

