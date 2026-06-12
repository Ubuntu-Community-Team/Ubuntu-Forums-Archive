---
title: "iptables rule to allow nfs?"
date: 2005-06-10
forum: General Help
---

### Post by shakin on 2005-06-10
I'm trying to get my Ubuntu box to mount an NFS share on an old Red Hat box. The RH box is running a firewall, configured from /etc/init.d/firewall.

Since it appears as though NFS through firewalls is not easy, I decided to open everything from my Ubuntu box to the RH box with this:

${iptables} -A INPUT -s 111.111.111.111 -j ACCEPT

However, I still get an error trying to mount the NFS drive: mount: RPC: Remote system error - Connection refused

Sounds like the firewall is still active. I did re-run the firewall script after making the change. Does that line not do what I assumed it would? What's the appropriate iptables command to open the connection between these two boxes. Note that I do have proper hosts.allow and exports entries for NFS between the computers.

Thanks.

---

### Post by C03N on 2005-06-10
If you haven't already, you may want to consider killing the firewall to validate that a connection can be made w/out it runnnig.

---

### Post by shakin on 2005-06-10
[QUOTE=C03N]If you haven't already, you may want to consider killing the firewall to validate that a connection can be made w/out it runnnig.[/QUOTE]

I know, but this is a box directly on the net... running a production mail server... not fully patched (patching will break so much I don't even want to think about it). Only the internet-exposed apps have been upgraded. It's an old Red Hat 8 install I inherited with this new job and it's going to be replaced very soon.

---

