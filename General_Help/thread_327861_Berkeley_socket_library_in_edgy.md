---
title: "Berkeley socket library in edgy?"
date: 2006-12-29
forum: General Help
---

### Post by KingAlbrecht on 2006-12-29
Hi, I'm a new Ubuntu user (new to linux as well; I've used solaris but I've never had to set any of the systems up before) and I'm trying to compile some software I wrote but I can't seem to figure out what package I need to install to get access to the berekely socket library;

ie when I compile I get an error message like this:

/usr/bin/ld: cannot find -lsocket

The command I'm using to compile is:
g++ -g -Wall        client.o -o client -L. -lnsl -lsocket -lrpc -lpthread

Any help would be appreciated

-Mike

---

### Post by dothedorky on 2006-12-29
edgy ft is still in the works, and there are lots of little different quirks about the system.

Can't really help you on this one, but applaud you nonetheless for trying out Edgy with little Linux experience :KS 

Might i recommend 6.06 LTS?

---

### Post by KingAlbrecht on 2006-12-30
I found the problem.  It's not actually an issue with ubuntu, more an issue with the developer trying to go from solaris->linux :confused: . 

Thanks to my trusty friend google, I learned that the socket functions are integrated into libc on linux.  You don't need to link an external library to use sockets under linux.

Series of messages posts here that I missed the first time with google:
[http://gcc.gnu.org/ml/gcc-help/2001-04/msg00190.html]("http://gcc.gnu.org/ml/gcc-help/2001-04/msg00190.html")
And see section 0 here:
[http://www.hackcanada.com/ice3/2600/2600_16-1_p15.txt]("http://www.hackcanada.com/ice3/2600/2600_16-1_p15.txt")

Now I just need to find out where the ltostr function is defined on linux...
Update: Found what I needed again, ltostr isn't part of the c-standard so linux doesn't have it :(
[http://www.groupsrv.com/linux/ntopic24262.html]("http://www.groupsrv.com/linux/ntopic24262.html")
Thanks for your help!

-Mike

---

