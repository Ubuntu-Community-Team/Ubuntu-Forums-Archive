---
title: "[SOLVED] network manager errors on reboot/shutdown"
date: 2008-04-07
forum: General Help
---

### Post by mandrill on 2008-04-07
Saturday I was playing around with conky, installed l-m sensors, something else, yesterday it (Gutsy) started giving me a whole page of network manager errors when restarting or shutting down, I uninstalled conky, l-m sensors, etc....no change. I get things like (always the same things) "debug open sockets", "caught terminal signal", "cifs vfs server not responding", and one more below that about cifs with numbers in it. I thought at first it was my cifs share from windows that automounts,
but it has never done this in the 2 months I've had it going.

Anybody got any Ideas?

---

### Post by mandrill on 2008-04-08
> **mandrill said:**
> Saturday I was playing around with conky, installed l-m sensors, something else, yesterday it (Gutsy) started giving me a whole page of network manager errors when restarting or shutting down, I uninstalled conky, l-m sensors, etc....no change. I get things like (always the same things) "debug open sockets", "caught terminal signal", "cifs vfs server not responding", and one more below that about cifs with numbers in it. I thought at first it was my cifs share from windows that automounts,
but it has never done this in the 2 months I've had it going.

Anybody got any Ideas?

I have since discovered that this is a cifs runlevel issue please see Sander Marachals' excellent explanation (and cure) [http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/](http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/)

---

