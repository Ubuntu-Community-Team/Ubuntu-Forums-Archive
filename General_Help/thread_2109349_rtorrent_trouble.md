---
title: "rtorrent trouble"
date: 2013-01-27
forum: General Help
---

### Post by whalex on 2013-01-27
I'm sorry if i've put this thread into wrong place, i'm new here):P


I've used rtorrent for a while, and i really got used to it. But now i have trouble running it, in fact - i can't.
here's what i get:
> whalex@whalex-VAIO:~/Downloads$ rtorrent 
rtorrent: Could not open/bind port for listening: Address family not supported by protocol

There is no difference when i use .rtorrent.rc or not.

I can't remember when exactly this started to happen. Please help

---

### Post by oldos2er on 2013-01-27
Moved to General Help.

---

### Post by andrew.46 on 2013-02-13
Some googling suggests that this is a bug fixed in rtorrent > 0.8.7, which version are you running? You can see this by running:

```

andrew@skamandros~$**[COLOR="Red"] rtorrent -h | head -n 1[/COLOR]**
Rakshasa's BitTorrent client version 0.9.2.

```

Hopefully you are running an old version and an upgrade will solve the issue :).

---

