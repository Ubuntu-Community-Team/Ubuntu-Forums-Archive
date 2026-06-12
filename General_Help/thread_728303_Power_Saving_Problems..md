---
title: "Power Saving Problems."
date: 2008-03-18
forum: General Help
---

### Post by sTpny on 2008-03-18
Hi Guys.. This computer isn't hibernating properly. I see the dhcpbd errors are these related? Why is it looking for a redhat folder? Is that part of ubuntu, or have I messed something up somewhere?
What it's actually doing, in spite of what the log says, is filling the screen with a bunch of ascii happy faces, in stead of powering down. From this state, the only solution I've found is a hard boot, and let the file system recover. I'm not sure how dangerous that is in linux, but I know its real bad in Windows. Anyhow, I was just wondering if anybody knew how to fix this.  It's important, because our electricity bill is through the roof. 

Heres my user.log.  Should I post any other logs as well?

The computer is pentiumIII compaq deskpro running gutsy gibbon.


Mar 18 13:03:36 MikesPC gnome-power-manager: (mike) Suspending computer because System idle
Mar 18 13:03:39 MikesPC dhcdbd: Unrequested down ?:3
Mar 18 14:08:38 MikesPC dhcdbd: Started up.
Mar 18 14:08:40 MikesPC dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Mar 18 14:08:44 MikesPC dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Mar 18 14:08:44 MikesPC dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

Thanks in advance.

sTpny

---

