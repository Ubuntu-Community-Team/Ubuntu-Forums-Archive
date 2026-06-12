---
title: "Using DNS to rediredct a domain to a host"
date: 2013-12-23
forum: General Help
---

### Post by jafacakes2011 on 2013-12-23
Hello all, I am new to Ubuntu and these forums, so I am sorry if I have posted in the wrong area.

I am just wanting some general help using Bind, I am using Ubuntu Server 12.04, and I have installed bind.
I have followed numerous tutorials to try and understand how to do this but none have worked.

I am wanting to be able to use exampledomain.com to access a server running on an external IP. It would be impractical to just edit the host files as I am wanting to do this on many machines and possibly add more at a later date.

Here is what i have done so far...
named.conf.local:
```

include "/etcbind/zones.rfc1918";

zone "example.com"{
    type master;
    file "/etc/bind/zones/example.com.db"
};

```
named.conf.options:
```

options {
    directory "/var/cache/bind";
    forwarders {
        192.168.1.254; my router
    };
    dnssec-validation auto;
    auth-nxdomain no;
    listen-on-v6 { any };
};

```
zones/example/com.db:
```

$TTL    604800
@    IN    SOA    ns1.example.com. root.example.com. (
    2006020201;
    604800;
    86400;
    2419200;
    604800);
;
example.com.    IN    A    EXT.ERN.AL.IP

```

All help is greatly appreciated, I know that it is going to be something really stupid, but i'm not used to DNS yet.

---

