---
title: "What's your opinion on best remote access?"
date: 2008-02-28
forum: General Help
---

### Post by bdemers on 2008-02-28
I am pre-install on a server for roaming users.  The clients will VPN into the domain, authenticate, and be led to a virtual session of their own desktop.  I will be using earlier Xen, not KVM for the virtual software, as the server is too old for processor virtual support.  What I am still debating is the content of the virtual session.  There are many ways of remote access, but the client will always be remote accessing, even when in home office.  This will be the client's desktop, so the fewer doors to open, the better, at least from clients viewpoint.  Thinking of a terminal server for each virtual session, with a fat client arrangement, whereby the clients local computer would handle any predetermined cpu or bandwidth intensive loads.  With this setup I will need to resolve how I determine what should be at the clients side or the servers side of the network.  Maybe I will need to limit access to a user and MAC address combo.  So...if you've had some excitement with any of these concepts, I'd like to know.

---

