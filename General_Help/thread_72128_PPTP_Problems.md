---
title: "PPTP Problems"
date: 2005-10-05
forum: General Help
---

### Post by MGajh on 2005-10-05
Hi!

I'm a MS sys admin and need to setup my laptop to VPN (PPTP) to my servers and also then use the TS Client (RDP) to administer them.

As far as I can tell, I have a properly working pptpclient installation but find that when connected I can't ping the external address and obviously the TSClient. Below is the connection extract from the PPTP Config program:

> Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/2
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP
local  IP address 192.168.1.12
remote IP address 192.168.1.17
primary   DNS address 192.168.1.1
pptpconfig: pppd process exit status 0 (started)
ip route add xxx.xxx.xxx.xxx via 192.168.2.1 dev wlan0  src 192.168.2.9
pptpconfig: routes added to remote networks
pptpconfig: DNS changes made to /etc/resolv.conf
pptpconfig: connected
ping -c 5 192.168.1.17
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
PING 192.168.1.17 (192.168.1.17) 56(84) bytes of data.

--- 192.168.1.17 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4001ms

pptpconfig: command failed, exit code 1

Any help would be greatly appreciated!

---

