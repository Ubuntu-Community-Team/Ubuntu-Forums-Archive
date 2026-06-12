---
title: "Is anyone else here having recent troubles connecting to Kademlia?"
date: 2008-05-23
forum: General Help
---

### Post by Keyper7 on 2008-05-23
Not exactly an Ubuntu issue, more of an aMule issue, but still, I'm curious to see if only me is experiencing this.

Started a couple of weeks ago. Not only I can't get pass the "firewalled" state, but I go to "off" after a while (I lose the nodes one by one). It worked before and I don't remember changing any settings. My ports are okay (connecting to servers with high id perfectly), I'm sharing large files... I think I'm doing everything by the book.

So, can I at least know if I'm alone at this or not? :)

---

### Post by atomkarinca on 2008-05-23
Well, I just checked and it seems OK.

---

### Post by Keyper7 on 2008-05-23
> **atomkarinca said:**
> Well, I just checked and it seems OK.

Could you please share which server and node list you usually use?

---

### Post by atomkarinca on 2008-05-23
[http://emule-inside.net/nodes.dat](http://emule-inside.net/nodes.dat)

I didn't change anything from the default configuration. Maybe you're having a port forwarding issue. Does ed2k protocol work alright?

---

### Post by Keyper7 on 2008-05-23
Unlikely, since I didn't change anything on the router configuration and as far as I remember port forwarding configuration wasn't even available.

What server do you use to bootstrap? I've heard some servers are more kad-friendly than others...

What really find strange about this issue is that I had firewall problems before but I would get "firewalled" status and stay like that. This time I'm going to "off" after five minutes or so.

Connection to server is perfect, I'm uploading stuff right now.

Thanks for your time, by the way.

EDIT: Sorry, forgot about your question. Yes, e2dk seems to be working fine.

---

### Post by atomkarinca on 2008-05-23
Maybe you should try enabling UPnP under Connection.

---

### Post by Keyper7 on 2008-05-23
Whatthe...? I restored aMule to do what you suggested and suddenly Kad is ok? It's the first time I got that in days. Let's see if it now stays that way.

Figures... came back as misteriously as it went away.

Anyway, thanks for all the help, atomkarinca, I really appreciate it.

---

### Post by atomkarinca on 2008-05-23
No problem. UPnP is used where you can't get your router to do the port forwarding. Keep it in mind, you might use it with torrent and such, too.

---

