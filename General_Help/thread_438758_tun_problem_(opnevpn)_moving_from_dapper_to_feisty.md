---
title: "tun problem (opnevpn) moving from dapper to feisty"
date: 2007-05-10
forum: General Help
---

### Post by jebe86 on 2007-05-10
Hi all, 

again some issues with update to 7.4 from 6.10.
I had an openvpn client working fine.
No changes made on the server, neither on my client config,
Alas, openvp does not work anymore.
Opnevpn.log says

Thu May 10 09:07:51 2007 us=571607 TLS Error: Unroutable control packet received from OPENVPN_SERVER:1194 (si=3 op=P_ACK_V1)

bu tI actualy believe it's a TUN issue.

#lsmod | grep tun
tun                    12032  0 

and 

# ls -la /dev/net/tun 
crw-rw---- 1 root root 10, 200 2007-05-03 14:50 /dev/net/tun


but it never gets started....

any clue ?

thank yuo all in advance .

---

