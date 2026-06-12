---
title: "Bittorrent kills my internet connection"
date: 2013-12-07
forum: General Help
---

### Post by morningc1986 on 2013-12-07
It seems my Transmission Bittorrent client kills my internet connection periodically on the current operating system (an Ubuntu 12.10). After browsing numerous websites it seems it's:

[LIST=1]
[*]linked to Ubuntu (since Windows isn't affected by it)
[*]the Ubuntu distro (some older versions don't have this problem)
[*]it can only be solved by lowering the number of peers
[/LIST]
 
Does anybody know why this problem only occurs on Linux? Why do applications like Amule where I can have thousands of connections not cause the same problem? Does anyone know another solution? Sysctl unfortunately didn't do it for me.

PS: my ISP and router are perfectly fine.

---

### Post by tgalati4 on 2013-12-07
Try the *nice* command to see if that lowers the load.  Describe in detail what you mean by "killing my internet connection".  If you are getting full download bandwidth, then any process that needs upload bandwidth will slow down (like using a browser).  What does your network monitor show when transmission is in use?

Perhaps you need to set some Quality of Service (QoS) rules in your router.

---

