---
title: "ssh timeout mechanism changed in gutsy"
date: 2007-11-07
forum: General Help
---

### Post by Micah Elliott on 2007-11-07
I'm using ssh (client, on Gutsy) to access another Gutsy sshd server.  A timeout occurs after 15 minutes (900s).  But the same setup works fine (no timeout) when my client is Feisty.

My means to avoid being timed out is the following in my client ~/.ssh/config:

    ServerAliveInterval 60

Now that I'm using a Gutsy client, the setting appears to be ignored.  Anyone else seen this?  Any suggestions?  (I'd like to avoid screen/ping/time hacks and just get some clean ssh setting working.)

---

### Post by nuggien on 2008-03-07
I'm experiencing this same problem.  Anyone have explanations?

---

