---
title: "Installed the update to Linux 5.15.0-121 and have some blocked ports"
date: 2024-09-13
forum: General Help
---

### Post by pook2022 on 2024-09-13
I just did the update to 5.15.0-121 and rebooted and now I have some weirdness.
I run a flask dev server on ports around 5000 and now I can't connect to that range externally.  
It doesn't seem to be a firewall issue, just no route to host on that port when I try and connect.

Anyone have any ideas?

iptables is fine
ufw not running
aa-status looks fine
netstat shows it's listening[INDENT]tcp        0      0 0.0.0.0:5003            0.0.0.0:*               LISTEN[/INDENT]

the interface looks fine
enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500[INDENT]inet 192.168.1.99  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::d65d:64ff:feee:8c29  prefixlen 64  scopeid 0x20<link>
        ether d4:5d:64:ee:8c:29  txqueuelen 1000  (Ethernet)
        RX packets 26302  bytes 4819204 (4.8 MB)
        RX errors 0  dropped 5  overruns 0  frame 0
        TX packets 15127  bytes 4039972 (4.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/INDENT]

From another host on my network I get
root@spoon:~# ping 192.168.1.99
[INDENT]PING 192.168.1.99 (192.168.1.99): 56 data bytes[/INDENT]
[INDENT]64 bytes from 192.168.1.99: icmp_seq=0 ttl=64 time=0.470 ms[/INDENT]
[INDENT]64 bytes from 192.168.1.99: icmp_seq=1 ttl=64 time=0.379 ms[/INDENT]
[INDENT]64 bytes from 192.168.1.99: icmp_seq=2 ttl=64 time=0.418 ms[/INDENT]
[INDENT]^C--- 192.168.1.99 ping statistics ---[/INDENT]
[INDENT]3 packets transmitted, 3 packets received, 0% packet loss[/INDENT]
[INDENT]round-trip min/avg/max/stddev = 0.379/0.422/0.470/0.037 ms[/INDENT]
root@spoon:~# telnet 192.168.1.99 5003
[INDENT]Trying 192.168.1.99...[/INDENT]
[INDENT]telnet: Unable to connect to remote host: No route to host[/INDENT]

---

### Post by pook2022 on 2024-09-13
AHAHHH!!!  firewalld!!!  man that took way too long to solve.

---

### Post by TheFu on 2024-09-13
> **pook2022 said:**
> AHAHHH!!!  firewalld!!!  man that took way too long to solve.

Firewalld?  Are you even running Ubuntu?

Anyway, please use the thread tools button and mark this thread as SOLVED to save time for other people.

---

### Post by coffeecat on 2024-09-15
Not a chat thread. Moved to General Help.

---

