---
title: "apache2 only answers IPv6?"
date: 2007-03-19
forum: General Help
---

### Post by qhartman on 2007-03-19
I have a Dapper installation that I have pared down to be fairly minimal for a pseudo-embedded envirnoment. For part of this project I will be running Apache2 to server a variety of web content. When I initially installed it and tried to connect to it, I got enough of the page that my browser showed me the page title, but failed to actually render anything. All of the log files for Apache showed normal behavior, and connecting from the local machine works fine. While troubleshooting this I discovered that apache (and everything else) was only listening on tcp6 addresses, not "normal" tcp. So, I disabled ipv6 by blacklisting the kernel module for it, and now apache is working fine. However, this raises some questions for me:

-What could have caused this behavior in the first place?
-What would the "right" way to get around it be?
-If it's only listending on ipv6, why could I get a page title?
-ssh also indicated that it was listening only in a tcp6 port, but it worked fine on ipv4 network. How can that be?

Thanks for any insight you can provide. fwiw, various prayers to google have gone unanaswered...

---

### Post by nautilus on 2007-04-15
the linux kernel has support for ipv6-mapped ipv4 addresses.

in other words, a server application (such as apache) need only bind to the ipv6 address "::" (or "any") and inherintly support both protocols.

incoming connections via ipv4 are received as ::192.168.0.44 (or whathaveyou) and are transferred as usual without any special work being done by the kernel, the server, or the client.

in your circumstance i can't justify why it worked over ipv4 but not over ipv6-mapped ipv4, since it doesn't even touch the ipv6 routing tables at all.

heck, it barely grazes the ipv6 module.

as for your key points:

1) i would poke through apache.  if it's the latest apache2, i'm shocked if it's a bug.
2) never disable ipv6.  it's the standard internet protocol, you're going to need that soon.
3) explained above
4) also explained above

---

