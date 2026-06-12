---
title: "Network Manager icon keeps spinning"
date: 2007-06-12
forum: General Help
---

### Post by Mr. Brownstone on 2007-06-12
I recently had the need to quickly install a DHCP server on my Acer Aspire 9300. I tried dhcpd and dhcp3-server, and once I finished with them I uninstalled them.

Since then the Network Manager has never fully loaded properly -- the icon just keeps spinning. (See attachment.) It does seem to connect okay (ie, I can ping stuff, access the 'Net etc), but every now and then the connection is dropped and restarted, and I can't choose any of my VPN options from the menu.

Here's a tail /var/log/messages ```
Jun 12 16:14:49 helluin gconfd (brownstone-5719): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 12 16:14:49 helluin gconfd (brownstone-5719): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 12 16:14:55 helluin gconfd (brownstone-5719): Resolved address "xml:readwrite:/home/brownstone/.gconf" to a writable configuration source at position 0
Jun 12 16:15:46 helluin dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 12 16:17:27 helluin dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 12 16:19:09 helluin dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 12 16:20:50 helluin dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 12 16:22:31 helluin dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 12 16:24:12 helluin dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 12 16:25:53 helluin dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
```I'm using Feisty Fawn 7.04. Thanks for any help.

---

### Post by Mr. Brownstone on 2007-06-12
*Nudge.*

---

### Post by fragos on 2007-06-12
The spining icon means its attempting to connect.  You could try dialing the access number on a voice line to see if it answers with a high pitch wine.  If not the number isn't valid.  I haven't used dial up in a while but if you can, place the modem answering sequence on your PC speakers.  You should be able to hear the far end modem answer and the two modems will negotiate the optimum speed too connect at.  If you will, an audible assurance that all is proceeding normaly.

---

### Post by Mr. Brownstone on 2007-06-13
Thanks for the reply, but I don't use dialup.

---

### Post by CocoAUS on 2007-06-13
What happens if you click it again while it's trying to connect?  I had this problem until the latest kernel update / I switched to Debian.  I would click the network I wanted once (or it would try to connect at startup), but then I'd have to click the network again to get it to connect.

---

### Post by fragos on 2007-06-13
Sorry about my confusion on dial up.  Spinning icon still means trying to connect.  CocoAUS has a good suggestion, effectively stopping the unmade connection and initiating a new one.  I find the network monitor applet helpful because as well as status it gives you direct access to network configuration.  The monitor plays nicely with the manager.

---

