---
title: "Rsync over VPN with specified network interface"
date: 2024-04-25
forum: General Help
---

### Post by macj72x on 2024-04-25
I'm trying to rsync some data to a remote device.  I have a vpn server set up on the remote device(192.168.1.2) with my router as the client device.  With the local device I have a specific network interface (br1/192.168.5.1) that data needs to travel out of to be routed over the tunnel. I can ping the remote device from the local device using ```
ping -I br1 192.168.1.2
```

So is there a certain syntax I need to accomplish this properly or should I look at a completely different architecture? Right now I'm trying different variations of something like this ```
rsync -avz -e -b 192.168.5.2 /path/to/origin/file/ destusername@192.168.1.2:/path/to/origin/file/
```

---

### Post by TheFu on 2024-04-26
Check the routing tables before and after the VPN is up.  Ensure the tunnel routing metric is lower than non-tunnel metrics for the route desired.

There isn't any way to force an application to use a specific route/VPN except by controlling the routing tables on the system. Here's a handy alias:
```
alias iproute='ip route | column -t'
```
since _route -n_ is deprecated and has been using unsupported code since 2011!  The newer ip commands have the same information, just in an ugly format. Sigh.

---

### Post by The Cog on 2024-04-26
TheFu is (as always) right. But I will add:

Although you can order ping to send via a given interface, you can't do that with rsync. I think you can ask it to use a chosen source address with --address=ADDRESS, this won't influence the direction that the routing table sends the packets in (It may influence the path any reply takes though). 
Use **[FONT=Courier New]ip route get 192.168.1.2[/FONT]** to see where they will be sent. Also **[FONT=Courier New]ip route get 192.168.1.2 from 192.168.5.1[/FONT]** but I doubt the answer will change.

Full details of all the IP addresses involved would help us understand. There seem to be at least 3 devices from your description, and there will be 2 tunnel ends so that's at least 5 IP addresses to fill the picture.

---

