---
title: "Network usage, how to see what programs are using my bandwidth?"
date: 2006-12-17
forum: General Help
---

### Post by userundefine on 2006-12-17
Greetings all,

Trying to get a handle on what is behind what the System Monitor keeps telling me about my network usage.  It says I'm constantly maxing out my upload, which is about 50kB/sec.  I don't have azureus running or other programs that would cause this.

I'm on a small home network with my comp connected directly to the router while other computers use wireless.  I don't know why that would matter, but who knows.

---

### Post by chalex on 2006-12-17
You could install ntop, the read the ntop documentation to configure it, then look at the results.

For simpler procedures, you can investigate "netstat -at" which will show you all open TCP connections or "lsof -i" which will show you which programs are using which ports.

---

