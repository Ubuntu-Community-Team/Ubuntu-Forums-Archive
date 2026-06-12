---
title: "ufw, gufw don't seem to actually open a port.  Newbie puzzled."
date: 2013-04-27
forum: General Help
---

### Post by CaptainBob on 2013-04-27
I have a nice brand new just built Ubuntu remote server,  v12.10 (32 bit), which I'm trying to configure.
I need to have port 9933 open on it bidirectionally,   to use a third-party app (SmartFoxServer2x).

So, trying to follow what instructions I can find,  I got the package "gufw" and ran it and did the obvious things.
I opened all the standard ports, and also port 9933.  When I look at the list of rules,  there is port 9933, for both inbound and outbound.
I've rebooted the server, and confirmed that the gufw firewall still reports it self as "on". 

But,  I can't get to port 9933.

If I probe it, from another computer over the web, using, say "telnet <ip-address> 9933", it reports that it cannot connect to that port.
If I try port 8080 instead, say,  it connects just fine.   So I think I'm typing the right test command.

So, as a newbie, I'm lost.  What ELSE do I need to do?   Why doesn't putting the port into the rules in gufw result in the port being open?

Pointers to text I should have read, or videos I should have watched would be appreciated.[IMG]http://www.flickr.com/photos/94655089@N03/8685643839/in/photostream[/IMG]

Image of what gufw looks like: [http://www.flickr.com/photos/94655089@N03/8685643839/in/photostream](http://www.flickr.com/photos/94655089@N03/8685643839/in/photostream)

---

### Post by dino99 on 2013-04-27
wont you have some other places to set those ports, like router ...
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[http://www.ubuntugeek.com/how-to-manage-range-of-ports-in-ufw.html](http://www.ubuntugeek.com/how-to-manage-range-of-ports-in-ufw.html)

---

