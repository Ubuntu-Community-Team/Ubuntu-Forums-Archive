---
title: "remote connection over network problems"
date: 2007-03-15
forum: General Help
---

### Post by m.musashi on 2007-03-15
I have set up my desktop and laptop with ssh and I can use Nautilus to connect to the desktop from the laptop to share files and such. However, the reverse is troublesome. Since the laptop gets it's IP address via DHCP it is not always the same. If I connect once, I get a message about being unknown and I do I want to trust it. I say yes and then it creates a file in .ssh called known_hosts. However, if the IP address changes then the RSA (I'm not sure what that is but seems to be a security thing) is reported as not matching and to contact my sysadmin. I'm the sysadmin but the only way I found to fix it is to delete the known_hosts file but that is kind of a pain. Is there a way to make ssh more permissive on my LAN so I don't have to worry about the changing IP? I don't want to try and set up static IPs.

Thanks.

---

