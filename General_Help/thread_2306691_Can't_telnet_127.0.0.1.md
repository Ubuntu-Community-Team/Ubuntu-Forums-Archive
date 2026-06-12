---
title: "Can't telnet 127.0.0.1"
date: 2015-12-17
forum: General Help
---

### Post by avinashsharmapgma on 2015-12-17
HI 
I'm not able to telnet 127.0.0.1
[I]
root@ubuntuzabbix:~# ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.055 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.079 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.078 ms
^C
--- 127.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.055/0.070/0.079/0.014 ms
root@ubuntuzabbix:~# telnet 127.0.0.1
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
root@ubuntuzabbix:~# tcptraceroute 127.0.0.1
Selected device lo, address 127.0.0.1, port 52065 for outgoing packets,
Tracing the path to 127.0.0.1 on TCP port 80 (http), 30 hops max
 1  localhost (127.0.0.1) [open]  0.119 ms  0.066 ms  0.063 ms
root@ubuntuzabbix:~#

**But**

root@ubuntuzabbix:~# telnet ubuntutest2
Trying 10.198.2.123...
Connected to ubuntutest2.
Escape character is '^]'.
Ubuntu 14.04.3 LTS
Ubuntutest2 login:

ufw settings
root@ubuntuzabbix:~# ufw status
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
80                         ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere
10050/tcp                  ALLOW       Anywhere
10051/tcp                  ALLOW       Anywhere
10051/udp                  ALLOW       Anywhere
10050/udp                  ALLOW       Anywhere
22 (v6)                    ALLOW       Anywhere (v6)
80 (v6)                    ALLOW       Anywhere (v6)
80/tcp (v6)                ALLOW       Anywhere (v6)
10050/tcp (v6)             ALLOW       Anywhere (v6)
10051/tcp (v6)             ALLOW       Anywhere (v6)
10051/udp (v6)             ALLOW       Anywhere (v6)
10050/udp (v6)             ALLOW       Anywhere (v6)

[/I]This is a VM. 
Please help me out

---

### Post by deepakdeshp on 2015-12-17
*ping 127.0.0.1 **is pinging with no loss. I do not understand the question. Can you elaborate please?*

---

### Post by steeldriver on 2015-12-17
Do you actually have a telnet server running on *ubuntuzabbix?*

---

