---
title: "Yet another synce problem..."
date: 2006-07-06
forum: General Help
---

### Post by beniwtv on 2006-07-06
Hi.

I'm trying to get synce working on ubuntu dapper.

I've got a Casio Cassiopeia EM-500. I can run successfully synce-serial-config ttyUSB0 and synce-serial-start. 

Then, the device doesn't connect (in breezy it did). But I tap connect on it and it connects well.

From this point, everything seems to be ok, in fact, I can browser the web on the device with the proxy on my PC. 

But when I try to start a tool: I get /home/beni/.synce/active_connection: File not found. RAPI: unspecified error

I tried both using dccm and vdccm. Both state that they're listening when starting in foreground mode. 

My question is, why dccm doesn't create this file? (I suppose it has to). I'm running it as the normal user, as I did in breezy (it worked in breezy).

Another thing I noticed was that in breezy I could see the port 990 on the device open in network tools. In dapper it doesn't shows up. I'm not using firestarter or something else. And my iptables are empty (I believe). Maybe this has something to do with the problem?

What I don't understand is why it doesn't work anymore on dapper. Even using the same packages as I did in breezy.

Thanks for help.

---

### Post by beniwtv on 2006-07-10
Anyone has the same problem? Anyone solved that?

---

