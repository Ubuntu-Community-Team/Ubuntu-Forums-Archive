---
title: "Load Balancing Question"
date: 2008-04-06
forum: General Help
---

### Post by Prospero2006 on 2008-04-06
The situation:

I manage a samba server on a single Linux machine that is accessed by over 100 computers on my school network. Most of the time, the network traffic is acceptable.
However, there are times when 20-30 students utilize this single drive rather intensively.
It gets throttled.

So, I am thinking I should parallelize somehow. Ideally I would like to have one machine distribute traffic to two or more machines that have identical data on them.  I've never tried it before. 

Who among you is familiar with distributed load balancing, and are there any good articles on it?

I have several high quality servers sitting idle right now I could put into action.

Thanks!

---

### Post by ericsante on 2008-04-06
most probably the problem is disk IO, this being the case I would suggest a R0 or a R3 configuration, R4 if you want parity.  This will supply all the bandwidth you may need.

The problem with Windows and Samba is that RPC is a "always connected" protocol, so adding more servers and a load balancer will not prevent the heavy hitters on your machine to route to another machine.

If you want to distribute your files among many servers, might I suggest Windows DFS, since your clients are windows clients DFS might be a better fit. 

I would still look at what is starving the clients on on samba server first and fix that problem.

---

