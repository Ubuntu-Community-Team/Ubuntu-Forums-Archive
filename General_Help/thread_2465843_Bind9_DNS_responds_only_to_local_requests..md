---
title: "Bind9 DNS responds only to local requests."
date: 2021-08-12
forum: General Help
---

### Post by Parrallax on 2021-08-12
Hi guys,

I am setting up an email server, nextcloud files server and DNS on a machine running Ubuntu 20.04. I've used iRedmail for email and it seems to be working. I need the DNS so that machines on the same network correctly access the server. I'm sorry I tried this on the networking forum but got zero views.

For the DNS I am using Bind9. Below is my named.conf.options
```
options {        directory "/var/cache/bind";
        listen-on-v6 { any; };
        version "not currently available";
        recursion yes;  
        querylog yes;
       max-cache-size 30%;


forwarders {
              8.8.8.8;
              8.8.4.4;
         };
        dnssec-validation no;
        auth-nxdomain no;    # conform to RFC1035
allow-recursion { any; };
allow-query { any; };
};

```

It works correctly when used on the local machine. But does not work when I try and access it from another machine on the network. I have tried disabling ufw so I don't think it's the firewall. Using ```
sudo tcpdump  -u port 53
``` I can see lots of DNS requests coming through including when I request them manually from another machine on the network.

My netstat:
```
muruadmin@mail:~$ sudo netstat -lnptu | grep namedtcp        0      0 192.168.1.5:53          0.0.0.0:*               LISTEN      63834/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      63834/named
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      63834/named
udp        0      0 192.168.1.5:53          0.0.0.0:*                           63834/named
udp        0      0 192.168.1.5:53          0.0.0.0:*                           63834/named
udp        0      0 192.168.1.5:53          0.0.0.0:*                           63834/named
udp        0      0 192.168.1.5:53          0.0.0.0:*                           63834/named
udp        0      0 192.168.1.5:53          0.0.0.0:*                           63834/named
udp        0      0 192.168.1.5:53          0.0.0.0:*                           63834/named
udp        0      0 192.168.1.5:53          0.0.0.0:*                           63834/named
udp        0      0 192.168.1.5:53          0.0.0.0:*                           63834/named
udp        0      0 192.168.1.5:53          0.0.0.0:*                           63834/named
udp        0      0 192.168.1.5:53          0.0.0.0:*                           63834/named
udp        0      0 192.168.1.5:53          0.0.0.0:*                           63834/named
udp        0      0 192.168.1.5:53          0.0.0.0:*                           63834/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           63834/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           63834/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           63834/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           63834/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           63834/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           63834/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           63834/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           63834/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           63834/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           63834/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           63834/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           63834/named



```

So it appears to be listening to port 53.

I've also tried PortQry and gotten this output:

```

portqry -n 192.168.1.5 -e 53 -p TCP


Querying target system called:


 192.168.1.5


Attempting to resolve IP address to a name...


Failed to resolve IP address to name


querying...


TCP port 53 (domain service): FILTERED

[CODE]

```

portqry -n 192.168.1.5 -e 53 -p UDP


Querying target system called:


 192.168.1.5


Attempting to resolve IP address to a name...


Failed to resolve IP address to name


querying...


UDP port 53 (domain service): LISTENING or FILTERED


Sending DNS query to UDP port 53...


DNS query timed out


[/CODE]

I just don't know anymore why it does not appear to be working. I'm sorry I've tried searching and seen this problem a lot but none of their solutions seem to work.

Thanks.

---

