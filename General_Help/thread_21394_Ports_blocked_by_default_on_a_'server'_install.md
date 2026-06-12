---
title: "Ports blocked by default on a 'server' install?"
date: 2005-03-22
forum: General Help
---

### Post by merc on 2005-03-22
I installed Hoary Array 6 by doing the following:

1) At the first prompt when cd boots, enter 'server' for minimal install
2) After installing from cd, apt-get install kdebase and xorg

Now I have kde setup and everything works great. Only problem is that I can't download anything using bittorrent. Installed "qtorrent", and uninstalled some packages that I thought might block ports (like iptables, netbase, netkit-inetd, iproute-pingar). Still, if I try to open a torrent, it says "Problems connecting to tracker". I tried two different bittorrent clients, both can't connect.  I forwarded the ports, changed from default to the range 8000-9000, then tried 40000-60000, then set my pc in the DMZ, and still it gives the same error. If I try using windows, it works fine.

Any idea if a "server" install of hoary has some software that blocks ports by default?

---

### Post by merc on 2005-03-22
Anyone?

If I do a default install of Hoary, will I be able to use bittorrent?

---

### Post by alastair on 2005-03-22
I don't seem to have problems - hoary latest. I tend to use "btdownloadheadless". Typing :

btdownloadheadless

on its own, give usage. There's an arg :

--spew <arg>
whether to display diagnostic info to stdout (defaults to 0)

Which could help debugging.

Usage :

btdownloadheadless <torrent file>

or try with the "spew" (set to 1 etc.)

---

### Post by az on 2005-03-22
"Any idea if a "server" install of hoary has some software that blocks ports by default?"

No.  It does not.  

"uninstalled some packages that I thought might block ports (like iptables, netbase, netkit-inetd, iproute-pingar"

That could be your problem?

---

### Post by merc on 2005-03-23
[QUOTE=azz]"Any idea if a "server" install of hoary has some software that blocks ports by default?"

No.  It does not.  

"uninstalled some packages that I thought might block ports (like iptables, netbase, netkit-inetd, iproute-pingar"

That could be your problem?[/QUOTE]

Well, I uninstalled them *after* I realized torrents weren't working. And even after uninstalling them, torrents still didn't work. So I'm sure it wasn't removing them that broke the config.

---

