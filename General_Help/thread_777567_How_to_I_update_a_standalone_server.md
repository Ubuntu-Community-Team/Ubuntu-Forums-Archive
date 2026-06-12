---
title: "How to I update a standalone server?"
date: 2008-05-01
forum: General Help
---

### Post by IanLinwood on 2008-05-01
I have installed 8.04 server as a test on a remote isolated network.

How can I collect updates (say using my 8.04 desktop) for the server version and take the updates to the remote network server and install them?

---

### Post by HermanAB on 2008-05-01
Hmm, my first question is why?  Since it is not on a network, there is not much motivation for doing updates.  Just leave it alone and it will keep working just fine for years to come till the hardware eventually fails.

Otherwise, you need to track which deb files changed, download them and install them manually with dpkg.

Cheers,

H.

---

### Post by ryot on 2008-05-01
You may want to look into apt-cache. I am currently setting this up on a test cluster to see how it works before placing it on production clusters. It may make things a bit easier but if the server is on an isolated network you may still need to copy all the updates to a CD or DVD to get them to the server. Anyone have any insight?

---

### Post by IanLinwood on 2008-05-02
> **HermanAB said:**
> 
Otherwise, you need to track which deb files changed, download them and install them manually with dpkg.

Cheers,

H.

The subject was slightly misleading, the server is not standalone, but on a restricted network with no external links.

I realise I'd need to put the updated on a CD or flash drive.

I'd like to update the server, but I'm unsure of how to locate/establish which packages are relevent and which method I'd use to update the server.

---

