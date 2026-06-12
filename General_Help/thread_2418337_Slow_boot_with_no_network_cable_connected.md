---
title: "Slow boot with no network cable connected"
date: 2019-05-05
forum: General Help
---

### Post by panja on 2019-05-05
I'm running Ubuntu Server 18.04.2 and when the network cable is not connected and I reboot it hangs on getting an IP from the DHCP server.
Online I found lots of articles about this but all are outdated.
They are all saying to edit /etc/network/interfaces and change auto to allow-hotplug.
Except the interfaces file is not used anymore on 18.04.2 as far as I can see.

 I cannot use a static IP on this machine.
Is there a way to remove the timeout?

---

