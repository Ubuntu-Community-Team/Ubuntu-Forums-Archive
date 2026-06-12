---
title: "Stop the bandwidth killer"
date: 2008-03-12
forum: General Help
---

### Post by Ripfox on 2008-03-12
So, how can one, being the Admin of the router, kill Bittorrent connections at will from other users on your network? I use a Linksys router and know how to log onto it, but where is the setting to kill bittorrent connections on my network?

TY

---

### Post by Ripfox on 2008-03-13
bump...I need to kill the bittorrent monsters

---

### Post by tubasoldier on 2008-03-13
I'm not sure what router you have... that information could help

I personally have a Belkin. I have the ability to use Client IP Filters. Perhaps your router has something similar? You can block computers, according to their ip address, from using certain ports. So simply block the bittorrent ports.

It all just depends on your router

---

### Post by Suparious on 2008-03-13
Most likely, you would want to find a way to control your outbound connections. Common hardware with those functions would include Cisco or Juniper (netscreen)  products.

Most 'consumer-grade' or common routers only firewall incoming connections, and most torrent clients can use NAT routing (and virtual ports) around outbound firewall policies.

You could set-up another Ubuntu box and google "linux router how-to" or "ubuntu router how-to", ect.. and use that to replace the existing linksys.

---

### Post by daengbo on 2008-03-13
You can go Comcast's route and forge packets terminating the connection. Shaping BT torrent is a real pain. It can be on any port. It can be encrypted. It can be tunnelled over SSH. You'll never find it if the user is sophisticated enough.

Your best bet is to create a terms of service document banning BT, get it signed, then simply block anyone who vilates the TOS.

---

### Post by Ripfox on 2008-03-13
Thank you for all your replies. This has been a good start.

:)

---

### Post by chadeldridge on 2008-03-13
I use the baseball bat method in my office ... tends to work really well.

---

### Post by Cadmus on 2008-03-13
> **chadeldridge said:**
> I use the baseball bat method in my office ... tends to work really well.

Ahh, a fine LART, this side of the Atlantic of course we prefer to use a cricket bat.

---

### Post by Oldsoldier2003 on 2008-03-13
> **Cadmus said:**
> Ahh, a fine LART, this side of the Atlantic of course we prefer to use a cricket bat.

for the nonviolent BOFH's just link their home dir and all their printers to /dev/null   doesn't save bandwidth but makes the admin feel a lot better....

---

### Post by the-edmeister on 2008-03-13
> **chadeldridge said:**
> I use the baseball bat method in my office ... tends to work really well.
I like the 'ring' from an aluminum bat!

---

### Post by Mithrilhall on 2008-03-14
Try building a MasterShaper. It works great on Bittorrent.


[www.mastershaper.org](www.mastershaper.org)

---

