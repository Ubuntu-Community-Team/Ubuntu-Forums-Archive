---
title: "Upgrade to 17.04 breaks custom DNS inside NetworkManager?"
date: 2017-04-26
forum: General Help
---

### Post by mikey93898 on 2017-04-26
After upgrading to Ubuntu 17.04, my laptop no longer uses the custom DNS servers as I have entered into NetworkManager. For me this means my local DNS server is no longer used, and I'm now unable to resolve all my other local machines and VMs. The internet works fine in general though.

Looking into the issue further, it seems "systemd-resolved" is now automatically installed on this laptop, and my /etc/resolv.conf file points only to 127.0.0.53.

So I guess my question is: How do I either:

A] Tell systemd-resolved to obey custom DNS settings in NetworkManager
or B] Manually add my custom DNS servers into systemd-resolved (less desirable because I would lose the ability to configure on a per-connection basis with NetworkManager)

Any help appreciated!

---

