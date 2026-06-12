---
title: "Ports and Moblock"
date: 2008-02-17
forum: General Help
---

### Post by Duffnuff on 2008-02-17
I recently started using Moblock which is something like Peer Guardian for windows.

What I want to know is which ports i need open?
Im running Edubuntu Gutsy. Gnome front end.

Which port needs to be open so the weather panel addition can update. I also have some problems connecting to  websites under Firefox. when i stop moblock everything updates and loads fine.

any ideas??


Thanks
DF

---

### Post by wolfen69 on 2008-02-17
are you running moblock with a p2p app? if so, which app?

---

### Post by Duffnuff on 2008-02-17
Yes, I have it configured properly using Azureus. The ports for it have been white-listed. and it works just fine with moblock started, my ports are open on Azureus.

Example, Myspace wont load until I stop moblock, same thing with you-tube and various other sites (not all sites through)

I just want the Weather tracker on the Gnome toolbar add ons to be able to update, also the websites to load properly

DF

Also, is there a GUI for Moblock?

---

### Post by jre on 2008-02-18
If you want to check Azureus' traffic you must NOT whitelist it's port!

For surfing, generally whitelisting ports 80 and 443 in WHITE_TCP_OUT is enough.

For the weather panel: check with "tail -f /var/log/moblock.log" which IP is blocked and whitelist this IP in WHITE_IP_OUT.

On moblock-deb.sf.net there's a GUI called mobloquer. Especially the soon coming version 0.4 is very nice. (At least) there you can whitelist IPs directly.

---

### Post by Duffnuff on 2008-02-18
Thanks! That got it working.

I'll look into that GUI, it looks nice.

Thanks again for the help

DF

---

