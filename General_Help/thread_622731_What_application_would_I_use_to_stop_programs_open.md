---
title: "What application would I use to stop programs opening webpages?"
date: 2007-11-25
forum: General Help
---

### Post by Game_boy on 2007-11-25
I'm running a random freeware Windows application with Wine on Ubuntu 7.10 (Gutsy Gibbon), and every time the application closes it opens a Firefox window and loads the creator's website.

Being closed-source, I cannot modify the program to stop this behaviour, so is there any commands or applications (AppArmor?) I can use to do it? Can I have simple instructions on how to do so?

Thanks.

---

### Post by Cannaregio on 2007-11-25
Blacklist on host, either through wine for your windoze appz or directly in GNU/Linux

```
man host
```

---

### Post by Game_boy on 2007-11-25
1. Will that stop it from opening Firefox? It looks like it will bring up a blank page.

2. How do I blacklist it if the filename is "generic.exe"? That man page isn't helping.

---

### Post by Cannaregio on 2007-11-25
Check DNS filtering and blacklisting through google

use 

```
dig
```

and

```
nslookup
```
as well.
Search and study dns blacklisting.

Basically, though, you'll do something like this:
```
host -t txt 2.0.0.127.your_target_http_address
```

I suggest you have a look at
[http://www.homepage.montana.edu/~unixuser/051905/abs-guide/communications.html]("http://www.homepage.montana.edu/~unixuser/051905/abs-guide/communications.html")

and

[http://www.unix.org.ua/orelly/networking_2ndEd/dns/ch12_01.htm]("http://www.unix.org.ua/orelly/networking_2ndEd/dns/ch12_01.htm")

The real phun in GNU/Linux is that you never finish studying :-)

---

