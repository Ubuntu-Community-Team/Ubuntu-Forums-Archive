---
title: "VPN Using ipsec-tools"
date: 2005-06-06
forum: General Help
---

### Post by outoforder2day on 2005-06-06
I'm trying to get a VPN up and running using the ipsec-tools in ubuntu.  NOTE: I installed the boxes with the server option, so there is no GUI available.

I have the following network
192.168.1.0/24 - local net (box1 is the gateway)
192.168.2.0/24 - remote net (box2 is the gateway)
LOCAL-IP - local external ip, box 1
REMOTE-IP - remote external ip, box 2

Both machines are running iptables and are acting as masq'd gateways for the hosts on the internal networks.

I got the configs from the linux vpn howto, and modified them for my environment

Local Config:
[INDENT]
## Flush the SAD and SPD
#
flush;
spdflush;

# ESP SAs doing encryption using 192 bit long keys (168 + 24 parity)
# and authentication using 128 bit long keys
add LOCAL-IP REMOTE-IP esp 0x201 -m tunnel
 -E 3des-cbc 0x7aeaca3f87d060a12f4a4487d5a5c3355920fae69a96c831
 -A hmac-md5 0xc0291ff014dccdd03874d9e8e4cdf3e6;

add REMOTE-IP LOCAL-IP esp 0x301 -m tunnel
 -E 3des-cbc 0xf6ddb555acfd9d77b03ea3843f2653255afe8eb5573965df
 -A hmac-md5 0x96358c90783bbfa3d7b196ceabe0536b;

# Security policies
spdadd 192.168.1.0/24 192.168.2.0/24 any -P out ipsec
           esp/tunnel/LOCAL-IP-REMOTE-IP/require;

spdadd 192.168.2.0/24 192.168.1.0/24 any -P in ipsec
           esp/tunnel/REMOTE-IP-LOCAL-IP/require;

#I've also tried adding this line in, to no avail
#spdadd 192.168.1.0/24 192.168.2.0/24 any -P fwd ipsec
#           esp/tunnel/LOCAL-IP-REMOTE-IP/require;
[/INDENT]
Remote Config:
[INDENT]
## Flush the SAD and SPD
#
flush;
spdflush;

#!/usr/sbin/setkey -f

# ESP SAs doing encryption using 192 bit long keys (168 + 24 parity)
# and authentication using 128 bit long keys
add LOCAL-IP REMOTE-IP esp 0x201 -m tunnel
 -E 3des-cbc 0x7aeaca3f87d060a12f4a4487d5a5c3355920fae69a96c831
 -A hmac-md5 0xc0291ff014dccdd03874d9e8e4cdf3e6;

add REMOTE-IP LOCAL-IP esp 0x301 -m tunnel
 -E 3des-cbc 0xf6ddb555acfd9d77b03ea3843f2653255afe8eb5573965df
 -A hmac-md5 0x96358c90783bbfa3d7b196ceabe0536b;

# Security policies
spdadd 192.168.1.0/24 192.168.2.0/24 any -P in ipsec
           esp/tunnel/LOCAL-IP-REMOTE-IP/unique;

spdadd 192.168.2.0/24 192.168.1.0/24 any -P out ipsec
           esp/tunnel/REMOTE-IP-LOCAL-IP/unique;

#Again, I also tried this
#spdadd 192.168.2.0/24 192.168.1.0/24 any -P fwd ipsec
#           esp/tunnel/REMOTE-IP-LOCAL-IP/require;
[/INDENT]

The configs seem to take, and the setkey -DP shows that the policies are up, but no traffic goes through the tunnel.  I've also tried using the IPSEC checklist, but it wasn't much help.  All traffic is allowed by default so firewalling shouldn't be an issue.  It seems that the traffic just isn't going through the tunnel, any idea how to route this kind of thing?  There's no phsycal interface like ipsec0 is there?
Any help would be greatly appreciated.

---

### Post by outoforder2day on 2005-06-06
Please disregard this and remember, the devil is in the details...  Check your default forward policies in iptables or else teh packets might just disappear...

---

