---
title: "what port should ugidd run on?"
date: 2007-12-02
forum: General Help
---

### Post by krazyman on 2007-12-02
Hi All,

I can't find an answer to this seemingly simple question anywhere.

By running ugidd on my clients, I expect user mapping to work for my nfs shares. However, it doesn't. I have added the following line into my /etc/hosts.allow on the client just to be sure:

rpc.ugidd: <ip.of.server.here>

I have the following in /etc/exports on the server:

/share <ip.of.client.here>(rw,async,map_daemon)

Now the man page for rpc.ugidd states that unless the -P option is set, then ugidd runs on a random port. My understanding is that the nfs file server machine queries the ugidd 'server' running on the client. If this is the case, how would the file server know what port to connect on? Is there a standard port which I need to set ugidd to run on?

Of course I could be barking up the wrong tree and there's some other explanation as to why it's not working...

Any help appreciated.

---

### Post by krazyman on 2007-12-02
OK mystery solved.

I found this: Bug#403232: nfs-kernel-server: map_daemon option silently ignored in /etc/export

which explains that map_daemon doesn't work in nfs-kernel-server. I have installed nfs-user-server, and now it all works. Precious little info on the net about this!!!

---

