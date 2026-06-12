---
title: "netstat - Established Connection"
date: 2014-03-19
forum: General Help
---

### Post by spec36 on 2014-03-19
I ran the following command:

```
netstat --ip -pan
```

these two listing stood out to me in that output. Looks like these 91... IPs are Canonical. Anyone know what these are? I don't like the fact that python has an established connection. Is this normal or not for Ubuntu?

```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0    106 192.168.1.111:42486     91.189.89.76:443        ESTABLISHED 3263/python     
tcp        1      0 192.168.1.111:42239     91.189.89.144:80        CLOSE_WAIT  3106/ubuntu-geoip-p

```

Any assistance would be greatly appreciated.

Thanks,

---

### Post by ian-weisser on 2014-03-19
Canonical servers provide LOTS of services to your system, including NTP, Geolocation, apt repositories, whoopsie/daisy error reporting, popularity contest, etc.

Looks normal to me. 
Insufficient data to determine the first service beyond the obvious fact that it's an encrypted http connection.
The second service is obviously [http://geoip.ubuntu.com](http://geoip.ubuntu.com) - some service you are using needs to know your approximate location. Insufficient data to determine the querant - you need to monitor dbus to determine that. IP location data is used for checking timezones, the weather applet, and other services.

None of those services are secret, and client source code is 100% available.
I have looked at a bunch of that source code over the past few years.
Disabling or redirecting those service clients to some other provider that you prefer is usually trivial.

---

### Post by efflandt on 2014-03-20
The whois command (like: **whois 91.189.89.76**) would show you that those IP addresses belong to in part:```
inetnum:        91.189.88.0 - 91.189.95.255
netname:        CANONICAL-CORE
descr:          Canonical Ltd
country:        GB
```which is related to Ubuntu. And as far as the port, **grep 443 /etc/services**```

https        443/tcp                # http protocol over TLS/SSL
https        443/udp
```encrypted web access

---

