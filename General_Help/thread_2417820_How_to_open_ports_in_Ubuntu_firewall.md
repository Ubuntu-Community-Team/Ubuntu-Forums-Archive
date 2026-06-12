---
title: "How to open ports in Ubuntu firewall?"
date: 2019-04-27
forum: General Help
---

### Post by yatski on 2019-04-27
How do I open ports in Ubuntu firewall?

According to list here([https://forums.tripwireinteractive.com/forum/killing-floor/technical-support-aa/killing-floor-support/31419-ports-used-by-killing-floor](https://forums.tripwireinteractive.com/forum/killing-floor/technical-support-aa/killing-floor-support/31419-ports-used-by-killing-floor)), I should allow these:

7707 UDP/IP (Game Port)
7708 UDP/IP (Query Port)
7717 UDP/IP (GameSpy Query Port)
28852 TCP/IP and UDP (Allows your Server to Connect to the Master Server Browser)
8075 TCP/IP (Port set via ListenPort that your WebAdmin will run on)
20560 UDP/IP (Steam Port)

Or should I just bluntly allow all traffic during gaming session?(I've tried it once and it didn't connect to server.)

---

### Post by Holger_Gehrke on 2019-04-27
While Ubuntu comes with a firewall pre-installed, it is **not** active by default. If you had configured it, you'd know how to open ports, I think :-)

The post you're linking to talks about opening ports in your **router's** firewall for your **server**. If the router isn't allowing unrequested packets - basically requests from other players to the server you're running - from the outside into your network and sending them to the right host, then your server will run, but nobody except yourself and people on your LAN will be able to connect to it.

Holger

---

### Post by mastablasta on 2019-04-29
also here are instructions for the firewall interface GUFW and how to use it: [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

