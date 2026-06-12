---
title: "OpenVPN - connect but no internet"
date: 2013-04-06
forum: General Help
---

### Post by sdpagent on 2013-04-06
I managed to get openvpn to 'work' on my openvz VPS (I manage the host node too) but I lose connectivity to everything else (except the vps) when I do this. I'm have a gut feeling the packet forwarding is messed up, but I have checked all the sysctl files etc. My theory now is that my iptables is not actually taking effect on the vps. I tried using these rules:
> 
iptables -A INPUT -j LOG --log-prefix "INPUT Packet: "
iptables -A FORWARD -j LOG --log-prefix "FORWARD Packet: "
iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -s 10.8.0.0/24 -j ACCEPT
iptables -A FORWARD -j ACCEPT
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o venet0 -j SNAT --to 192.211.58.12



And notice that nothing is getting logged to /var/log/messages for packets. Perhaps my first two rules dont do what I think they do though. My askubuntu thread which has had no respondants, providing more detail is [here]("http://askubuntu.com/questions/278238/openvpn-on-ubuntu-openvz"). Perhaps there are more steps that I need to perform on the host node (centos5.8). Do I need to perform any packet mangling on that in iptables?

Any tips/advice is appreciated!

---

### Post by SeijiSensei on 2013-04-07
Are you trying to push all your traffic through the tunnel?  If so, you need to be careful how you set up routes.  This is entirely separate from iptables.

You need to have a route that points specifically to the IP address of your VPN remote that uses your computer's default gateway, then you need to replace the default route with one that points to the remote end of the tunnel.

If you run the command "route -n", you'll see the address of your default gateway listed alongside the 0.0.0.0 default route.  For illustration, let's suppose your router has address 192.168.1.1.  Now suppose you want to set up a tunnel to the server at 172.16.16.16, with the tunnel having the address 10.10.10.10 on your machine and 10.10.10.11 on the server.  Then you need to run some commands like these:
```

sudo ip route add 172.16.16.16 via 192.168.1.1
sudo ip route del default
sudo ip route add default via 10.10.10.11

```

The first tells your computer that it should send traffic intended for the remote server out through the normal default gateway 192.168.1.1.  The next two commands then deletes the default route through that server and replaces it with the remote end of the tunnel.  Now all traffic intended for the server will go out your router and over the Internet, while the rest of your traffic will go through the tunnel.

You can set up OpenVPN to run these commands when it starts using the "up" directive in openvpn.conf.

---

### Post by sdpagent on 2013-04-08
Thank you Mononoke for replying.

I am really sorry for wasting your time, but **your response did lead me to finding the solution**. Whilst creating a document of all the iproutes and ifconfigs for my reply to you, I discovered two tunnels on the 'non-working' openvpn server. Performing an openvpn restart showed me that it was restarting a client. I removed the client.conf file from /etc/openvz, restarted the openvz servcie and retried the connection and now I have internet.

Just for reference, I didn't need to perform any manual configuring of routes.

Thanks again for replying and your help.

---

### Post by atux on 2013-08-20
check if the file *etc/sysctl.conf*[FONT=sans-serif]  has [/FONT][COLOR=black]net.ipv4.ip_forward = 1
also try
[/COLOR]iptables -A FORWARD -i eth0 -o tun0 -m state --state ESTABLISHED,RELATED -j ACCEPT
[FONT=inherit][/FONT]iptables -A FORWARD -s 10.9.8.0/24 -o eth0 -j ACCEPT
[FONT=inherit][/FONT]iptables -t nat -A POSTROUTING -s 10.9.8.0/24 -o eth0 -j MASQUERADE


change the ip to yours.

---

