---
title: "no vpn then no download"
date: 2014-06-04
forum: General Help
---

### Post by jgw on 2014-06-04
I am running with ubuntu 14.04  I am not competent to write this but, perhaps, somebody already has.  I found one run at it in the sabnzbd forum but it never went anyplace.  What I am looking for is something that will sense when a vpn goes down and stops all downloading.  I use private internet vpn and sabnzbd for downloading.  

If anybody knows of such a facility I would be grateful.

Thank you...................

---

### Post by TheFu on 2014-06-04
I don't know anything about BT or using a vpn to hide in this way, however, .... on Linux the route would change when the VPN was dropped, so you could monitor that and kill the BT when it happens with a 5 line (or less) script - bash would be easy.  The downloading program should store the PID somewhere - perhaps in /var/run/ ?

Run **route** every minute (or whatever the VPN-Status checking process is) to see if the specific VPN route is there - something like **route |egrep -c tun0** and check to see that it is non-zero. If zero, the vpn is dropped and you'd want to kill the downloading.

---

