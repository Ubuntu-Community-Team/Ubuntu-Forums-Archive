---
title: "Kernel Types"
date: 2007-12-17
forum: General Help
---

### Post by Lagos on 2007-12-17
Can someone tell me the basic benefits and draw backs to these different kernel types. 

Generic
Server 
RT

I understand that one is meant for server use and one is "real time", but how does this actually affect the way things work?

---

### Post by AlexThomson_NZ on 2007-12-17
I'm not sure off-hand about the 'server' kernel- probably organises scheduling a bit differently to be more efficient with a large number of smaller threads, rather than a smaller number of larger threads.

The real-time thread is designed to be more 'responsive' to system events (don't confuse with 'user responsiveness')- this is important probably most commonly with audio engineering, where low-latency is important, but is useful in all sorts of more 'engineering' type situations (monitors, controllers, etc.).  The downside I guess to this is that this type of setup probably suffers more when doing multitasking type operations.

---

