---
title: "Is LAMP Safe on my Local Development Computer"
date: 2015-11-27
forum: General Help
---

### Post by mpskinner on 2015-11-27
Hi

I have a computer where I am developing and testing my code.

I have LAMP installed and running..

How safe is my computer from external internet attack?

Should I turn Apache off when I am not developing?

Thank  you...

I remember when using WAMP there was an off line / online option. Is there a similar option with LAMP?

Also how can I make it so Apache is off by default?

Thank You.

---

### Post by TheFu on 2015-11-27
If apache only listens on "localhost", then no, there isn't any security worries related to it.  Also, just follow nominal system security techniques and use a firewall to prevent unwanted connections for all ports.

There are a few basic security guides for ubuntu. Follow those.

---

### Post by mpskinner on 2015-11-27
I just installed ubuntu (studio) what firewall would you recommend..

thank you..

---

### Post by TheFu on 2015-11-27
My profile here under "visitor messages" has many links for this stuff.
There is really only 1 firewall on Linux. Every program that you might pick is just an interface to it.

I use iptables, but someone new would probably want either ufw or gufw.

BTW - be certain to change the apache config to only listen on localhost if that is your desire.

---

### Post by mpskinner on 2015-11-27
> My profile here under "visitor messages" has many links for this stuff.

Very impressive.. thank you

---

