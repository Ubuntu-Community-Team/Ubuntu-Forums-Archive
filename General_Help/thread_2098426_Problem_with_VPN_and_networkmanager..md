---
title: "Problem with VPN and networkmanager."
date: 2012-12-26
forum: General Help
---

### Post by nabdina on 2012-12-26
Hello, 

I have some problems connecting to my VPN through networkmanager. I have entered all the setting but whenever I try to connect by pressing the VPN connection, then simply nothing happens. No error message, no nothing. I have tried both OpenVPN and PPTP with the same results.

Any ideas?

I run Ubuntu 12.04 Server LTS with KDE

---

### Post by nabdina on 2012-12-26
I finally found the solution to the problem here [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/305606](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/305606)

[Chris Coulson (chrisccoulson)]("https://launchpad.net/%7Echrisccoulson")             wrote             on 2008-12-11:                          
"This is because you have your network configuration statically defined in /etc/network/interfaces. With this configuration, Network Manager won't manage your device.
 If you want to keep the static  configuration, but have Network Manager manage your device, you can  remove the "auto eth0" line from your /etc/network/interfaces."

---

