---
title: "cups bad request line"
date: 2007-03-30
forum: General Help
---

### Post by UltraMathMan on 2007-03-30
I finally got rid of the encryption error I was getting by compiling openssl and cups 1.2.10 (see [here]("http://www.ubuntuforums.org/showthread.php?t=376945")). Now I'm getting

D [29/Mar/2007:20:49:38 -0400] cupsdAcceptClient: 12 from 192.222.19.178:515 (IPv4)
E [29/Mar/2007:20:49:38 -0400] Bad request line "Schachter" from 192.222.19.178!
D [29/Mar/2007:20:49:38 -0400] cupsdSendError: 12 code=400 (Bad Request)
D [29/Mar/2007:20:49:38 -0400] cupsdCloseClient: 12

when I try to print from my OS X client (to lpd://server/queue) my Ubuntu Linux 6.10 server (I can print from the server). I also have xinetd running cups-lpd. My cupsd.conf is attached below.

Any ideas as to what's causing this and/or what I can do to fix it?

Thanks!

---

### Post by UltraMathMan on 2007-04-13
FINALLY RESOLVED! 

So I finally got everything working - will write everything up and post as a HOWTO when I get back to my computer. \\:D/

---

### Post by UltraMathMan on 2007-05-17
The HOWTO is done and available [in this thread]("http://ubuntuforums.org/showthread.php?p=2674183#post2674183").

---

