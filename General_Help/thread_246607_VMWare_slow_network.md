---
title: "VMWare slow network"
date: 2006-08-29
forum: General Help
---

### Post by Guimas on 2006-08-29
I had some problems with VMWare Server and Ubuntu (as host) recently: a file transfer between the guest and the host was very slow. Between any other machine on my LAN, things were normal.

In a post on the VMWare foruns I found a solution: using ethtool, I just run "ethtool -K eth0 tso off", and the transfers are normal, just like any network transfer.

My question is, how do I set up this permanently? I have to run this command every time I turn on my computer, before initializing my virtual machine.

Thanks in advance, 

Guimas

---

### Post by PriceChild on 2006-08-29
You could add it to "System>Preferences>Sessions" in the "startup" tab

However there must be a "better" solution.

---

### Post by Guimas on 2006-08-29
> **PriceChild said:**
> You could add it to "System>Preferences>Sessions" in the "startup" tab

However there must be a "better" solution.

Yeah, that's what I feel, since this is a network configuration, it should go somewhere in the /etc directory...

Anyway, I totally forgot I could put it there, thanks for the idea.

---

