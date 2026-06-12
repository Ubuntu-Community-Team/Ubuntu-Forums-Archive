---
title: "BitTornado firewall help"
date: 2007-02-17
forum: General Help
---

### Post by maniacrobbins on 2007-02-17
When I'm downloading torrents via BitTornado, the status light is yellow. Upon checking online, I learned that a yellow status light probably means that a firewall is slowing my download speeds. With BitTornado, my average speed is anywhere from 1kbs to 9kbs so I do have some downloading problem. Can anyone help me with this problem?

Thanx

Dave

---

### Post by CocoAUS on 2007-02-17
Since you're not using Windows, I doubt your firewall is causing problems.  Most likely, you need to forward ports from your router.  What does BitTornado use for ports?  6881-6889 or something?

Either way, log into your router, then find the port forwarding option, and insert the port range used by BitTornado.  The option might be under "Virtual Server," "Special Applications," or simply "Port Forwarding."  You might also have to forward ports specifically for your computer, so do a "ifconfig" in your terminal and look at what your computer's IP is.  It will be similar to your router's IP, only with a distinct ending.  For instance, if your router's IP is 192.168.1.1, your computer's IP would be something like 192.168.1.148 (the last digits changed).

Hope that helps.

---

### Post by maniacrobbins on 2007-02-18
Sorry, but I have no idea how to log into a router while using Ubuntu.  Can anybody help?

---

