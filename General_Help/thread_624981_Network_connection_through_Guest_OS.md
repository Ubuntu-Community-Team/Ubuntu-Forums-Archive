---
title: "Network connection through Guest OS"
date: 2007-11-27
forum: General Help
---

### Post by corefile on 2007-11-27
My company has a SSL VPN that has a Windows only client, I would like to us a VM (vmware,virtualbox) Guest Windows OS to make the SSL vpn connection, then from my linux host either route or via proxy connect through the Guest OS vpn client connection.

---

### Post by DagMan on 2007-11-27
I don't know everything to that, and I'd suggest breaking it up into peices in differant threads if you need to know how to do all the steps involved.
You'd want to start off just getting the networking set up so that your guest and you host have differant IP addresses so you talk back and forth between the guest and host, it sounds like.
Try this
[http://ubuntuforums.org/showthread.php?t=346185](http://ubuntuforums.org/showthread.php?t=346185)

---

### Post by corefile on 2007-11-27
I already have both the host and guest OS networking working in VMware, both have their own IP, and both can connect to the internet. What I need to know is how I can access the VPN network on the Guest windows OS, from my linux host os

---

