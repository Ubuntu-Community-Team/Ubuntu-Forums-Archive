---
title: "Share a VPN connection with Ethernet"
date: 2019-06-02
forum: General Help
---

### Post by hresna on 2019-06-02
[COLOR=#242729][FONT=Arial]running Ubuntu 18.04 LTS.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm looking to replicate functionality I can do on the macos hardware & OS: Share the OS-level VPN connection with a hardware interface. [/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]In this particular case, a laptop connects to unsercure wifi, establishes VPN tunnel, the VPN is then shared with an Ethernet interface, upon which I connect a DD-WRT router (double-nat, obviously) that supplies secure wifi/ethernet to clients. The reason for using a laptop with a real OS for the gateway is to handle captive portals via browser (as many hotels do).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]This setup makes it impossible for the clients' traffic to leak over the gateway wifi since only the VPN connection is shared. If VPN drops, the clients have no connectivity at all. Easy enough to do under macos with l2tp.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Is there a reasonably simple way to do this from the gnome GUI? It took me hours trying to get just the L2TP+IPsec tunnel to work and finally gave up. I am using OpenVPN now. But I can't find a simple way of sharing the OpenVPN connection specifically, just the wifi, which would fall to insecure if the tunnel ever dropped, exposing the client traffic.[/FONT][/COLOR]

---

### Post by LwIh%*7 on 2019-06-03
This maybe? 

[https://askubuntu.com/questions/926116/share-my-vpn-connection-with-other-lan-users](https://askubuntu.com/questions/926116/share-my-vpn-connection-with-other-lan-users)

---

### Post by hresna on 2019-06-03
> **ImpWarfare said:**
> This maybe? 

[https://askubuntu.com/questions/926116/share-my-vpn-connection-with-other-lan-users](https://askubuntu.com/questions/926116/share-my-vpn-connection-with-other-lan-users)

Thanks for this - I landed on that link yesterday and it does look about as close to what I'm trying to do as I've found. But it's a lot more CLI and less GUi than I was hoping for!


My fall-back is to switch up the implementation a bit, have the router establish the VPN tunnel and see if I can set up a firewall rule in the router itself to work as the "internet kill switch" if the VPN drops. I'd lose the ability to do secure browsing on the host-gateway, but I think the setup might be a lot simpler.


Will keep at it a while longer though before giving up. I may try to tackle that CLI method...

---

### Post by hresna on 2019-06-13
With some trial and error and help from a different forum, I managed to get this working.
 
The only part that can be done with GUI is setup for the OpenVPN connection, and the client network on the second interface (this is done in network manager). In my case, ens9 is a secondary Ethernet interface that I configured with static IP on a unique local subnet. Client devices were pre-configured to use this IP as their gateway.
 
Full verbose details of my solution here: [https://www.linuxquestions.org/questions/linux-networking-3/share-vpn-with-ethernet-interface-4175655027/](https://www.linuxquestions.org/questions/linux-networking-3/share-vpn-with-ethernet-interface-4175655027/)
 
VPN kill-switch for the Gateway device itself goes like this:
 
Make these changes in /etc/sysctl.conf
```
 #disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
#enable packet forwarding
net.ipv4.ip_forward=1
```
 
In UFW’s default config file (/etc/default/ufw), make this change:
```
DEFAULT_FORWARD_POLICY=“ACCEPT”
```
 
Through command line, edit the ufw rules as so:
```
 sudo ufw default deny incoming
sudo ufw default deny outgoing
sudo ufw allow out on tun0
sudo ufw allow out on wlp2s0 to XXX.YYY.ZZZ.AAA port 1194 proto udp
```
In the last line, use the name of the interface you are using for the WAN connection (use ifconfig command to see all interfaces), and use the IP address and port number for your OpenVPN server – this can be lifted from the ovpn.config file supplied.
 
This much gets you a working VPN kill-switch on the gateway device. The last step is masquerading the VPN connection on the secondary interface (in my case, the Ethernet device called ens9).
 
Don’t use the GUI method from nm-connection-editor to enable sharing, it will bypass your kill switch. Instead, edit the file /etc/ufw/before.rules by adding a nat section just above the *filter heading:
```
 ### Start OpenVPN Share rules
### NAT table rules
*nat
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 192.168.10.0/24 -o tun0 -j MASQUERADE  
COMMIT
```
Where 192.168.10.0/24 stands in for the IP address range of your client network. In my case, I defined it statically within that range. If your use case requires it, you would go the extra step of configuring your gateway to DHCP on that interface.
 
And that was pretty much it.
I expected to need a ufw rule like this:
```
sudo ufw allow out on ens9 to 192.168.10.0/24
```
But it works just fine without it.

---

