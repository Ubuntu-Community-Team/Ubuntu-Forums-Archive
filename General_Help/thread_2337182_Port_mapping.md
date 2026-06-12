---
title: "Port mapping"
date: 2016-09-15
forum: General Help
---

### Post by neil37 on 2016-09-15
Hi,

I'm wondering if it is possible to re-direct ports to use one same port.
For example I have a VPN provider that allows one port to be opened on their service.
This is good for one application but I find that I am unable to use the same port for another application as it is in use.
Is there a way to have more than one program use the one same port... maybe map a local set of ports to one external so they all
point through the opened port on the VPN?

Thanks

---

### Post by ian-weisser on 2016-09-15
EDIT: SeijiSensei's answer is better than mine. Use his!

---

### Post by SeijiSensei on 2016-09-15
I don't know what kind of VPN protocol your service uses, but one port is the norm.  I have static OpenVPN connections to my remote servers.  Each uses one port, but they handle all the traffic sent their way just as if the server were here on my local network.  Perhaps you just need to configure your VPN client to use the remote VPN host as your default gateway.

---

### Post by neil37 on 2016-09-15
I'm using OpenVPN.
If I run Program 1 on port 16655 which is the same as the port that has been forwarded on the VPN server to allow all incoming connections on this port.
When I try and run Program 2 on port 16655 so that I can also use the forwarded port, it will fail as 16655 is already in use. So I cannot get traffic from multiple programs
to use the same forwarded port on the VPN server. I can only open one port on the VPN servers at a time.

---

### Post by SeijiSensei on 2016-09-15
You can't use the port supporting the OpenVPN tunnel for other services.  It's already dedicated to OpenVPN.  Perhaps you should describe what you're trying to do in more detail.

If you want to forward a port back from the OpenVPN server to a port on your local machine, you would need either to write appropriate iptables rules on the server, or use an application-level proxy like [tcproxy]("https://github.com/dccmx/tcproxy").  In either case you would need to use a different port than the one assigned to OpenVPN.

---

### Post by neil37 on 2016-09-15
OK the OpenVPN client when connecting to a VPN server (on the service provider) has a certain port opened. This one port allows connections to flow into the client and not be protected by the VPN firewall.
This is all this port does.. opens up (port forwards) the firewall on that one port.
This is where I have issues because I can only seen to allow one application to use the port not multiple.

I'm not sure how else I can explain it.

---

### Post by SeijiSensei on 2016-09-15
Let's suppose you have a tunnel established with 10.10.10.1 as the VPN IP address on the server, and 10.10.10.2 as the VPN address on the server.  You should be able to see all the ports on both machines via the tunnel.  

I think the confusion arises from your use of the term "port forward."  There is no port forwarding going on, just a connection over the tunnel.  Port forwarding would apply if you wanted to let people connect to, say, port 80 on the VPN server and have that connection be forwarded back to port 80 on the VPN client machine.  I doubt you can do anything like that since you don't control the VPN server.

I'm still not clear on what your question is. What specific application are you trying to set up?  Most VPN providers only intend for their connections to be used for web surfing or similar activities.  For instance, if you made 10.10.10.1 the default gateway on your machine, web browsing would happen over the tunnel.  However this gets tricky because you need to maintain the connection between the two machines over the public Internet.  In practice, I would use custom routing rules to handle this case (assume 172.16.16.16 is the public IP of the VPN server, and 192.168.1.1 is the internal IP of your router):
```

sudo ip route add 172.16.16.16/32 via 192.168.1.1
sudo ip route default via 10.10.10.1

```
The first command tells the client to send traffic to the server's public address via your router.  The second command tells the client to send all other traffic over the tunnel.

---

