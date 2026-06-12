---
title: "DNS BIND9 not working"
date: 2013-02-07
forum: General Help
---

### Post by ricstriker21 on 2013-02-07
[SIZE=3]Hi i've been searching a solution for a couple of days now with no success. I followed this tutorial [http://lani78.wordpress.com/2012/07/22/setting-up-a-dns-for-the-local-network-on-the-ubuntu-12-04-precise-pangolin-server/](http://lani78.wordpress.com/2012/07/22/setting-up-a-dns-for-the-local-network-on-the-ubuntu-12-04-precise-pangolin-server/) . B[SIZE=3]tw my OS is ubuntu 12.04. [/SIZE]Here's the error when i input the command _host [www.striker.com]("http://www.striker.com")_
```
 
Host www.st[SIZE=3]rike[/SIZE]r.com.striker.com not found:[SIZE=3] 2(SERVFAIL)
 [/SIZE]
```[B]
[SIZE=3]Con[SIZE=3]te[SIZE=3]nt of [SIZE=3]/etc/bind/named.conf.options
[/SIZE][/SIZE][/SIZE][/SIZE][/B][/SIZE]```

options {
           directory "/var/cache/bind";
           
           forwarders {
                        8.8.8.8;
                        8.8.4.4;
                        };

                      dnssec-validation auto;
                      auth-nxdomain no;  # conform to RFC1035
                      listen-on-v6 { any;};
};

```

[SIZE=3][B][SIZE=3]Content of [/SIZE][SIZE=3] /etc/network/interfaces[/SIZE]
[/B][/SIZE]
```

auto eth0 
iface eth0 inet static        
address 192.168.1.15         
netmask 255.255.255.0         
gateway 192.168.1.1         
network 192.168.1.0         
broadcast 192.168.1.255         
dns-nameservers 127.0.0.1         
dns-search striker.com         
dns-domain striker.com

```[SIZE=3][B]
[SIZE=3]Content of /etc/bind/named.conf.local[/SIZE][/B][/SIZE]

```

zone "striker.com" IN {
       type master;
       file "/etc/bind/zones/striker.com.db";
       };

zone "1.168.192.in-addr.arpa" {
       type master;
       file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
       };


```[B]
Content of /etc/bind/zones/striker.com.db[/B]

```

$ORIGIN .
$TTL 86400
striker.com. IN SOA ubuntu.striker.com. hostmaster.striker.com. (
          2013020702
          8H
          4H
          4W
          1D
)
striker.com. IN NS ubuntu.striker.com.
striker.com. IN MX 10 ubuntu.striker.com.

$ORIGIN striker.com.

localhost     IN      A      127.0.0.1
www           IN      A      192.168.1.13

```[B]

Content of [/B][B]/etc/bind/zones/rev.1.168.192.in-addr.arpa
[/B]
```

@ IN SOA ubuntu.striker.com. hostmaster.striker.com. (     
2013020701      
8H      
4H     
 4W      
1D  
)            
IN NS ubuntu.striker.com. 
 1         IN PTR www.striker.com.

```[B]

Pls help thanks
[/B]

---

### Post by Doug S on 2013-02-07
I suspect that for some reason the host program does not seem to realize that you have already given the full domain name rather than an abbreviation, so it appends the dns-search part again leading to the failed look up. What you want is results like this:```
doug@doug-64:~/config/dhcp$ host www.smythies.com
www.smythies.com has address 192.168.111.1
doug@doug-64:~/config/dhcp$ host www
www.smythies.com has address 192.168.111.1

```I don't know what is wrong with striker.com.db, but I have also never had success with $ directives, not that I have ever tried very hard. Myself, I would try these changes:
named.conf.local: change this:```
zone "striker.com" IN {
       type master;
       file "/etc/bind/zones/striker.com.db";
       };

```to this:```
zone "striker.com" {
       type master;
       file "/etc/bind/zones/striker.com.db";
       };

```striker.com.db: Replace with this:```
;
; BIND data file for striker.com
;
$TTL 86400
@       IN      SOA striker.com. hostmaster.striker.com. (
                2013020703      ; Serial
                8H              ; Refresh
                4H              ; Retry
                4W              ; Expire
                1D )            ; Negative Cache TTL
                IN      A       192.168.1.13
;
@               IN      NS      ubuntu.striker.com.
ubuntu          IN      A       192.168.1.13
www             IN      A       192.168.1.13
```I left out the MX record on purpose, for now, get this part working correctly first.
In your reverse file, change this line:```
 1         IN PTR www.striker.com.
```to this:```
 13         IN PTR www.striker.com.
```

---

