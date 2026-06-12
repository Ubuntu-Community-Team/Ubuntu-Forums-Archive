---
title: "I Need Some Port Forwarding Help"
date: 2013-02-23
forum: General Help
---

### Post by jnLink on 2013-02-23
I have a local host working great at 190.168.1.69. I need my IP address to forward it to this local host using forwarding correct? My router uses this interface -  [IMG]http://www.weebly.com/uploads/1/7/6/3/17638123/untitled.png[/IMG]
What do I need to fill in for it to forward everything to my local host? Please Help!

---

### Post by carl4926 on 2013-02-23
Can we just clarify..
Is 190.168.1.69 the LAN IP address assigned to the machine you want to forward to?

What service do you want to forward
And what port number/s

---

### Post by jnLink on 2013-02-23
Yes, 190.168.1.69 is what I wish for it to forward to.

---

### Post by carl4926 on 2013-02-23
It looks a bit like a netgear router.

There is a default list of services in the section:
Firewall Rules
But if the default port is not what you want you need to add a custom service
[http://paste.opensuse.org/65288080](http://paste.opensuse.org/65288080)

Then in Port forwarding
[http://paste.opensuse.org/89511845](http://paste.opensuse.org/89511845)

---

### Post by jnLink on 2013-02-23
I don't understand. I'm more of a programmer. I'm a bit new to this. I have no Firewall option in my sidebar. Did I set something up wrong?
 
Box - WRN1000v2

---

### Post by carl4926 on 2013-02-23
Maybe your router doesn't have a firewall built in.

So just add the service in the PF section.

There is a site offering dedicated guides on this subject
[http://portforward.com/english/routers/port_forwarding/Netgear/WNR1000v2/Links.htm](http://portforward.com/english/routers/port_forwarding/Netgear/WNR1000v2/Links.htm)

---

### Post by jnLink on 2013-02-23
It says I need to forward 3 different ports? Can you explain sir?

---

### Post by jnLink on 2013-02-23
I tried all 3 ports they sugegsted, none of them worked. Could it possibly be my router?

---

### Post by carl4926 on 2013-02-23
> **jnLink said:**
> It says I need to forward 3 different ports? Can you explain sir?

No
How can I possibly.

I wouldn't accept any auto config suggestions

Set it up manually. But you need to know a little bit about what you are doing.

ie: The application and which port/s
 
I did ask you earlier, what application and port.....

---

