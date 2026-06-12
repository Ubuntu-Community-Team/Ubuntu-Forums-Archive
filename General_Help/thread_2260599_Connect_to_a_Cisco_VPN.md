---
title: "Connect to a Cisco VPN"
date: 2015-01-13
forum: General Help
---

### Post by Skyflier on 2015-01-13
Hi, 
I'm trying to connect to my university's VPN using Ubuntu 14.04. It happens that my institution uses Cisco VPN with two certificates to authenticate, a user CA and a Chain certificate.
But I'm having trouble connecting, most specifically with the Cisco VPN Client. My college provides me with a source code of the client to download, but I can't compile it. The version is really old and was meant for kernel 2.6. 
Is there any other way to connect to a Cisco VPN? A way to compile and install the client for example?

---

### Post by aromo2 on 2015-01-13
In Synaptic, search for cisco.  Install the VPN client and the Network Manager plugin.

---

### Post by Skyflier on 2015-01-13
I already did that but I can't find how to import the certificates to it, there's no option in the UI.

---

### Post by Skyflier on 2015-01-13
Well I almost found the way to do it.
I installed the openconnect package and plugin, that one provides Cisco AnyWhere VPN and allows me to connect using certificates.

However I still can't connect. The certificates provided by the college are not in .pem format, I converted them but I gives me an error connecting.
I will contact the support centre of the institution to see if they can give me a hand since it seems like the problem is with the certificates. They provide instructions on how to connect in Linux but they use Gentoo as reference and it is highly different from Ubuntu.

---

