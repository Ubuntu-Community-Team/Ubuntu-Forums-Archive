---
title: "Change Synaptic ports?"
date: 2007-01-13
forum: General Help
---

### Post by Wise_One on 2007-01-13
Is there a way to change the ports Synaptic uses to get updates?

And if so, how can I see the current ports?

---

### Post by jpeddicord on 2007-01-13
Synaptic uses the same port as your web browser (80) to download updates. You cannot change the post itself, as it is required by the repository servers that hold the updates to use that port.

If you are on a proxy server, however, and need to change your proxy port, you can do that from Settings > Preferences > Proxy in Synaptic.

---

### Post by Wise_One on 2007-01-14
I see... Hey I got another question. When I go at Network Tools, on the first page it has two devices...

One called Loopback and another one which is my ethernet card. If I select my ethernet card and exit Network Tools, it's gone. Nothing's saved. Also, when at Loopback, the Settings button is unavailable.

If I select my ethernet card and then press the Settings button, it comes up with a message saying that I am not allowed to change the system configuration. Well, that's true. I have to be logged in as root to change that.

So, how do I log in as root? I HAVE to change the Loopback device 'cause I think that's why I can't update Synaptic...

---

### Post by mandible on 2007-03-01
I can't get updates inside my companies firewall but I can access port 80 for web access just fine.  Any ideas?  If the synaptic port is using 80 I can't see how it could be blocked in this way.

---

